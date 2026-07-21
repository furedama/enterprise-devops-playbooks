# Apache Tomcat Installation and Configuration Guide

## Overview

This document provides a standard procedure for installing and configuring Apache Tomcat for enterprise Java applications.

## Supported Environment

| Component | Version |
|---|---|
| Operating System | Ubuntu Server 22.04 LTS |
| Java | JDK 8 / JDK 17 |
| Application Server | Apache Tomcat 9.x |
| Database | PostgreSQL |
| Reverse Proxy | Nginx |

---

# Installation Steps

## 1. Install Java

Verify Java installation:

```bash
java -version

Example:

openjdk version "1.8.x"
2. Create Tomcat User

Create a dedicated service account:

sudo useradd -m -d /opt/tomcat -s /bin/bash tomcat
3. Download Apache Tomcat

Example:

wget https://downloads.apache.org/tomcat/

Extract:

tar -xzvf apache-tomcat.tar.gz

Move:

mv apache-tomcat /opt/tomcat
4. Configure Permissions
chown -R tomcat:tomcat /opt/tomcat
5. Configure JVM Options

Example production configuration:

JAVA_OPTS="
-Xms8g
-Xmx12g
-XX:+UseG1GC
-XX:MaxGCPauseMillis=300
-XX:+UseStringDeduplication
"
6. Start Tomcat
cd /opt/tomcat/bin

./startup.sh
7. Verify Service

Check process:

ps -ef | grep tomcat

Check logs:

tail -f /opt/tomcat/logs/catalina.out
Troubleshooting

Common problems:

Application startup failure
JVM memory shortage
Garbage Collection issues
Thread leaks
Database connection failures
Large catalina.out logs
Production Recommendations
Configure log rotation
Monitor JVM memory
Enable health checks
Backup configuration files
Use deployment rollback procedures---
