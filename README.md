# GitHub Actions Demo with React

This repository demonstrates how to use GitHub Actions with a React application.

## Project Structure

- `.github/workflows/egg.yaml`: Contains the GitHub Actions workflow configuration
- `react-app/`: Contains the React application code

## Local Development

To run the application locally:

1. Navigate to the react-app directory:
   ```bash
   cd react-app
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm start
   ```

4. Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

## GitHub Actions Workflow

The workflow will:
1. Check out the code
2. Set up Node.js
3. Install dependencies
4. Build the application
5. Run tests

The workflow is triggered on every push to the repository.


## egg.yaml
Github Actions workflow structure
```
name: CI Workflow

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '14'

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test
```
* name: 工作流的名称，可以自定义
* on: 定义触发工作流的事件，例如 push、pull_request 等。可以指定特定的分支或标签
* jobs: 定义多个作业（jobs），每个作业可以在不同的环境中运行
* job_name: 每个作业的名称，如 build
* runs-on: 指定作业运行的环境，如 ubuntu-latest、windows-latest 等
* steps: 作业中的具体步骤，按顺序执行
* name: 每个步骤的名称，便于识别
* uses: 使用现成的 GitHub Action，例如 actions/checkout、actions/setup-node 等
* run: 直接运行 shell 命令，适合自定义步骤

### 其他常见配置
* env: 定义环境变量，可以在作业或步骤中使用。
* with: 提供额外参数给特定的 Action。
* needs: 指定作业之间的依赖关系，确保按顺序执行。
* timeout-minutes: 定义作业的超时时间。

### 实例
```
name: CI Workflow

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: '3.8'

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: Run lint
        run: flake8 .

      - name: Run tests
        run: pytest
```