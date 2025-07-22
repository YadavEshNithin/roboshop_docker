FROM python:3.9.23-alpine3.22 AS builder
WORKDIR /opt/server
RUN apk add --no-cache gcc musl-dev python3-dev libffi-dev openssl-dev
COPY payment.ini /opt/server/
COPY *.py /opt/server/
COPY requirements.txt /opt/server/
RUN pip install -r requirements.txt
RUN find / -name uwsgi -type f

FROM python:3.9.23-alpine3.22
WORKDIR /opt/server
# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop \
#     && chown -R roboshop:roboshop /opt/server 
# USER roboshop
ENV PATH="/usr/local/bin:${PATH}"
COPY --from=builder /opt/server /opt/server/
CMD ["uwsgi", "--ini", "payment.ini"]

# FROM python:3.9.23-alpine3.22
# EXPOSE 8080
# WORKDIR /opt/server
# COPY requirements.txt .
# COPY *.py .
# COPY payment.ini .
# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop \
#     && chown -R roboshop:roboshop /opt/server 
# RUN apk add --no-cache python3-dev build-base linux-headers pcre-dev
# RUN pip3 install -r requirements.txt
# # USER roboshop
# CMD ["uwsgi", "--ini", "payment.ini"]


# FROM python:3.9
# EXPOSE 8080
# WORKDIR /opt/server
# COPY requirements.txt .
# COPY *.py .
# COPY payment.ini .
# RUN pip3 install -r requirements.txt
# CMD ["uwsgi", "--ini", "payment.ini"]