## General Information on WebSphere Libery

WebSphere Libery Buildpack provides a WebSphere liberty container capable of running JavaEE apps.  Has support for Spring and includes the IBM JRE.  You can use WebSphere Libery Buildpack to run deploy multiple apps in the same Liberty server.  The buildpack ensures environment variables for backing services are exposed as configuration variables in Liberty.

* IBM JRE 8
* JavaEE 7 Web Profile is enabled
* Default Features
  * beanValidation-1.1, cdi-1.2, ejbLite-3.2, el-3.0, jaxrs-2.0, jdbc-4.1, jndi-1.0, jpa-2.1, jsf-2.2, jsonp-1.0, jsp-2.3, managedBeans-1.0, servlet-3.1, websocket-1.1.
* Can deploy war and ear packaged apps

## Push packaged app  

Packaged server file (``server.xml``) deployments can be pushed and handled by the WebSphere Liberty Buildpack.  In this mode the developer runs Liberty's server package command to bundle a local WebSphere Liberty server for the cloud.

## WebSphere Liberty Start Command

```bash
# buildpack: https://github.com/cloudfoundry/ibm-websphere-liberty-buildpack
> .liberty/create_vars.rb wlp/usr/servers/defaultServer/runtime-vars.xml && \
  .liberty/calculate_memory.rb && \
  WLP_SKIP_MAXPERMSIZE=true \
  JAVA_HOME="$PWD/.java" \
  WLP_USER_DIR="$PWD/wlp/usr" \
  exec .liberty/bin/server run defaultServer
```

## References

https://developer.ibm.com/wasdev/docs/developing-apps-with-intellij-idea-and-liberty-profile/
https://developer.ibm.com/wasdev/downloads/download-latest-stable-websphere-liberty-runtime/
https://app-transformation-cookbook-internal.cfapps.io/javaee/liberty-users-guide/
https://www.ibm.com/support/knowledgecenter/en/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/rwlp_dirs.html
