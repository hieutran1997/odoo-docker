FROM base_odoo:14
MAINTAINER Hieutv26 <hieutv26@viettel.com.vn>

SHELL ["/bin/bash", "-xo", "pipefail", "-c"]

COPY ./entrypoint.sh /entrypoint.sh

RUN chmod +x /entrypoint.sh

RUN dos2unix ./entrypoint.sh

# source code odoo
COPY ./Odoo/ /odoo/

RUN rm -rf /odoo/venv

ENV ODOO_BIN=/odoo/odoo-bin 
ENV ODOO_CONFIG=/odoo/config/odoo.conf
ENV POSTGRES_USER=odoo
ENV PASSWORD=admin@123
ENV DB_HOST=localhost
ENV DB_PORT=5432
ENV HTTP_PORT=8069
ENV DBS=TEST_ERP

# create path external
RUN mkdir -p /odoo/extra-addons
RUN mkdir -p /odoo/data_dir
RUN mkdir -p /odoo/config

EXPOSE 8010 8069 8071 8072

VOLUME ["/odoo/extra-addons", "/odoo/data_dir", "/odoo/config"]

CMD ["./entrypoint.sh"]