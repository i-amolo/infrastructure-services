FROM mcr.microsoft.com/mssql/server:2022-latest

ENV ACCEPT_EULA=Y
ENV SA_PASSWORD=!Pa55w0rd
ENV MSSQL_PID=developer
ENV MSSQL_TCP_PORT=1433

WORKDIR /src

RUN mkdir ./data/mssql
RUN sudo chown mssql ./data/mssql

# Copy file from current dir (that runs docker build) to docker container dir
COPY filldata.sql ./filldata.sql

# RUN SQL SERVER and Access SQL CLI on localhost with given credentials 
# Then run SQL Script - filldata.sql
RUN (/opt/mssql/bin/sqlservr --accept-eula & ) | grep -q "Service Broker manager has started"