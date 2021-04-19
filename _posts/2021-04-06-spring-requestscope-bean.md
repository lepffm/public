---
layout: post
title: "spring @requestscope bean usage"
---
# subject
example for spring requestscope bean

# purpose
send web layer  information to service layer

# description
flow

user request -> webconfig -> interceptor (set ip) -> controller (call service) -> service (use RCBean)
```
@Data
public class WebData{
  private String uri;
}
---
@Configuration
public class WebConfig implements WebMvcConfigurer{

  @Bean
  @RequestScope
  public WebData requestRSBean(){ return new WebData(); }

  @Bean public MyInterceptor  getInterceptor(){ return new MyInterceptor(); }

  @Override public void addInterceptors(InterceptorRegistry ir){
    ir.addInterceptor(getInterceptor());
  }
}
---
public class MyInterceptor extends HandleInterceptorAdaptor{
  private WebData webData;
  @Override public boolean preHandle(HttpServletRequest req, HttpServletResponse res, Object handler) throws Exception{
    webData.setUri( req.getRequestURI());
    return true;
  }
}
---
@Service
public class MyService {
  private WebData webData;
  public hello(){
    return webData.getUri();
  }
}
```
