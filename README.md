### confluence-jira

Đây là bản mới nhất của jira và confluence đã được crack hoàn chỉnh 
để xem chi tiết docker image có thể xem qua các git sau các bạn có thể tự buil và recheck (các bạn cần vào project build gửi mail tới email contact {at} mtz.pw để mình cấp quyền và được cập nhập image version nhanh nhất)

jira: 
https://git.mtz.pw/vouu/jira-build

confluence: 
https://git.mtz.pw/vouu/confluence-build


### chạy phần mềm

```
git clone https://github.com/vncloudsco/confluence-jira.git
cd confluence-jira
docker-compose up -d
``` 

| Phần mềm     | Port |
| ------------ | ----------- |
| jira         | 8080        |
| confluence   | 8090        |


thông tin kết nối db xem trong file  ```database-confluence.env``` và ```database-jira.env``` và điền vào các ô tương ứng khi cài đặt

- lưu ý: 
    - hệ thống sẽ dùng postgres
    - thông tin database host xem bảng bên dưới


| Phần mềm     | dbhost      |
| ------------ | ----------- |
| jira         | jiradb      |
| confluence   | confluencedb|


Thông tin database

| Phần mềm     | database info file     |
| ------------ | ---------------------- |
| jira         | database-jira.env      |
| confluence   | database-confluence.env|


để crack thì chạy lệnh sau 

- lưu ý 
    - nhớ thay 127.0.0.1 thành IP của bạn,
    - confluence thì không cần quan tâm server ID cứ lệnh đó mà chạy
    - jira thì nhớ thay server ID 

```

docker exec jira-srv java -jar /var/agent/atlassian-agent.jar \
    -p jira \
    -m admin@gmail.com \
    -n admin@gmail.com \
    -o http://127.0.0.1:8080 \
    -s BOQU-95EE-NRW6-AQDG

docker exec confluence-srv java -jar /var/agent/atlassian-agent.jar \
    -p conf \
    -m admin@gmail.com \
    -n admin@gmail.com \
    -o http://127.0.0.1:8090 \
    -s 202
```

nền tảng hỗ trợ

| nền tảng     | support   |
| ------------ | --------- |
| x86_64       | yes       |
| ARM          | no        |

Phiên bản hỗ trợ

| Phần mềm     | Version   |
| ------------ | --------- |
| confluence   | 7.14.1    |
| jira         | 8.20.1    |