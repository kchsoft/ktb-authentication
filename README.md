# ktb-authentication
Kakao Api and OAuth 2.0

## 문제 정의
사용자가 나의 서비스를 더 편리하게 사용하기 위해서, 때로는 다른 서비스의 도움을 받아야할 때가 있다.  
예를 들어 게임에 접속하여 친구와 같이 플레이를 한다고 했을 때, 일일히 친구들에게 친구 추가 요청을 보내는 것은 번거롭다.  
하지만 카카오톡으로 로그인하여 게임을 플레이 한다고 했을 때, 카카오톡 친구와 게임 친구 목록이 동일해 진다고 생각해 보자.  
친구요청을 보낼 필요 없이, 바로 게임 플레이를 할 수 있다.  
간단히 말해서 다른 서비스의 유저 정보를 가져와 나의 서비스에 적용시키는 것, 이에 대한 인증을 가능하게 해주는 것이 OAuth 2.0 이다.  
이 프로젝트에는 Kakao API와 OAuth 2.0을 활용하여 로그인 및 인증 기능을 구현한다.  

## 요구 사항
Kakao에 로그인을 할 수 있어야 하며, 로그 아웃 또한 가능해야 한다.  
Kakao에 대한 인증을 마쳤다면, Kakao API를 바탕으로 Kakao 서비스를 이용한다.  

---

## OAuth 2.0 과정
필수 정보 :  
 - Client ID : 인증하는 서비스(카카오,구글,페이스북 등)는 요청(나의 app)하는 app을 구분한다.
 - Client Secret : ID에 대한 비밀번호, __보안 중요__
 - Authorized redirect URIs : 내가 설정한다. 인증을 마친 서비스(카카오,구글 등)는 해당 URI로 redirect한다.  

위의 정보들은 서비스(카카오,구글, 등)에 내 app을 등록하고, 발급 받는다.  

### OAuth 2.0 Onwer 승인 과정  
> 3-1 요청 URL 예시 : https://resource.server/?client_id=abc&scope=B,C&redirect_uri=https://exam/callback
 - scope : 인증하는 서비스(카카오)에서 제공 하는 기능이다. ex) B = 카카오톡 친구 목록 , C = 카카오톡 대화 내용  
<img src="./OAuth2.0 Owner승인.svg" alt="OAuth2.0 Owner승인" width="700" height="700"/>  





### OAuth 2.0 Server 승인 과정
>2. Location : https://client/callback?code=3  

>4. URL : https://resource.server/token?grant_type=authorization_code&code=3&redirect_uri=https://exam/callback&client_id=abc&client_secret=123  

<img src= "./OAuth2.0 Server승인.svg" alt = "OAuth2.0 Server승인" width="700" height="700"/>  


### OAuth 2.0 Access Token 발급 과정
<img src= "./OAuth2.0 AccessToken.svg" alt = "OAuth2.0 Server승인" width="700" height="700"/>
