# springboot-i18n


- https://blog.csdn.net/linxingliang/article/details/52350238
- https://stackoverflow.com/questions/36655104/spring-boot-localization-issue-accept-language-header


```java
String lang = LangAOP.getLang();
MessageSource source = new DelegatingMessageSource();
source.getMessage("20000",null,new Locale(lang,lang));
```


```java
@AfterReturning(returning = "rvt",value = "controllerLangPointcut()")
public void resetCode(Object rvt) throws Throwable {
    String lang = LangAOP.getLang();
    //MessageSource source = new DelegatingMessageSource();
    MessageSource source = SpringContextUtil.getBean(MessageSource.class);
    System.out.println("====================================");
    System.out.println(source.getMessage("20000", null, "unknown code", new Locale(lang, lang)));
    BaseResp resp = (BaseResp) rvt;
    resp.setDesc(source.getMessage("20000", null, "unknown code", new Locale(lang, lang)));
}
```

```yml
spring:
  messages:
    basename: i18n/messages
    cache-seconds: 60
    fallback-to-system-locale: false
    encoding: UTF-8
```    
    
- `main\resources\i18n\messages.properties`
- `main\resources\i18n\messages_cn.properties`
- `main\resources\i18n\messages_en.properties`

    
