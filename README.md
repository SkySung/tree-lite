# tree-lite
[繁體中文](https://github.com/SkySung/tree-lite/blob/main/README-zh-TW.md) | [English](https://github.com/SkySung/tree-lite/blob/main/README.md)

A lightweight directory structure generator.

An alternative to the Linux `tree` command, but in a shorter version. (200 lines)

Easily customizable with AI/LLM!

## Output Example

```bash
current_directory/
├── node_modules/
├── src/
│   ├── main.sh
│   └── utils.sh
├── README.md
└── LICENSE
```

## Quick start

```bash
curl -O https://raw.githubusercontent.com/SkySung/tree-lite/main/tree.sh

chmod +x tree.sh

./tree.sh
```
tree.sh will automatically generate a tree.txt file containing the directory structure.

## Features
+ Easily Using LLM to customize. Need some personal config? `tree.sh` with 200 only lines, easily fit within any LLM context size. Ask AI to make your cutomization.
+ Handles Large Directories: Automatically identifies large directories to avoid full traversal (eg. node_modules/, media/ tmp/).
+ Multiple Depth Specification Methods: Set directory recursion depth using positional arguments (e.g., ./tree.sh 3) or option parameters (e.g., ./tree.sh -L 3).
+ Customizable Ignore List: Easily specify files or directories to exclude from the tree.

## Notice
Don't forget to add tree.sh/tree.txt in your .gitignore file, or it will be upload to your remote repo.

## Installation
1. Download tree.sh to the Current Directory:

```bash
curl -O https://raw.githubusercontent.com/SkySung/tree-lite/main/tree.sh
```
2. Grant Execute Permissions:

```bash
chmod +x tree.sh
```
3. Run the Script to Generate the Directory Structure:
```bash
./tree.sh
```

## Usage
```bash
./tree.sh [options] [depth]

Options:
  -L [depth]   Set the maximum display depth of the directory tree.
  -h, --help   Display this help message.

Arguments:
  [depth]      Optional. The number of levels to recurse into. Can be prefixed with a '-' (e.g., -3). Default is 3 if not provided.
               Valid inputs: `./tree.sh 4`, `./tree.sh -4`, or `./tree.sh -L 4` for 4 levels of recursion.

Examples:
  # Specify depth using positional argument
  ./tree.sh 3

  # Specify depth using a negative positional argument (same effect as above)
  ./tree.sh -3

  # Specify depth using the -L option
  ./tree.sh -L 3

  # Display help information
  ./tree.sh -h
  ./tree.sh --help
```
## Customization

You can customize the tree.sh script according to your needs by modifying the following variables:

Output File Name:
Change the output_file variable in the script to alter the name of the generated directory structure file.
```bash
output_file="custom_tree.txt"
```

Ignore Files or Directories:
Update the ignore_list array to specify files or directories to exclude.
```bash
ignore_list=("$script_name" "$output_file" ".git" ".gitignore" "node_modules")
```

Large Directories:
Adjust the large_dirs array to control which directories should not be fully traversed.
```bash
large_dirs=("node_modules" "vendor" "build" "dist" "logs" "tmp" "cache" "__pycache__" "media" "uploads" "data" "datasets")
```

## Contributing
Contributions are welcome! Please submit issues or pull requests to improve this project. Follow the guidelines below:

Fork the Repository.
Create a New Branch (git checkout -b feature/YourFeature).
Commit Your Changes (git commit -m 'Add some feature').
Push to the Branch (git push origin feature/YourFeature).
Create a Pull Request.
