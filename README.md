# FolderZipper External Object for GeneXus

**Version:** 1.0  
**Supported Generators:** `.NET (C#)`, `Java`  
**Author:** Hussain Behestee  
**License:** MIT  

---

## 📝 Description
FolderZipper is a **GeneXus External Object** that enables **folder compression (ZIP)** using native `.NET` and `Java` implementations. This allows **GeneXus applications** to create ZIP files programmatically.

###  Features
✅ Compress a folder into a ZIP file  
✅ Works with `.NET` and `Java` generators  
✅ Easy integration into GeneXus applications  
✅ Supports GeneXus **17+**  

---

## 📁 Installation Guide

### 🔹 Step 1: Import the External Object
1. Open **GeneXus**.
2. Navigate to **Knowledge manager → Import**.
4. Select `FolderZipperEO.xpz` and Click **Import** 
5. Follow Step 2 to copy the DLL and JAR file to the necessary environment directory.


---

### 🔹 Step 2: Copy Dependencies

#### **For .NET Generator**
1. If already not copied please copy `FolderZipperLibrary.dll` to:
   ```
   Target Environment Directory: web\bin
   ```
2. Build All.

#### **For Java Generator**
1. If already not copied please copy `FolderZipper.jar` to:
   ```
   Target Environment Directory: web\drivers
   ```
2. Build All.

---

### 🔹 Step 3: Use in GeneXus Code

Example usage:
```genexus
&BaseFolder = format(!'%1/Download/', Directory.TemporaryFilesPath)
&SourceFolder = format(!'%1Files/', &BaseFolder)
&DestinationZip = format(!'%1/Download/files.zip', Directory.TemporaryFilesPath)
&ZipFileName = !'files.zip'

// Clear existing temporary files & folder if you prepare files in the folder here,
// Ohterwise you do not need to clear the files from here.
&Directory.Source = &BaseFolder
If &Directory.Exists()
	&Directory.Delete()
Endif

// Add the files folder temporarily
&Directory.Source = &SourceFolder
If NOT &Directory.Exists()
	&Directory.Create()
Endif

// Put here your logic to collect the files if already the files are not there
For each 
	Where FileServerId > 0
	&LocalFile.Source = FileServerFile
	&LocalFile.Copy(&SourceFolder + &LocalFile.GetName())
	
Endfor

// Set the response hear with appropriate content type
&ContentType = !"application/x-zip-compressed"

// Initiate compressing. if fails it will return false. true on success
&IsSuccess = FolderZipper.zipFolder(&SourceFolder, &DestinationZip)

If &IsSuccess
	// On success send the zipped file to download.
	Filedownloader.Call(&ZipFileName, &DestinationZip, &ContentType)
else
	// Show message if compression faild!
	msg("Folder compression failed!")
Endif
```
- `&SourceFolder` → Path of the folder to zip.  
- `&DestinationZip` → Path to save the ZIP file. 
- `&ZipFileName` → Name of the ZIP file to show in the download dialog. 
- `&ContentType` → Response Header content type. i.e. `application/x-zip-compressed` or `application/octet-stream`
---


## 📁 Full Example

### 🔹 Step 1: Import the External Object
1. Open **GeneXus**.
2. Create a New Project
3. Navigate to **Knowledge manager → Import**.
4. Select `FolderZipperExample.xpz` and Click **Import** 
5. Copy the DLL and JAR file to the necessary environment directory.
6. Build All

---


## 🔧 Troubleshooting

### **Error: "Unable to load assembly"**
✅ Ensure the **DLL** is placed in the correct directory **web\bin**  
✅ Buil All after copying dependencies.  

### **Error: "Method not found"**
✅ Ensure the **JAR** is placed in the Tomcat project directory **.\WEB-INF\lib**.
✅ Build All after copying dependencies. 

---

## 📜 License
This project is licensed under the **MIT License** – you can use, modify, and distribute it freely.

---

## Support & Contact
For issues and support, contact **Hussain Behestee**  
📧 Email: behestee@innovative-solutions.co.jp   
