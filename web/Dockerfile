FROM nginx:latest
    RUN apt-get update && apt-get upgrade -y
    RUN apt-get install -y wget
    ## Install the RADIUSdesk CakePHP v2 Application
    RUN wget https://github.com/cakephp/cakephp/archive/2.10.22.tar.gz
    RUN cp 2.10.22.tar.gz /usr/share/nginx/html/
    RUN cd /usr/share/nginx/html/ && tar -xzvf /usr/share/nginx/html/2.10.22.tar.gz && \
        ln -s ./cakephp-2.10.22/ ./cake2
        
    ##RUN service php7.3-fpm reload
    RUN apt-get install subversion -y
    RUN cd /usr/share/nginx/html/cake2/
    RUN svn checkout svn://dvdwalt@svn.code.sf.net/p/radiusdesk/code/trunk/rd_cake ./rd_cake/
    RUN cd /usr/share/nginx/html/
    RUN chown -R www-data. /usr/share/nginx/html/cakephp-2.10.22/
    ## Install the RADIUSdesk CakePHP v3 Application
    RUN cd /usr/share/nginx/html/ && svn checkout svn://dvdwalt@svn.code.sf.net/p/radiusdesk/code/trunk/cake3 ./cake3/
    RUN chown -R www-data. /usr/share/nginx/html/cake3/
    ## Viewer Component
    RUN cd /usr/share/nginx/html/ && \
        svn checkout svn://dvdwalt@svn.code.sf.net/p/radiusdesk/code/trunk/rd ./rd/ && \
        svn checkout svn://svn.code.sf.net/p/radiusdesk/code/extjs ./ && \
        mv  ext-6-2-sencha_cmd.tar.gz ./rd/ && \
        cd /usr/share/nginx/html/rd/ && \
        tar -xzvf ext-6-2-sencha_cmd.tar.gz
    #RUN cp /usr/share/nginx/html/cake2/rd_cake/Setup/Cron/rd /etc/cron.d/
