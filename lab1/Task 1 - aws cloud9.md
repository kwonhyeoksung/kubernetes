# Task 1 - aws cloud 9  

### aws 의 Cloud9 서비스를 사용하여 실습에서 사용할 IDE 환경을 구축  

1. 제공된 링크로 접속하고, 제공받은 계정정보로 로그인합니다.

![image](https://user-images.githubusercontent.com/92773629/160507348-cafdaaf2-080f-4e2c-95cb-3305a499093f.png)

2. 우측 상단 '지역'을 클릭하고 '서울'을 클릭합니다.

![image](https://user-images.githubusercontent.com/92773629/160509195-5f8e45a9-e4be-4dd9-81c3-354c9bf8577f.png)

<br/>

3. 상단 검색창에 Cloud9 을 검색하고 Cloud9 서비스를 클릭합니다.

![image](https://user-images.githubusercontent.com/92773629/137866767-ff6f5a76-1d89-49d0-9c69-21d800131b74.png)

<br/>

4. Create environment 를 클릭합니다.

![image](https://user-images.githubusercontent.com/92773629/137866834-b127941e-57e2-4b9f-aed0-43cb7836603d.png)

<br/>

5. Name란에 제공받은 계정명을 입력하고 Next step 을 클릭합니다.

![image](https://user-images.githubusercontent.com/92773629/160509447-d8d571bf-c502-463b-a271-96b64aca6ed9.png)

<br/>

6. Configure settings 에서 Instance type 을 t3.small 을 선택하고, Platform의 Ubuntu server 18.04 선택 후 Next step 버튼을 클릭합니다.
그리고 선택한 내용 확인 후 Create environment 버튼 클릭합니다.

![image](https://user-images.githubusercontent.com/92773629/160509632-1491e3bd-de27-440b-9f72-2ae25c7afda5.png)

7. 제공받은 pem 파일을 Cloud 환경에서 좌측상단 File - Upload Local Files 를 클릭하여 해당 파일을 업로드합니다.

![image](https://user-images.githubusercontent.com/92773629/137873529-5837be1a-d45f-46aa-9376-90eb1786ff34.png)  
![image](https://user-images.githubusercontent.com/92773629/137873582-384779d7-ec24-4e5f-9a96-6198add963b8.png)

<br/>

8. 해당명령으로 key 파일의 권한을 변경합니다.

```
chmod 600 k8skey.pem
```

9. 해당 명령으로 master 노드에 접속합니다.

```
ssh -i k8skey.pem <master ip>
```
![image](https://user-images.githubusercontent.com/92773629/137873943-2c1d74aa-5954-4ef9-a73f-6e61d8b9015e.png)

<br/>
