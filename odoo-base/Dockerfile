FROM debian:bullseye-slim

LABEL author="Aymen Jemi (Aisysnext Ltd)"


RUN apt update && apt install -y python3 python3-pip python3-dev wget curl gnupg wkhtmltopdf  python3-xlwt python3-num2words
RUN apt install -y npm node-less

# install nodejs libs
RUN npm install -g rtlcss less less-plugin-clean-css


# remove apt cache
RUN apt clean

# Expose Odoo services
EXPOSE 8069 8072

CMD ["bash"]