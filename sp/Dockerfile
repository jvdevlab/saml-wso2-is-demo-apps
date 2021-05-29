FROM tomcat:9-jdk15-openjdk-slim

ARG DOWNLOAD_URL=https://github.com/wso2/samples-is/releases/download/v4.3.0/
ARG WAR_NAME
ARG CONFIG_DIR

WORKDIR /usr/local/tomcat/webapps
ADD ${DOWNLOAD_URL}${WAR_NAME} ./${WAR_NAME}

# ServletContextListener.class inside saml2-web-app-pickup-dispatch.com.war\WEB-INF\classes\
# loads properties using getClassLoader().getResourceAsStream("sso.properties")
# BUT putting properties into /usr/local/tomcat/lib/ will not work because
# SSOAgentContextEventListener.class (and others) inside WEB-INF/lib/org.wso2.carbon.identity.sso.agent-5.3.4.jar
# loads properties using getServletContext().getResourceAsStream("/WEB-INF/classes/" + propertyFileName)
# which will look for the properties in the root of the webapp according to this
# https://docs.oracle.com/javaee/7/api/javax/servlet/ServletContext.html#getResource-java.lang.String-
# thus, have to replace props inside the war.
COPY ${CONFIG_DIR}/sso.properties ./WEB-INF/classes/
RUN jar -uf ${WAR_NAME} WEB-INF && rm -r WEB-INF

EXPOSE 8080
CMD ["catalina.sh", "run"]