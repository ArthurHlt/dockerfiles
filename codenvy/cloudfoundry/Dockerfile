FROM codenvy/jdk7
RUN mkdir /home/user/cf
WORKDIR /home/user/cf
RUN wget -q http://go-cli.s3-website-us-east-1.amazonaws.com/releases/v6.7.0/cf-cli_amd64.deb && \
    sudo dpkg -i cf-cli_amd64.deb
RUN mkdir /home/user/app
WORKDIR /home/user/app

RUN cf login --skip-ssl-validation -a ${CF_API} -u ${CF_LOGIN} -p ${CF_PASSWORD} -o ${CF_ORG} -s ${CF_SPACE}
ENV appName myApp-ahalet
VOLUME ["/home/user/app"]
ENV CODENVY_APP_BIND_DIR /home/user/app
CMD cf push ${appName} >&1 && cf logs ${appName} >&1

