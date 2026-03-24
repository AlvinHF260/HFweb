HFweb 文档构建说明

项目使用 Sphinx 构建文档，文档源文件位于 docs/source，构建产物位于 docs/build/html。

一、环境准备

1. 安装 Python（建议 3.11+）。
2. 在项目根目录创建并激活虚拟环境（可选但推荐）。
3. 安装文档依赖。

Windows PowerShell 示例：

~~~powershell
cd d:\Users\asus\Desktop\temp\hf-web
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r docs\requirements.txt
~~~

二、本地编译

推荐命令（PowerShell，一条命令完成清理和构建）：

~~~powershell
cd d:\Users\asus\Desktop\temp\hf-web\docs; $env:SPHINXBUILD='d:/Users/asus/Desktop/temp/hf-web/.venv/Scripts/sphinx-build.exe'; .\make.bat clean; .\make.bat html
~~~

构建成功后可在以下位置查看页面：

- 首页：docs/build/html/index.html
- 目录：docs/build/html

三、Read the Docs

仓库已使用 .readthedocs.yaml 配置构建，关键点如下：

1. Sphinx 配置文件路径：docs/source/conf.py
2. 依赖安装文件：docs/requirements.txt
3. 线上域名：https://hfweb.readthedocs.io

四、常见问题

1. pip 命令找不到

使用 python -m pip 代替 pip，例如：

~~~powershell
python -m pip install -r docs\requirements.txt
~~~

2. make.bat 提示找不到 sphinx-build

请显式指定 SPHINXBUILD：

~~~powershell
$env:SPHINXBUILD='d:/Users/asus/Desktop/temp/hf-web/.venv/Scripts/sphinx-build.exe'
~~~

3. Read the Docs 报 Expected file not found: docs/conf.py

原因是配置路径错误。应使用 docs/source/conf.py。

五、内容编辑入口

1. 首页：docs/source/index.rst
2. 配置：docs/source/conf.py
3. 主体章节：docs/source 下各 rst 文件
4. 静态资源：docs/source/_static
