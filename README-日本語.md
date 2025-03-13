# GeneXus の FolderZipper 外部オブジェクト

**バージョン:** 1.0
**サポートされているジェネレーター:** `.NET (C#)`、`Java`
**作成者:** Hussain Behestee
**ライセンス:** MIT

---

## 📝 説明
FolderZipper は、ネイティブの `.NET` および `Java` 実装を使用して **フォルダー圧縮 (ZIP)** を可能にする **GeneXus 外部オブジェクト** です。これにより、**GeneXus アプリケーション** はプログラムで ZIP ファイルを作成できます。

### 機能
✅ フォルダーを ZIP ファイルに圧縮
✅ `.NET` および `Java` ジェネレーターで動作
✅ GeneXus アプリケーションへの簡単な統合
✅ GeneXus **17+** をサポート

---

## 📁 インストール ガイド

### 🔹 ステップ 1: 外部オブジェクトのインポート
1. **GeneXus** を開きます。
2. **ナレッジ マネージャー → インポート** に移動します。
4. `FolderZipperExample.xpz` を選択し、**インポート** をクリックします。
5. ステップ 2 に従って、DLL および JAR ファイルを必要な環境ディレクトリにコピーします。

---

### 🔹 ステップ 2: 依存関係をコピー

#### **.NET ジェネレーターの場合**
1. `FolderZipperLibrary.dll` を次の場所にコピーします:
```
ターゲット環境ディレクトリ: web\bin
```
2. すべてをビルドします。

#### **Java ジェネレーターの場合**
1. `FolderZipper.jar` を次の場所にコピーします:
```
ターゲット環境ディレクトリ: web\drivers
```
2. すべてをビルドします。

---

### 🔹 ステップ 3: GeneXus コードでの使用

使用例:
```genexus
&IsSuccess = FolderZipper.zipFolder(&SourceFolder, &DestinationZip)

If &IsSuccess
Filedownloader.Call(&ZipFileName, &DestinationZip, &ContentType)
Endif
```
- `&SourceFolder` → 圧縮するフォルダーのパス。
- `&DestinationZip` → ZIP ファイルを保存するパス。
- `&ZipFileName` → ダウンロード ダイアログに表示される ZIP ファイルの名前。
- `&ContentType` → レスポンス ヘッダーのコンテンツ タイプ。つまり、`application/x-zip-compressed` または `application/octet-stream`
---

## 📁 完全な例

### 🔹 ステップ 1: 外部オブジェクトのインポート
1. **GeneXus** を開きます。
2. 新しいプロジェクトを作成します
3. **ナレッジ マネージャー → インポート** に移動します。
4. `FolderZipperExample.xpz` を選択し、**インポート** をクリックします
5. DLL および JAR ファイルを必要な環境ディレクトリにコピーします。
6. すべてをビルドします

---

## 🔧 トラブルシューティング

### **エラー: "アセンブリをロードできません"**
✅ **DLL** が正しいディレクトリ **web\bin** に配置されていることを確認します
✅ 依存関係をコピーした後、すべてをビルドします。

### **エラー: 「メソッドが見つかりません」**
✅ **JAR** が Tomcat プロジェクト ディレクトリ **WEB-INF\lib** に配置されていることを確認します。
✅ 依存関係をコピーした後、すべてをビルドします。

---

## 📜 ライセンス
このプロジェクトは **MIT ライセンス** に基づいてライセンスされています。自由に使用、変更、配布できます。

---

## サポートと連絡先
問題やサポートについては、**Hussain Behestee** にお問い合わせください。
📧 メール: behestee@innovative-solutions.co.jp