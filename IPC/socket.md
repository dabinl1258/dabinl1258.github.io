# socket
socket은 말그대로 멀티탭에 있는 그것을 말하는 것이다.
?? 전류 대신에 connect 하면 신호가 나가는 것이고 unpluge = disconnect 하면 신호를 못 보내는 것으로 생각하면 된다.

다른 점이라면 우리가 이미쓰는 소켓은 콘센트에서 플러그 쪽으로만 전류가 흐르지만 여기에서는 서버(콘센트)와 클라이언트(플러그) 서로 신호 전송이 가능하다.

우리가 콘센트플러그를 원하는 데로 자유롭게 쓰듯이

예를 들어서 휴대폰 배터리가 부족한경우 충전을 하는 경우도 있고 배터리가 충분한 경우 충전을 하는 경우도 있고 휴대폰이 꺼진경우에야 충전 하는 사람도 있다.

마찬가지로 우리의 소켓도 사용자(프로그래머)가 코딩하기에 따라서 다양한 방식으로 구현이 가능하다.


## c와 node js 통신
node js를 서버로 하고
c를 클라이언트로 하여


"bye"를 보내고 연결이 끝어지는 서버를 구현 해보았다. (내가필요해서)
```c

// client.c
#include <sys/types.h>
#include <arpa/inet.h>
#include <sys/socket.h>
#include <stdlib.h>
#include <stdio.h>


int main(int argc , char * argv[])
{		
	int sock;
	int port;
	char * addr ;
	struct sockaddr_in  server;
	char msg[255];

	if(argc < 2 )
		return 0;

	port = atoi(argv[1]);
	addr =  argv[2];
	sock = socket(AF_INET , SOCK_STREAM, 0);
	if ( sock == -1)
	{
		printf("can't create socket ");
		return 0;
	}

	server.sin_addr.s_addr = inet_addr(addr);
	server.sin_family = AF_INET;
	server.sin_port =  htons(port);

	if (connect(sock , (struct sockaddr *) & server , sizeof(server) ) < 0)
	{
		printf("could connect");
		return 0;
	}
	if (recv(sock , msg , 255 , 0) < 0)
	{
		printf ("recive failed");
		return 0;
	}
	printf("%s" , msg);
	return 0;
}

```

```bash
$ gcc client.c
```

```js
const net  = require("net")
port = 1234
addr = "127.0.0.1"
var server = net.createServer(function (socket) {
  socket.end("bye");
  server.close();
});
server.listen(port , addr);
console.log("end");
```
