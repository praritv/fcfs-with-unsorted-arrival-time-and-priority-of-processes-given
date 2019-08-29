# fcfs-with-unsorted-arrival-time-and-priority-of-processes-given
fcfs with unsorted arrival time and priority of processes given
#include<iostream>
using namespace std;
class block{
	public:
	int at;
	int bt;
	int wt;
	int id;
	int pr;//priority
};
block* bubblesort(block *arr,int n)
{
	int i,j;
	for(int i=0;i<n-1;i++)
	{
		for(int j=0;j<n-i-1;j++)
		{
			if(arr[j].at>arr[j+1].at)
			{
				block temp;
				temp=arr[j];
				arr[j]=arr[j+1];
				arr[j+1]=temp;
			}
			else if(arr[j].at==arr[j+1].at && arr[j].pr>arr[j+1].pr)
			{
				block temp;
				temp=arr[j];
				arr[j]=arr[j+1];
				arr[j+1]=temp;
		    }
		}
	}
	return arr;
}
block* bubblesortid(block *arr,int n)
{
	int i,j;
	for(int i=0;i<n-1;i++)
	{
		for(int j=0;j<n-i-1;j++)
		{
			if(arr[j].id>arr[j+1].id)
			{
				block temp;
				temp=arr[j];
				arr[j]=arr[j+1];
				arr[j+1]=temp;
			}
		}
	}
	return arr;
}
int main()
{
	int b;
	cout<<"Enter the number of elements"<<endl;
	cin>>b;
	block n[b];
	cout<<"Enter the arrival time"<<endl;
	for(int i=0;i<b;i++)
	{
		n[i].id=i; 
		n[i].wt=0; 
		cin>>n[i].at;
	}
	cout<<"Enter the burst time"<<endl;
	for(int i=0;i<b;i++)
	{
		cin>>n[i].bt;
	}
	cout<<"Enter the priority"<<endl;
	for(int i=0;i<b;i++)
	{
		cin>>n[i].pr;
	}
	bubblesort(n,b);
    int y=0;
    n[0].wt=0;
	     for(int i=1;i<b;i++){
	        int x=0;
	        for(int j=0; j<i; j++)
	            n[i].wt+=n[j].bt;
	        if(i>0)
	            x=n[i].at-n[i-1].at-n[i-1].bt;
	        if(x>0)
	            y+=x;
	            n[i].wt = n[i].wt - n[i].at + n[0].at+y;
	          }
                bubblesortid(n,b);
                cout<<endl;
                cout<<"Processes"<<"   "<<"Waiting time"<<endl;
                cout<<"------------------------"<<endl;
				    for(int i=0;i<b;i++)
				    {
				        cout<<"Process("<<n[i].id<<")   "<<"   "<<n[i].wt<<endl;
				    }
	return 0;
}
