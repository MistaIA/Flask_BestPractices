# Flask_BestPractices

## <Flask 最佳实践>

##### 这是一个项目结构,可以直接使用并开始编写业务逻辑

##### 包含前后端分离/与不分离 jinja2 模版渲染

---------->>>>>>持续更新<<<<<<----------

后续会使用此结构加上 Vue 与 React 实现一套前后分离的博客前后台。

可能会再出 Tornado，Sanic 等最佳实践。

大佬们！下面简陋的文档凑合先看着,有空闲时间补上详细使用文档。

如有疑问 -> QQ or Wechat : 417993207 (使用遇到问题请马上联系我会及时为你解答)

点个 star 吧！(你的 star 是我跟新的动力哟)

Github 访问不流畅可以前往->码云 https://gitee.com/yangyuexiong/Flask_BestPractices

Flask 官方文档
https://flask.palletsprojects.com/

Flask 中文文档
https://dormousehole.readthedocs.io/en/latest/

```text
Flask_BestPractices
├── app(应用)
│   ├── __init__.py
│   ├── all_reference.py(通用统一导入)
│   ├── api
│   │   ├── __init__.py(注册url)
│   │   ├── method_view_demo(MethodView使用例子)
│   │   │   ├── __init__.py
│   │   │   └── method_view_demo.py
│   │   ├── restful_demo(flask_restful使用例子)
│   │   │   ├── __init__.py
│   │   │   └── restful_demo.py
│   │   └── route_demo(flask路由使用例子)
│   │       ├── __init__.py
│   │       └── route_demo.py
│   ├── controllers(其他业务)
│   │   ├── __init__.py
│   │   ├── other_module_01
│   │   │   ├── __init__.py
│   │   │   └── module_01.py
│   │   ├── other_module_02
│   │   │   ├── __init__.py
│   │   │   └── module_02.py
│   │   └── other_module_03
│   │       ├── __init__.py
│   │       └── module_03.py
│   ├── models(模型)
│   │   ├── __init__.py
│   │   └── admin
│   │       └── models.py
│   ├── static(静态文件(Js,Css,Img))
│   │   ├── flask.jpg
│   │   └── images
│   │       └── flask.jpg
│   └── templates(模版文件(HTML)用于模版渲染(前后分离不需要,这里只作为一个例子))
│       ├── index01.html
│       ├── index02.html
│       └── index03.html
├── common(公共文件分类)
│   ├── __init__.py
│   ├── interceptors(路由钩子)
│   │   ├── ApiHook.py(前台应用拦截处理器(即:访问api开头的url时做的逻辑处理))
│   │   ├── AppHook.py
│   │   ├── CmsHook.py(管理后台拦截处理器(即:访问cms开头的url时做的逻辑处理))
│   │   └── __init__.py
│   └── libs
│       ├── BaseModel.py(ORM基类)
│       ├── __init__.py
│       ├── api_result.py(统一返回json格式规范)
│       ├── customException.py(自定义异常)
│       └── tools.py(工具)
├── config(配置文件)
│   ├── __init__.py
│   ├── config.py
│   ├── dev.ini
│   └── pro.ini
├── ExtendRegister(扩展统一注册)
│   ├── __init__.py
│   ├── bp_register.py(蓝图)
│   ├── conf_register.py(配置文件)
│   ├── db_register.py(数据库)
│   ├── excep_register.py(异常处理)
│   └── hook_register.py(路由钩子拦截器)
├── logs
│   ├── __init__.py
│   └── tb.log
├── migrations(数据迁移文件(会在初始化迁移环境后生成))
├── tasks(定时任务/异步任务)
│   ├── APSchedulerTasks
│   │   └── clear_logs.py
│   ├── CeleryAsyncTasks
│   │   ├── __init__.py
│   │   ├── celeryconfig.py
│   │   └── main.py
│   └── __init__.py
├── test(测试)
│   ├── __init__.py
│   ├── excep_test.py
│   ├── req_test.py
│   ├── test_celery.py
│   ├── test_data.py
│   └── test_env.py
├── ApplicationExample.py(应用实例)
├── LICENSE
├── manage.py(脚本命令文件(初始化迁移环境,迁移数据库,映射数据库等一系列的操作))
├── Pipfile(环境依赖)
├── Pipfile.lock
├── README.md
├── run.py(启动文件)
└── test_run.py(调试启动文件(可以忽略或者删除))

```

## 安装

- Python3.7+
- pip3
- pipenv

  ```shell script
  pip3 install pipenv
  ```

## 配置虚拟环境

- 进入项目根目录

  ```shell script
  cd /Flask_BestPractices
  ```

- 修改 pipenv 的 pip 安装源(科学上网(翻墙)的同学可以忽略)

  ```
  Pipfile文件修改如下:

  # 国内pip安装源(不能翻墙的同学修改如下,在可以翻墙的情况下依旧国内pip源比较快)
  url = "https://mirrors.aliyun.com/pypi/simple"

  # 国外pip安装源(可以翻墙)
  url = "https://pypi.org/simple"
  ```

- 安装虚拟环境与依赖的包

  ```shell script
  pipenv install
  ```

- 进入虚拟环境

  ```shell script
  pipenv shell
  ```

