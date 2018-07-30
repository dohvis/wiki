# My-dev-cheatsheet

## Regular Expression

전,후방 탐색

```python
from re import search

search(r'\d+(?=원)', '10000원').group()  # '10000'
search(r'(?<=price:)\d+', 'price:10000').group() # '10000'


pattern = r'(?P<item>\w+):(?P<price>\d+)(?=\$)'
string = 'apple:1000$'

search(patten, string).group()
# 'apple:1000'

search(pattern, string).group('item')
# 'apple'

search(patten, string).groups()
# ('apple', '1000')

search(pattern, string).groupdict()
# {'item': 'apple', 'price': '1000'}

# compile 이용한 방법 추가
```

[출처 - 금지된 엑시노아의 비공정 - 정규 표현식\(Regex\) 강좌 9편. 전후방탐색\(lookaround\)](http://blog.eairship.kr/205)

[출처2 - ┗System∑Sec†ion┛](http://devanix.tistory.com/296)

## scp

#### 전송

scp 파일 계정@서버주소:목적경로

* `scp test.txt nero@8.8.8.8:/home/nero/target_dir/`

#### 수신

scp 계정@서버주소:원본경로 목적파일명

* `scp testuser@8.8.8.8:/var/www/html/index.html ./8.html`

디렉토리 전달 옵션

* `scp -r testuser@8.8.8.8:/var/www/html/ /var/www/`

출처: [http://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4\_scp\_%EC%82%AC%EC%9A%A9%EB%B2%95](http://zetawiki.com/wiki/리눅스_scp_사용법)

## python에서 system\(\) 결과

python3.5 이상이면

```python
result = subprocess.run(['ls', '-l'], stdout=subprocess.PIPE)
result.stdout.decode('utf-8')
```

[http://stackoverflow.com/questions/4760215/running-shell-command-from-python-and-capturing-the-output](http://stackoverflow.com/questions/4760215/running-shell-command-from-python-and-capturing-the-output)

# Ubuntu

## 우분투 버전 확인

`$ lsb_release -a`

## tar 압축,해제

* `tar xvzf toextract.tar.gz`
* `tar cvzf tocompression.tar.gz files...`

## SQL

```
UPDATE table_name SET column=value, col2=val2 WHERE 1=1;
```

# MySQL

## 사용자 계정 추가

```
CREATE DATABASE DB default character set utf8;
GRANT ALL PRIVILEGES ON DB.* TO USER_NAME@localhost
    IDENTIFIED BY 'PASSWORD';
flush privileges;
SHOW GRANTS FOR USER_NAME@localhost;
```

# PostgreSQL

## 사용자 계정 추가

```
sudo su - postgres
psql
CREATE DATABASE {}db;
CREATE USER {}user WITH PASSWORD 'password';
ALTER ROLE {}user SET client_encoding TO 'utf8';ALTER ROLE {}user SET default_transaction_isolation TO 'read committed';ALTER ROLE {}user SET timezone TO 'UTC-9';
GRANT ALL PRIVILEGES ON DATABASE {}db TO {}user;
\q
```

## Python3 멀티프로세싱

```python
from multiprocessing impogt Pool
from os impogt getpid

def func(argv):
    print("pidd = {} , argv[0] : {}, argv[1] : {}".format(getpid(),argv[0],argv[1]))
    return argv[0]+argv[1]

with Pool(processes=4) as pool:
    _list = pool.map(func,zip(range(10),range(10,21,1)))
print("return value list : {}".format(_list))


"""
    return value list : [10, 12, 14, 16, 18, 20, 22, 24, 26, 28]
    pidd = 18634 , argv[0] : 0, argv[1] : 10
    pidd = 18633 , argv[0] : 1, argv[1] : 11
    pidd = 18631 , argv[0] : 6, argv[1] : 16
    pidd = 18632 , argv[0] : 2, argv[1] : 12
    pidd = 18634 , argv[0] : 3, argv[1] : 13
    pidd = 18634 , argv[0] : 4, argv[1] : 14
    pidd = 18634 , argv[0] : 5, argv[1] : 15
    pidd = 18634 , argv[0] : 7, argv[1] : 17
    pidd = 18634 , argv[0] : 8, argv[1] : 18
    pidd = 18634 , argv[0] : 9, argv[1] : 19
"""
```

## [리스트 집합 관계 - 점프 투 파이썬](https://wikidocs.net/1015)

## Sublime Text

[개행되어있는 텍스트 리스트형태로 편하게 바꾸기](http://www.sublimetext.com/forum/viewtopic.php?f=2
&
p=48955)

## Alembic

[https://eshlox.net/2017/08/06/alembic-migration-for-string-length-change/](https://eshlox.net/2017/08/06/alembic-migration-for-string-length-change/)

[http://blog.code4hire.com/2017/06/setting-up-alembic-to-detect-the-column-length-change/](http://blog.code4hire.com/2017/06/setting-up-alembic-to-detect-the-column-length-change/)

