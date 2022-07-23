---
layout: post
title: MSSQL server in Ubuntu 21.04 + Connecting it with SSMS in Windows
subtitle:
cover-img: /assets/img/dotnet.jpg
thumbnail-img: /assets/img/hello_world.jpeg
share-img: /assets/img/hello_world_jpeg
tags: [c#, csharp,.net, msssql ]
comments: true
---
## Installing Microsoft SQL Server 2019 on Ubuntu 21.04

#### Step 1: Import Public Repository GPG keys

{: .box-warning}
sudo wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

#### Step 2: Register Microsoft SQL Server Ubuntu Repository for SQL Server 2019

{: .box-warning}
sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/20.04/mssql-server-2019.list)"

#### Step 3: Install SQL Server

{: .box-warning}
sudo apt update
{: .box-warning}
sudo apt install -y mssql-server

#### Step 4: Configure SQL server and give a password

{: .box-warning}
sudo /opt/mssql/bin/mssql-conf setup

#### Step 5: Start the service

{: .box-warning}
sudo systemctl start mssql-server

#### Step 6: Check for status

{: .box-warning}
sudo systemctl status mssql-server

## Setting up Remote Connection to SQL Server and Connecting to SSMS in Windows

#### Step 1: Enable port 1433 and 1434 on firewall

{: .box-warning}
sudo ufw enable
{: .box-warning}
sudo ufw allow 1433
{: .box-warning}
sudo ufw allow 1434

#### Step2: Download SSMS for Windows

{: .box-warning}
https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver15

#### Step 3: Connect to Server 

{: .box-warning}
Server Type:   Database Engine
{: .box-warning}
Server Name:   <<Computer Name or IP>>
{: .box-warning}
Authentication:SQL Server Authentication
{: .box-warning}
Login:         SA
{: .box-warning}
Password:      *********

Connect and good to go....