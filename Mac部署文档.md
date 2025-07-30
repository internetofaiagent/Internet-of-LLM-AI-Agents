# PolyAgent-Web3-AI-Agent-Interoperability-Protocol Mac 部署文档

## 系统要求

在开始部署之前，请确保您的Mac系统已安装以下依赖：

- **Python**: 3.8+ & <3.12
- **Node.js**: 16.0+
- **npm**: 8.0+
- **Git**: 最新版本

### 依赖安装检查

可以通过以下命令检查当前版本：

```bash
python3 --version
node --version
npm --version
git --version
```

如果缺少任何依赖，请先安装：

- **Python**: 通过 [Python官网](https://www.python.org/) 或 Homebrew 安装: `brew install python`
- **Node.js**: 通过 [Node.js官网](https://nodejs.org/) 或 Homebrew 安装: `brew install node`
- **Git**: 通过 Xcode Command Line Tools 或 Homebrew 安装: `brew install git`

## 部署步骤

### 后端部署

#### 第一步：设置Python虚拟环境

1. 打开终端 (Terminal)
2. 导航到项目根目录：
   ```bash
   cd /path/to/PolyAgent-Web3-AI-Agent-Interoperability-Protocol
   ```

3. 创建Python虚拟环境：
   ```bash
   python3 -m venv venv
   ```

4. 激活虚拟环境：
   ```bash
   source venv/bin/activate
   ```
   
   激活成功后，终端提示符前会显示 `(venv)`

5. 安装Python依赖：
   ```bash
   pip install -r requirements.txt
   ```

#### 第二步：启动后端服务

在同一个终端窗口中（确保虚拟环境已激活），输入：

```bash
python app.py
```

如果启动成功，终端会显示类似以下的提示信息：
```
🧠 正在初始化AI模型...
✅ ModelScope Qwen 模型初始化成功。
🤖 正在加载AI Agents...
✅ AI Agents 已加载。
 * Running on http://127.0.0.1:5000
```

**注意**: warning 警告可以忽略，如果出现 error 错误说明有问题需要解决。

### 前端部署

#### 第一步：进入前端目录

后端成功启动后，打开新的终端窗口并进入前端目录：

```bash
cd /path/to/PolyAgent-Web3-AI-Agent-Interoperability-Protocol/frontEnd
```

#### 第二步：安装前端依赖

1. 如果您还没有安装 pnpm，请先全局安装：
   ```bash
   npm install -g pnpm
   ```

2. 如果已经安装过 pnpm，在 frontEnd 目录下安装项目依赖：
   ```bash
   pnpm install
   ```

#### 第三步：启动前端开发服务器

在 frontEnd 目录下运行：

```bash
pnpm run dev
```

如果启动成功，终端会显示类似以下信息：
```
  VITE v6.3.5  ready in 1234 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  press h + enter to show help
```

然后您可以：
- 按 `o + Enter` 自动在浏览器中打开应用
- 或手动访问显示的本地地址（通常是 http://localhost:5173/）

## 常见问题

### 1. Python虚拟环境激活问题

如果 `source venv/bin/activate` 命令失败，请确保：
- 使用的是正确的Shell（bash/zsh）
- 虚拟环境目录创建成功
- 您在项目根目录下运行命令

### 2. 权限问题

如果遇到权限问题，可能需要使用 `sudo`，但建议首先尝试：
```bash
# 对于npm全局安装
npm config set prefix ~/.npm-global
export PATH=~/.npm-global/bin:$PATH
```

### 3. 端口冲突

- 后端默认使用端口 5000
- 前端默认使用端口 5173

如果端口被占用，您可以：
- 关闭占用端口的其他程序
- 或在启动时指定其他端口

### 4. 依赖安装失败

如果Python依赖安装失败，尝试：
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

如果前端依赖安装失败，尝试：
```bash
pnpm cache clean
pnpm install
```

## 停止服务

- **停止后端**: 在后端终端中按 `Ctrl + C`
- **停止前端**: 在前端终端中按 `Ctrl + C`
- **退出虚拟环境**: 在终端中输入 `deactivate`

## 下次启动

下次启动项目时：

1. 激活虚拟环境：
   ```bash
   cd /path/to/PolyAgent-Web3-AI-Agent-Interoperability-Protocol
   source venv/bin/activate
   ```

2. 启动后端：
   ```bash
   python app.py
   ```

3. 启动前端（新终端）：
   ```bash
   cd frontEnd
   pnpm run dev
   ```

---

**注意**: 请确保在开发过程中保持两个终端窗口打开，一个运行后端服务，一个运行前端服务。 