# DB연동하기

 기본적으로 **DB user**와 **password**는 *root*이고, **database 이름**은 *TFC* 입니다. **포트번호**는 *3306*입니다.

 만약 변경을 원하시면 
  - main.php
  - board.php
  - gadetail.php
  - season.php
  - region.php
  - signup.php
  - thismonth.php
  - wanting.php
  - login.php

  위 파일들의 최상단에 *$username, $password, $db_name*의 변수값을 변경하시면 됩니다. 
  (포트번호는 고정해주셔야합니다.)

# DB 한글 깨짐 해결

&nbsp;&nbsp;웹에서 언어인코딩을 UTF-8을 사용하기 때문에 윈도우에서 크롤링 후 DB에 값을 삽입하면 인코딩이 달라 한글 깨짐이 발생할 수 있습니다. 
mysql설정 파일인 my.cnf에서 아래와 같이 수정하시면 됩니다.

my.cnf 파일을 열어서 

|요소|삽입문장|
|----|--------|
|[client]|default-character-set = utf8|
|[mysqld]|character-set-client-handshake=FALSE<br><br>init_connect=&quot;SET collation_connection = utf8_general_ci&quot;<br><br>init_connect=&quot;SET NAMES utf8&quot;<br><br>character-set-server = utf8<br><br>collation-server = utf8_general_ci|
|[mysqldump]|default-character-set = utf8|
|[mysql]|default-character-set = utf8|

각 요소를 찾아 요소 아래에 해당하는 문장을 삽입하면됩니다.

테이블에 나와있는 문장들을 삽입한 후 **cmd** 를 켜서 **chcp 65001** 입력합니다. 

그 후 mysql을 접속하여 정상 이용하시면 됩니다.

# DB 테이블 생성

mysql에 접속한 후 **sqlData.sql** 파일 내용을 복사 붙여넣기 하시면 됩니다. 

**"TFC"** 라는 database를 **삭제**하고 **생성**하는 쿼리문이니 주의해서 사용해 주시기 바랍니다.

# 웹 크롤링 프로그램

**extract.jar**은 맥용이며 **extract.exe**는 윈도우용입니다. 물론 extract.jar는 윈도우에서도 사용가능합니다.

각 TextField에는 Label에 맞는 값을 입력하여 주시면 됩니다.(포트 번호는 3306 고정)

Start옆의 TextField는 문화제청에서 업데이트하고자하는 게시판 번호를 입력하시면됩니다. **입력시 ~로 범위를 지정**해주셔야하며 5000~8000과 같은 형식으로 ~에 숫자를 붙여주셔야합니다. 서버단에서 이용하는 프로그램이라 따로 잘못된 인풋에 대해서는 처리하지 않아서 **반드시** 지켜주셔야합니다.

게시판 번호는 5000번대부터 2017년의 축제들이 시작되므로 5000대 이하의 값은 입력하셔도 DB에 들어가는 값이 없을 수 있습니다. (2016년의 값은 집어넣지 못하도록 막아놓음)

크롤링 프로그램을 구동하면 구동한 위치에 img라는 폴더가 만들어지고 그곳에 게시판 아이디의 이름을 가진 게시판 **이미지**가 다운로드 됩니다. 

img 폴더와 main.php 파일은 동일한 위치에 있어야 이미지가 웹페이지에서 제대로 적용됩니다.

(윈도우에서는 DB 삽입 중에 간혹 한글 깨짐이 발생할 수 있습니다.)

# 실행이 안될 경우

파일이나 폴더경로를 정확히 확인해주시고, 그래도 안된다면 dudu016@naver.com으로 연락 주시면 감사하겠습니다.
