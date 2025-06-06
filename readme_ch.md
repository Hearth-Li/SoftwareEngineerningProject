# Collegra

[English Version](README.md)

**Collegra**（College + Agora）是一个轻量级的软件平台，集成了多种实用功能，旨在帮助大学生在学业、职业发展和日常生活中全面成长。

---

## 🚀 安装指南

1. 使用 conda 创建并激活虚拟环境：
```bash
conda create -n collegra python=3.9
conda activate collegra
```

2. 安装所需依赖：
```bash
pip install flask flask_sqlalchemy flask_babel requests
```

3. 进入项目目录并运行程序：
```bash
cd Collegra
python app.py
```

4. 在浏览器中访问：[http://127.0.0.1:8000/](http://127.0.0.1:8000/)

---

## 📁 项目结构

```bash
Collegra
    |-- app.py
    |-- README.md
    |-- readme_ch.md
    |-- text2cv.py
    |-- static
    |-- templates
        |-- CourseScheduler
        |-- PathRecommender
        |-- base.html
        |-- index.html
        |-- recommender.html
        |-- resume.html
        |-- course_scheduler.html
        |-- todo.html
        |-- chat.html
```

- **`app.py`**：Flask 应用的主文件，定义路由、初始化程序并启动服务器。
- **`base.html`**：定义顶栏（包括 logo、标语、语言切换和菜单）以及渐变背景的基础模板。
- **`index.html`**：Collegra 的主页。
- **`static/`**：包含静态资源，如 CSS、JavaScript 和图像等。
- **`text2cv.py`**：用于将文本生成简历的脚本（如需也可补充用途说明）。
- **`recommender.html`**: 路径推荐模块的主页, 它为用户推荐一些领域方向的学习路径。
- **`resume.html`**: 简历生成器的主页, 它根据用户输入生成简历。
- **`course_scheduler.html`**: 课程表管理主页。
- **`todo.html`**: 待办列表主页, 它可以设置不同的任务和优先程度等。
- **`chat.html`**: 大模型接口, 支持问答

---

## 🤝 贡献指南

如果你想贡献一个对大学生有帮助的新模块，请遵循以下步骤：

1. 将你的模块主页的 `HTML` 文件直接放入 `templates/` 文件夹中。
2. 如果你的模块包含多个页面，请在 `templates/` 下创建一个新文件夹，并将辅助页面放入其中。
3. 在 `app.py` 中注册模块路由，例如：
   ```python
   @app.route('/<your_module>')
   def your_module():
       return render_template('<your_main_html_path>')
   ```
   根据实现的复杂程度，你可能还需要添加更多的 Python 接口逻辑。

4. 更新 `base.html` 中的导航菜单，添加模块链接：
   ```html
   <a href="{{ url_for('your_module') }}">
       <span class="lang-en hidden">Your Module Name</span>
       <span class="lang-zh">你的模块名称</span>
   </a>
   ```
5. 将接口按钮加到主页面. 在`index.html`中, 仿照之前的模块加入:
    ```html
    <a href="{{ url_for('your_module') }}"
       class="mt-4 inline-block bg-blue-500 text-white py-2 px-4 rounded hover:bg-blue-700 lang-en hidden">
        Your Module Name
    </a>
    <a href="{{ url_for('your_module') }}"
       class="mt-4 inline-block bg-blue-500 text-white py-2 px-4 rounded hover:bg-blue-700 lang-zh">
        你的模块名称
    </a>
    ```
6. 所有的 `HTML` 页面应继承自 `base.html`，以保持一致的页面结构和样式。
7. 请确保你提议的模块与现有模块不相似或重复。

