DispatcherServlet
---

> DispatcherServlet 是 Spring MVC 框架中的前端控制器（Front Controller）负责处理传入的 HTTP 请求并将其分发给相应的处理程序（Controller）

**它的主要功能包括**
- 请求分发：根据请求的 URL 和配置的映射规则，将请求分发给相应的 Controller 方法。

- 视图解析：处理完请求后，负责将处理结果渲染为视图并返回给客户端。

- 异常处理：处理请求处理过程中抛出的异常，并返回适当的错误响应。

- 多视图支持：支持多种视图技术，如 JSP。

**工作流程**
- 接收请求：DispatcherServlet 接收来自客户端的 HTTP 请求。

- 查找 Handler：根据请求的 URL 和配置的映射规则，查找相应的 Handler（Controller 方法）。

- 执行 Handler：调用相应的 Handler 方法处理请求。

- 处理结果：Handler 方法返回处理结果（如视图名称、模型数据等）。

- 视图解析：DispatcherServlet 根据返回的视图名称，查找并渲染相应的视图。

- 返回响应：将渲染后的视图返回给客户端。
