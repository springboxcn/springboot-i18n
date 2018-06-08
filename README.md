# springboot-i18n


- https://blog.csdn.net/linxingliang/article/details/52350238
- https://stackoverflow.com/questions/36655104/spring-boot-localization-issue-accept-language-header


```java
String lang = LangAOP.getLang();
MessageSource source = new DelegatingMessageSource();
source.getMessage("20000",null,new Locale(lang,lang));
```