- 查看虚拟环境路径

  ```shell script
  pipenv --venv
  ```

  ![image](images/f1.png)

- Pycharm 配置 pipenv 虚拟环境(不使用 Pycharm 的同学可以忽略)

  ![image](images/f2.png)
  ![image](images/f3.png)

- 配置 Pycharm 的 Flask 变量(因为 Pycharm 运行项目不会读取系统变量所以要配置在 Pycharm 中)

  ![image](images/f4.png)
  ![image](images/f5.png)

- 配置 Flask 系统变量(原本操作系统中并没有 FLASK_ENV 变量,所以 Flask 启动的时候默认为 production,为了区分开发/生产需要通过以下方式配置)(以下配置只能在终端启动项目生效在 Pycharm 不生效)

- Windows 系统(一般用于开发环境,所有配置为开发的变量:development)

  ![image](images/f6.png)

- MacOS 系统(同样也配置为开发环境,所有配置为开发的变量:development)

  ```shell script
  vim ~/.bash_profile
  ```

  ![image](images/f7.png)

  ```
  打开文件找到(如果没看到这个文件 按: shift按键+command按键+ . 按键。就会显示隐藏文件因为隐藏文件一般不显示/需要使其隐藏,再按一次 shift按键+command按键+ . 按键)
  ```

  ![image](images/f8.png)

  ```shell script
  生效配置文件
  source ~/.bash_profile
  ```

- Linux 系统(一般使用为生产环境,所有配置为生产的变量:production)
  ```shell script
  vim ~/.bashrc
  ```
  ![image](images/f9.png)
  ```shell script
  source ~/.bashrc
  ```

## 访问例子(注意在 url 末尾要加上'/'否则会出现 308 报错,或者在定义 url 时不在末尾加上'/')

- api:

  - http://0.0.0.0:9999/api

- cms:

  - http://0.0.0.0:9999/cms

- 其他业务模块:

  - http://0.0.0.0:9999/m1/
  - http://0.0.0.0:9999/m2/
  - http://0.0.0.0:9999/m3/

## 修改 config.py 文件

- 数据库部分(先创建好数据库)
- 其他配置根据需要修改/增加

## 创建表(这里我提供了一套简单的后台权限管理:model/admin,可以自己设计你自己的权限管理或者直接开始设计你的表 和 manage shell)

- manage.py 文件中已经定义好初始化数据,创建表等方法(根据需要自定义其他方法,详细例子:manage.py 文件)

  ```shell script
  pipenv run python3 manage.py
  ```

- 首次!首次!首次! 创建表时执行(注意需要在虚拟环境中执行:即 pipenv shell)

  ```shell script
  pipenv run python3 manage.py orm
  ```

- 每次！每次！每次！新增 model 表后在 manage.py 导入后执行(区别在于没有初始化:python3 manage.py db init)

  ```shell script
  pipenv run python3 manage.py table
  ```

## 业务实现

- 路由注册

  ```
  /Flask_BestPractices/app/api/__init__.py
  ```

- 其他注册

  ```
  /Flask_BestPractices/ExtendRegister/bp_register.py
  ```

## 钩子函数(拦截器)使用:

- 拿其中一个举例:业务逻辑根据自己需要编写

  ```
  /Flask_BestPractices/common/interceptors/ApiHook.py
  ```

## 自定义异常添加使用:

- 在<Flask_BestPractices/common/libs/customException.py>添加

  ```python

    # 在文件中添加元组变量 例如
    ServerError = (500, '服务器内部异常')

    # 在下方ab_code方法中的字典 C 中添加key:value 例如
    def ab_code(data):
        C = {
            400: Bad_Request,
            401: NOT_AUTHORIZED,
            403: FORBIDDEN,
            500: ServerError,
            666: not_token
        }
        code = C.get(data)[0]
        msg = C.get(data)[1]
        raise CustomException(code=code, msg=msg)

    # 使用
    # MethodView 使用 ab_code
    # flask_restful 使用 ab_code_2
    from common.libs.customException import ab_code,ab_code_2

    class FlaskRestfulCustomException(Resource):

        def get(self):
            ab_code_2(333)

    class MethodViewCustomException(MethodView):

        def get(self):
            ab_code(333)

  ```

## 任务

- 异步任务

  ```
  注意:配置好redis,如果使用MQ等其他需要对应修改配置后在启动
  启动celery例子(必须要在/CeleryAsyncTasks目录下启动以及配置好redis):
      /CeleryAsyncTasks/main.py里面含有启动/停止等命令例子,模拟邮件发送任务例子.

  调用任务例子:
      启动后调用任务例子:
      调用任务例子: /test/test_celery.py
  ```

- 定时任务
  ```
  使用例子:
      /tasks/APSchedulerTasks/clear_log.py文件中包含3钟常用方法,以清除日子为例子
  启动:
      /APSchedulerTasks目录下直接执行clear_log.py文件
  ```

## 部署(2019-06-18 更新):

- 我掘金的一篇文章

  - https://juejin.im/post/5d08574351882563f967d5b9

- 代码中可能存在大量打印调试代码语句(print('xxxx'))可以将其注释或者删除。

- 快试试快速实现你业务需求吧！！！嘻嘻！！！
