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
4. Select `FolderZipperExample.xpz` and Click **Import** 
5. Follow Step 2 to copy the DLL and JAR file to the necessary environment directory.


---

### 🔹 Step 2: Copy Dependencies

#### **For .NET Generator**
1. Copy `FolderZipperLibrary.dll` to:
   ```
   Target Environment Directory: web\bin
   ```
2. Build All.

#### **For Java Generator**
1. Copy `FolderZipper.jar` to:
   ```
   Target Environment Directory: web\drivers
   ```
2. Build All.

---

### 🔹 Step 3: Use in GeneXus Code

Example usage:
```genexus
&IsSuccess = FolderZipper.zipFolder(&SourceFolder, &DestinationZip)

If &IsSuccess
	Filedownloader.Call(&ZipFileName, &DestinationZip, &ContentType)
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
✅ Ensure the **JAR** is placed in the Tomcat project directory **WEB-INF\lib**.
✅ Buil All after copying dependencies. 

---

## 📜 License
This project is licensed under the **MIT License** – you can use, modify, and distribute it freely.

---

## Support & Contact
For issues and support, contact **Hussain Behestee**  
📧 Email: behestee@innovative-solutions.co.jp   
