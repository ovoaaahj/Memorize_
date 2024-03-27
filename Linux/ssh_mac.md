<h2>step 1</h2>  /.ssh 폴더 생성하기 (해당폴더에 기본키와 공개키 넣어줄 예정)<br><br>


```bash
mkdir ~/.ssh
```

<h2>step 2</h2>  다운받은 공개키 및 비밀키 .ssh 폴더로 복사하기<br><br>

```bash
cp /Downloads/공개키정보 ~/.ssh
cp /Downloads/비밀키정보 ~/.ssh
```

<h2>step 3</h2>  비밀키 권한 변경하기 <br><br>

```bash
cd ~/.ssh
chmod 600 비밀키정보
```

<h2>step 4</h2>  config 파일 생성하기 <br><br>

```bash
vim config
```

<h2>step 5</h2>  config 파일 내용 작성하기 <br><br>

```bash
Host 접속할때사용할이름
HostName IP정보
User 사용자ID
IdentityFile ~/.ssh/비밀키정보
```

<h2>step 6 </h2>  실행하기 <br><br>

```bash
ssh 접속할때사용할이름
```

<br><br><br><br><br><br>
<strong>참고자료 :: https://github.com/Bletcher-Project/bletcher_mix/issues/8 </strong>


