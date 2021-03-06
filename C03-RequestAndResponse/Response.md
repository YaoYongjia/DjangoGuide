# 响应

视图在接收请求并处理后，必须返回HttpResponse对象或子对象。HttpRequest对象由Django创建，HttpResponse对象由开发人员创建。

## 1 HttpResponse

可以使用**django.http.HttpResponse**来构造响应对象。

```python
HttpResponse(content=响应体, content_type=响应体数据类型, status=状态码)
```

也可通过HttpResponse对象属性来设置响应体、状态码：

- content：表示返回的内容。
- status_code：返回的HTTP响应状态码。

响应头可以直接将HttpResponse对象当做字典进行响应头键值对的设置：

```python
response = HttpResponse()
response['Itcast'] = 'Python'  # 自定义响应头Itcast, 值为Python
```

示例：

```python
from django.http import HttpResponse

def demo_view(request):
    return HttpResponse('itcast python', status=400)
    或者
    response = HttpResponse('itcast python')
    response.status_code = 400
    response['Itcast'] = 'Python'
    return response
```

## 2 HttpResponse子类

Django提供了一系列HttpResponse的子类，可以快速设置状态码

* HttpResponseRedirect  301
* HttpResponsePermanentRedirect  302
* HttpResponseNotModified  304
* HttpResponseBadRequest  400
* HttpResponseNotFound  404
* HttpResponseForbidden  403
* HttpResponseNotAllowed  405
* HttpResponseGone  410
* HttpResponseServerError  500

## 3 JsonResponse

若要返回json数据，可以使用JsonResponse来构造响应对象，作用：

* 帮助我们将数据转换为json字符串
* 设置响应头**Content-Type**为 **application/json**

```python
from django.http import JsonResponse

def demo_view(request):
    return JsonResponse({'city': 'beijing', 'subject': 'python'})
```

## 4 redirect重定向

```python
from django.shortcuts import redirect

def demo_view(request):
    return redirect('/index.html')
```

