### 基于Deerlet做了个人版本的在线简历模板PersonalResume

[DEMO | 在线预览](http://resume.dwzhao.com)

### 下载及部署

**Clone**:

    git clone https://github.com/DaweiZhao007/PersonResume.git && cd PersonResume/static && git clone https://github.com/pandao/editor.md.git

**安装第三方依赖包（最好使用virtualenv中）**：

    pip install -r requirements.txt

**安装 pdf 打印服务的依赖 `wkhtmltopdf`**.

按照wkhtmltopdf[官网](http://wkhtmltopdf.org/downloads.html)下载安装对应版本

```
Linux:
    cd mytmpfolder
    wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.4/wkhtmltox-0.12.4_linux-generic-amd64.tar.xz
    sudo tar xvf wkhtmltox-0.12.4_linux-generic-amd64.tar.xz
    sudo mv wkhtmltox/bin/wkhtmlto* /usr/bin/
    
    由于服务器中文字体不全的问题，请下载字体并更新缓存：
    sudo apt-get install fonts-wqy-microhei ttf-wqy-microhei fonts-wqy-zenhei ttf-wqy-zenhei
    fc-cache -f -v
```
**运行**：

    Python main.py
    open "http://127.0.0.1:5000" # 访问 http://127.0.0.1:5000

### 配置
    配置在项目根目录下的 config.py 中：
    TITLE = '马云的简历'  # 简历标题，例：马云的简历
    SUB_TITLE = '好的东西往往都是很难描述的'  # 简历子标题，一句话介绍自己，例：好的东西往往都是很难描述的。
    READ_PASSWORD = '12345'  # 简历浏览密码
    ADMIN_PASSWORD = 'abcd'  # 简历管理密码
    BASE_DIR = basedir
    UPLOAD_FOLDER = basedir

    PDF_OPTIONS = {
        'page-size': 'Letter',
        'margin-top': '0.75in',
        'margin-right': '0.75in',
        'margin-bottom': '0.75in',
        'margin-left': '0.75in',
        'encoding': "UTF-8",
        'no-outline': None
    }  # PDF 设置

在线编辑模式下，每 6 秒自动保存一次当前的文本（全文保存），如果你想修改这个数值，在 `admin.html` 的第 35 行进行修改：

    setInterval("saveToFile()", 6000);  // 修改自动保存的时间

一切简历数据（除了标题）保存在 `resume.md` 中，如果喜欢，你也可以离线编辑，并且 copy 到任何地方。


### 技术框架：
- 后端基于：[Flask](https://github.com/mitsuhiko/flask),   [Flask-Markdown](https://github.com/dcolish/flask-markdown)
- 前端基于：[yue.css](https://github.com/lepture/yue.css),   [editor.md](https://github.com/pandao/editor.md)
- pdf打印服务基于：[wkhtmltopdf](http://wkhtmltopdf.org/)

