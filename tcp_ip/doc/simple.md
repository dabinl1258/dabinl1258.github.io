# 가장 기초적인 소켓 예제 입니다.


server.c
```c
#include <stdio.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>
#include <sys/types.h>
#include <pthread.h>


int main(int argc , char ** argv)
{
	int listenfd =0 , connectfd = 0;
	struct sockaddr_in  serv_addr;
	char sendBuffer[255];
	int port;

	time_t ticks;
	
	if ( argc < 2)
	{
		printf(" few argument \n");
		return 0;
	}
	
	listenfd = socket(AF_INET, SOCK_STREAM,0 );

	memset(&serv_addr, 0 , sizeof(serv_addr));
	memset(&sendBuffer , 0 , sizeof(sendBuffer));
	port = atoi(argv[1]);

	serv_addr.sin_family = AF_INET;
	serv_addr.sin_addr.s_addr = htonl(INADDR_ANY);
	serv_addr.sin_port = htons(port);

	if (bind(listenfd , (struct sockaddr *)&serv_addr,   sizeof(serv_addr)) < 0)
	{
		printf("bind false\n");
		return 0;
	}

	listen(listenfd , 10);
	

	connectfd = accept(listenfd , (struct  sockaddr *)NULL  , NULL);
	printf("accepted \n");

	sprintf(sendBuffer, "hi you");
	send(connectfd , sendBuffer, sizeof(sendBuffer), 0);

	close(connectfd);

	
	return 0;


}

```

socket을 이용하여 소켓을 생성합니다.

여기에서 AF_INET은 IPV4 주소체계 , SOCK_STREAM tcp 프로토콜입니다. tcp는 순서대로 정확히 데이터를 전송합니다.

memset을 이용하여 struct sockaddr_in와 sendBuff를 0으로 초기화 시킴니다.

struct sockaddr_in serv_sock에 데이터를 초기화 합니다.

htonl , htons 함수는 일반적으로 x86에서 사용하는 little-endian을 네트워크에서 사용하는 big-endian으로 전환합니다.
(little-endian과 big-endian은 MSB와 LSB가 반대에 위치해 있습니다).

atoi(argv[1]) , atoi 함수를 이용하여 cahr 배열 형테의 port 번호를 정수형으로 변환합니다.

bind()는 소켓을 바인드 시키는 것입니다. 운영체제에서 해당 포트를 이미 쓰고 있으면 -1을 리턴 합니다.

listen은 이제 클라인언트가 접속하기를 기다리는 것 입니다.

클라인언트가 연결이 되면 accept함수가 클라이언트의 fd(file descriptor)를 반환합니다.

sprintf로 sendBuffer에 문자열을 담습니다.

send로 문자열을 보내고 
close로 연결된 클라이언트를 끊습니다.



client.c 
```c 
#include <stdio.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>
#include <sys/types.h>
#include <time.h>

int main(int argc , char ** argv)
{
	int listenfd =0 , connectfd = 0;
	struct sockaddr_in  serv_addr;
	char sendBuffer[255];
	int port;

	time_t ticks;
	
	if ( argc < 2)
	{
		printf(" few argument \n");
		return 0;
	}
	
	listenfd = socket(AF_INET, SOCK_STREAM,0 );

	memset(&serv_addr, 0 , sizeof(serv_addr));
	memset(&sendBuffer , 0 , sizeof(sendBuffer));
	port = atoi(argv[1]);

	serv_addr.sin_family = AF_INET;
	serv_addr.sin_addr.s_addr = htonl(INADDR_ANY);
	serv_addr.sin_port = htons(port);

	if (bind(listenfd , (struct sockaddr *)&serv_addr,   sizeof(serv_addr)) < 0)
	{
		printf("bind false\n");
		return 0;
	}

	listen(listenfd , 10);
	

	connectfd = accept(listenfd , (struct  sockaddr *)NULL  , NULL);
	printf("accepted \n");


	recv(connectfd , sendBuffer , sizeof(sendBuffer),0);
    printf("%s\n", sendBuffer);

	close(connectfd);
	return 0;
}

```

클라이언트에서도 비슷한 것을 행하지만 몇가지 차이점이 있습니다.

inet_pton은 "127.0.0.1"등의 도메인 주소를 serv_addr.sin_addr.s_addr에 적합한 형태로 변환합니다.
connect는 실제 서버에 접속하는 것이고 서버에 대한 fd를 받습니다.
recv함수는 버퍼에 반대쪽에서 보내는 문자열을 받아서 옮깁니다.

