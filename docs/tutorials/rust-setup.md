# Setting up a dev container for Rust

* Primary author: [Tracy Dang](https://github.com/tmndang)
* Reviewer: [Kibby Pangilinan](https://github.com/hyacinp)

# Objective
This tutorial will guide you through setting up a development container for Rust, initializing a project, and writing a simple "Hello COMP423" program.

# Prerequisites
Make sure you have the following completed:
1. Docker installed on your system and running
2. Visual Studio Code installed
3. Git installed
4. The Dev Containers extension installed in VS Code
5. A GitHub account

# Step 1: Git Repository
1. Open your terminal. Create a new directory for your project and initialize a Git repository:
```bash
    mkdir rust-dev-container
    cd rust-dev-container
    git init
```

2. Create a README file:
```bash
    echo "# Rust Dev Container Project" > README.md
    git add README.md
    git commit -m "Initial commit with README"
```

3. Navigate to GitHub and create a new repository page. Name is rust-dev-container, set to public visibility, and do not initialize any files. Then push to a remote repository:
```bash
    git remote add origin https://github.com/<your-username>/rust-dev-container.git
    git branch -M main
    git push -u origin main
```

# Step 2: Dev Container Configuration
1. Install the Dev Containers extension for VS Code. Create a `.devcontainer` directory at the root.
```bash
    mkdir .devcontainer
```

2. Add the `devcontainer.json` file:
```json
    {
      "name": "Rust Dev Environment",
      "image": "mcr.microsoft.com/devcontainers/rust:latest",
      "customizations": {
        "vscode": {
          "extensions": ["rust-lang.rust-analyzer"]
        }
      },
      "postCreateCommand": "cargo install cargo-edit"
}
```

3. Reopen the project in the dev container:
a) Press `Ctrl+Shift+P` or `Cmd+Shift+P` on Mac in VS Code
b) Select **Dev Containers: Reopen in Container**

4. Verify the Rust version:
```bash
    rustc --version
```
This command checkes that you are using the most recent version of Rust

# Step 3: Rust Project
1. Inside the dev container, create a new Rust project:
```bash
    cargo new hello-comp423 --vcs none
    cd hello-comp423
```
The `--vcs none` flag makes sure no new Git repository is created.

2. Open and update the main.rs file to print "Hello COMP 423":
```bash
    fn main(){
    println!("Hello COMP423!");
    }
```

# Step 4: Build and Run the Program:
1. Build the program:
```bash
    cargo build
```
The `cargo` handles dependency magagement and builds the entire project, while `gcc` compilies individual source files.

2. Run the program:
```bash
    cargo run
```
The `cargo run` command combines building and executing the program, while `cargo build ` only compiles without running.

# Step 5: Git Changes
1. Add your changes:
```bash
    git add .
```

2. Commit your changes:
```bash
    git commit -m "<meaningful message here>"
```

3. Push to remote repository:
```bash
    git push origin main
```

# Done
You have successfully set up local and remote repositories, set up your Rust Dev Container, and ran a basic program!