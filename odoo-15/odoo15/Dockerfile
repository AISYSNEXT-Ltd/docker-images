FROM jemiaymen/odoo:base

LABEL author="Aymen Jemi (Aisysnext Ltd)"

RUN wget -O - https://nightly.odoo.com/odoo.key | apt-key add -
RUN echo "deb http://nightly.odoo.com/15.0/nightly/deb/ ./" >> /etc/apt/sources.list.d/odoo.list
RUN apt update && apt install -y odoo

RUN pip3 install prestapyt psycopg2-binary future



# Copy entrypoint script and Odoo configuration file
COPY ./entrypoint.sh /
COPY ./odoo.conf /etc/odoo/
RUN chmod -R 0755 /entrypoint.sh

# Set permissions and Mount /var/lib/odoo to allow restoring filestore and /mnt/extra-addons for users addons
RUN chown odoo /etc/odoo/odoo.conf \
    && mkdir -p /mnt/extra-addons \
    && chown -R odoo /mnt/extra-addons
VOLUME ["/var/lib/odoo", "/mnt/extra-addons"]

# Set the default config file
ENV ODOO_RC /etc/odoo/odoo.conf

COPY wait-for-psql.py /usr/local/bin/wait-for-psql.py
RUN chmod -R 0755 /usr/local/bin/wait-for-psql.py



# remove apt cache
RUN apt clean

# Expose Odoo services
EXPOSE 8069 8072


ENTRYPOINT ["/entrypoint.sh"]
CMD ["odoo"]