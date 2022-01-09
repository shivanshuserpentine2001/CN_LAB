#include<bits/stdc++.h>
#include<unistd.h>
using namespace std;
#define bucketSize 500

void bucketInput(int a,int b) 
{
	if(a > bucketSize)
		cout<<"\n\t\tBucket overflow";
	else{
		sleep(5);
		while(a > b){
			cout<<"\n\t\t"<<b<<" bytes outputted.";
			a-=b;
			sleep(5);
		}
		if(a > 0) 
			cout<<"\n\t\tLast "<<a<<" bytes sent\t";
		cout<<"\n\t\tBucket output successful";
	}
}
int main() 
{
	int op,pktSize;
	cout<<"Enter output rate : "; 
	cin>>op;
	for(int i=1;i<=5;i++)					
	{
		sleep(rand()%10);
		pktSize=rand()%700;
		cout<<"\nPacket no "<<i<<"\tPacket size = "<<pktSize;
		bucketInput(pktSize,op);
	}
	cout<<endl;
	return 0;
}

/*

Enter output rate : 100

Packet no 1     Packet size = 267
                100 bytes outputted.
                100 bytes outputted.
                Last 67 bytes sent
                Bucket output successful
Packet no 2     Packet size = 600
                Bucket overflow
Packet no 3     Packet size = 324
                100 bytes outputted.
                100 bytes outputted.
                100 bytes outputted.
                Last 24 bytes sent
                Bucket output successful
Packet no 4     Packet size = 658
                Bucket overflow
Packet no 5     Packet size = 664
                Bucket overflow  
PS D:\codes\Practice Code\C++\lab> 

*/