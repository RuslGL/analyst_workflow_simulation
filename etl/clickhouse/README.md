# ClickHouse Setup Guide

## English 🇬🇧

### Instructions for Deploying and Configuring ClickHouse

**Without the entire project, for example, on VPS.**

### 📌 Installation

1. **Clone the Repository with Only the ClickHouse Folder:**
   ```bash
   git clone --no-checkout git@github.com:RuslGL/analyst_workflow_simulation.git && cd analyst_workflow_simulation
   git sparse-checkout init && git sparse-checkout set etl/clickhouse && git checkout
   mv etl/clickhouse ../ && cd ..
   rm -fr analyst_workflow_simulation
   ```

### !!! Change credentials in the docker-compose file
2. **Go to the ClickHouse Directory and Start the Container:**
   ```bash
   cd clickhouse
   docker-compose up -d
   ```

3. **Check Running Containers:**
   ```bash
   docker ps
   ```

4. **Connect to the ClickHouse Container:**
   ```bash
   docker exec -it [CONTAINER NAME / ID] bash
   ```

5. **Open ClickHouse Client:**
   ```bash
   clickhouse-client -u prev_user_name
   ```

### * following steps only if necessary
6. **Create a New User:**
   ```sql
   CREATE USER new_user_name IDENTIFIED BY 'new_password';
   ```

7. **Grant Permissions to the New User:**
   ```sql
   GRANT SHOW, SELECT, INSERT, ALTER, CREATE, DROP, UNDROP TABLE, TRUNCATE, OPTIMIZE, BACKUP, 
          KILL QUERY, KILL TRANSACTION, MOVE PARTITION BETWEEN SHARDS, ROLE ADMIN, 
          CREATE ROW POLICY, ALTER ROW POLICY, DROP ROW POLICY, 
          CREATE QUOTA, ALTER QUOTA, DROP QUOTA, 
          CREATE SETTINGS PROFILE, ALTER SETTINGS PROFILE, DROP SETTINGS PROFILE, 
          ALLOW SQL SECURITY NONE, SHOW ACCESS, SYSTEM, dictGet, displaySecretsInShowAndSelect, 
          INTROSPECTION, SOURCES, CLUSTER, TABLE ENGINE, CREATE USER, ALTER USER, DROP USER, 
          CREATE ROLE, ALTER ROLE, DROP ROLE, SET DEFINER
   ON *.* TO new_user_name;
   ```

8. **Delete the Previous User:**
   ```sql
   DROP USER prev_user_name;
   ```

9. **Show the List of Users:**
   ```sql
   SHOW USERS;
   ```

10. **Connect with the New User:**
   ```bash
   clickhouse-client -u new_user_name --password new_password
   ```

---

## Русский 🇷🇺

### Инструкция по Разворачиванию и Настройке ClickHouse

**Без остального проекта, например, на VPS.**

### 📌 Установка

1. **Клонируйте Репозиторий с Папкой ClickHouse:**
   ```bash
   git clone --no-checkout git@github.com:RuslGL/analyst_workflow_simulation.git && cd analyst_workflow_simulation
   git sparse-checkout init && git sparse-checkout set etl/clickhouse && git checkout
   mv etl/clickhouse ../ && cd ..
   rm -fr analyst_workflow_simulation
   ```
### !!! Измените логин и пароль в файле  docker-compose

2. **Перейдите в Папку ClickHouse и Запустите Контейнер:**
   ```bash
   cd clickhouse
   docker-compose up -d
   ```

3. **Проверьте Запущенные Контейнеры:**
   ```bash
   docker ps
   ```

4. **Подключитесь к Контейнеру ClickHouse:**
   ```bash
   docker exec -it [CONTAINER NAME / ID] bash
   ```

5. **Откройте Клиент ClickHouse:**
   ```bash
   clickhouse-client -u prev_user_name
   ```

### * дальнейшие шаги по мере необходимости
6. **Создайте Нового Пользователя:**
   ```sql
   CREATE USER new_user_name IDENTIFIED BY 'new_password';
   ```

7. **Выдайте Права Новому Пользователю:**
   ```sql
   GRANT SHOW, SELECT, INSERT, ALTER, CREATE, DROP, UNDROP TABLE, TRUNCATE, OPTIMIZE, BACKUP, 
          KILL QUERY, KILL TRANSACTION, MOVE PARTITION BETWEEN SHARDS, ROLE ADMIN, 
          CREATE ROW POLICY, ALTER ROW POLICY, DROP ROW POLICY, 
          CREATE QUOTA, ALTER QUOTA, DROP QUOTA, 
          CREATE SETTINGS PROFILE, ALTER SETTINGS PROFILE, DROP SETTINGS PROFILE, 
          ALLOW SQL SECURITY NONE, SHOW ACCESS, SYSTEM, dictGet, displaySecretsInShowAndSelect, 
          INTROSPECTION, SOURCES, CLUSTER, TABLE ENGINE, CREATE USER, ALTER USER, DROP USER, 
          CREATE ROLE, ALTER ROLE, DROP ROLE, SET DEFINER
   ON *.* TO new_user_name;
   ```

8. **Удалите Предыдущего Пользователя:**
   ```sql
   DROP USER prev_user_name;
   ```

9. **Покажите Список Пользователей:**
   ```sql
   SHOW USERS;
   ```

10. **Подключитесь с Новым Пользователем:**
   ```bash
   clickhouse-client -u new_user_name --password new_password
   ```

