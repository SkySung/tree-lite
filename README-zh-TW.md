# tree-lite

一款輕量級的目錄結構生成器。

是 Linux `tree` 命令的替代品，但更精簡（僅200行）。

輕鬆使用 AI/LLM 進行自定義！

## 輸出範例

```bash
current_directory/
├── node_modules/
├── src/
│   ├── main.sh
│   └── utils.sh
├── README.md
└── LICENSE
```

## Quick Start
```bash
curl -O https://raw.githubusercontent.com/SkySung/tree-lite/main/tree.sh

chmod +x tree.sh

./tree.sh
```

tree.sh 會自動生成一個包含目錄結構的 tree.txt 文件。

## Feature
+ 使用 LLM 進行自定義：有個人需求嗎？tree.sh 只有200行，輕鬆適配任何 LLM 的上下文大小。只需複製貼上，輕鬆打造屬於自己的版本。
+ 處理大型目錄：避免完全遍歷大型目錄，（例如 node_modules/、media/、tmp/）。
+ 多種深度指定方式：可以使用位置參數（例如 ./tree.sh 3）或選項參數（例如 ./tree.sh -L 3）來設定目錄遞迴深度。
+ 可自定義忽略列表：輕鬆指定要從樹狀圖中排除的檔案或目錄。

## 注意事項
別忘了將 tree.sh 和 tree.txt 加入你的 .gitignore 文件，否則它們會被上傳到遠端倉庫。

## 安裝

1. 下載 tree.sh 到當前目錄：
```bash
curl -O https://raw.githubusercontent.com/SkySung/tree-lite/main/tree.sh
```
2. 賦予執行權限：
```bash
chmod +x tree.sh
```
3. 運行腳本以生成目錄結構：
```bash
./tree.sh
```

## 使用方法
```bash
./tree.sh [選項] [深度]

選項:
  -L [深度]    設定目錄樹的最大顯示深度。
  -h, --help   顯示這個幫助訊息。

參數:
  [深度]       可選。要遞迴的層數。可以以 '-' 為前綴（例如 `-3`）。如果未提供，預設為 3。
               有效輸入：`./tree.sh 4`、`./tree.sh -4` 或 `./tree.sh -L 4` 代表遞迴4層。

範例:
  # 使用位置參數指定深度
  ./tree.sh 3

  # 使用負數位置參數指定深度（效果同上）
  ./tree.sh -3

  # 使用 -L 選項指定深度
  ./tree.sh -L 3

  # 顯示幫助訊息
  ./tree.sh -h
  ./tree.sh --help
```

## 自定義
你可以通過修改以下變數來根據需求自定義 tree.sh 腳本：

+ 輸出文件名稱：
  修改腳本中的 output_file 變數來改變生成的目錄結構文件名稱。
```bash
output_file="custom_tree.txt"
```
+ 忽略的檔案或目錄：
  更新 ignore_list 陣列來指定要排除的檔案或目錄。
```bash
ignore_list=("$script_name" "$output_file" ".git" ".gitignore" "node_modules")
```
+ 大型目錄：
  調整 large_dirs 陣列來控制哪些目錄不應完全遍歷。(你不會想要列出 node_modules 裡的東西對吧？)
```bash
large_dirs=("node_modules" "vendor" "build" "dist" "logs" "tmp" "cache" "__pycache__" "media" "uploads" "data" "datasets")
```
## 貢獻
歡迎貢獻！請提交問題（issues）或拉取請求（pull requests）來改進這個專案。請遵循以下指南：

1. Fork 此倉庫。
2. 建立新分支 (git checkout -b feature/YourFeature)。
3. 提交更改 (git commit -m 'Add some feature')。
4. 推送到分支 (git push origin feature/YourFeature)。
5. 創建 Pull Request。