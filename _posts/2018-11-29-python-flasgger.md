---
published: true
title: (Python-學習-09) --- 使用 Flassger 自動產生 API 文件
layout: post
author: Allen
category: Python
type: Blog
image: /images/blog/20181129/20181129-000.png
tags: 
  - Python
comments: true
---

![book](/images/blog/20181129/20181129-000.png)

# 為何需要自動產生 API 文件 ?
這是源自於工程師的天性，懶得寫文件，我們常常一接到專案，就開始埋頭寫 code，修 bug ，偶爾會先寫 Design Document 但是常常到後來 Document 與實際程式碼，相差甚遠。
造成後續維護與交接時，還需要再重寫文件。
經過多次專案的經驗，發現工程師比較願意再寫 code 時順便改一下註解，所以如果能夠透過註解內容產生文件，這樣文件可以與 code 的版本趨於一致。
傳統使用 C++ 開發 Windows 應用程式時，我都會使用 [Doxygen](http://www.doxygen.nl/) 但是開發 RESTful APIs 就發現 [Flasgger](https://github.com/rochacbruno/flasgger)  這個好用的工具。


# Swagger 簡介
Swagger 是一個大型的 API 開發者的工具框架，該框架提出了一個編寫OpenAPI的規範（命名為OAS），並且 Swagger 可以跨整個API生命週期進行開發，從設計和文檔到測試和部署。
透過 OpenAPI 規範， Swagger 能夠自動產生 Web 版的 API 文件，並且可提供網頁 UI 進行 API 測試

# Flask 簡介
Flask 是一個使用 Python 撰寫的輕量級 Web 應用程式框架，由於其輕量特性，也稱為 micro-framework（微框架）。
Flask 核心十分簡單，主要是由 Werkzeug WSGI 工具箱和 Jinja2 模板引擎所組成，Flask 和 Django 不同的地方在於 Flask 給予開發者非常大的彈性（當然你也可以說是需要思考更多事情），可以選用不同的用的 extension 來增加其功能。

# Flasgger 出現
在 Flask 框架中使用的 Swagger 即為 Flasgger， Flasgger 是 Flask 支持的 Swagger UI，
方便讓我們基於 Flask API 基礎上自動產生 Swagger Style 的 API 文件。
可以參考作者這篇 [Blog](http://brunorocha.org/python/flask/flasgger-api-playground-with-flask-and-swagger-ui.html)

# 安裝 Flasgger
安裝方式非常簡單，首先透過 pip 進行安裝

```
pip install flasgger
```

# 在 Flask Web API 上設定 Flasgger

```python
from flasgger import Swagger
app = Flask(__name__)
app.config['SWAGGER'] = {
    "title": "My API",
    "description": "My API",
    "version": "1.0.2",
    "termsOfService": "",
    "hide_top_bar": True
}
CORS(app)
Swagger(app)
```

# 在 API 上加上 API 說明

```python
@app.route('/v1/node', methods=['GET'])
def node_topo():
  """
    Get All Node List 
    Retrieve node list 
    ---
    tags:
      - Node APIs
    produces: application/json,
    parameters:
    - name: name
      in: path
      type: string
      required: true
    - name: node_id
      in: path
      type: string
      required: true
    responses:
      401:
        description: Unauthorized error
      200:
        description: Retrieve node list
        examples:
          node-list: [{"id":26},{"id":44}]
  """
  ret = jsonify(ret_list)
  return ret
```

# 啟動 Flasgger
使用 Flasgger 最大的好處驅動自動文件產生不需要特別指令，只需要重新執行 Flask Web API 即可

```
sudo python api.py
```

這時候 Flasgger 就會自動在 Web API 上面建立 **/apidocs/** 目錄夾

畫面如下
![book](/images/blog/20181129/20181129-001.png)

![book](/images/blog/20181129/20181129-002.png)