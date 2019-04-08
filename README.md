#include<stdio.h>
int main()
{
	int n;
	printf("Enter no of students : ");
	scanf("%d",&n);
	printf("\n");
	int waiting_time[n],priority[n],process[n],burst_time[n], i, j,k ,temp;
	float avg_waiting_time ,sum=0;
	
	printf("Enter priority as equal to no of gifts. \n");
	for(i=0;i<n;i++)
	{
		printf("\nProcess [%d] \n",i+1);
		printf("Enter no of gifts of student %d: ",i+1);
		scanf("%d",&priority[i]);
		printf("Enter time for billing of student %d : ",i+1);
		scanf("%d",&burst_time[i]);
		printf("\n");
		process[i]=i+1;
	}
	
	for(i = 0; i < n-1; i++)
    {
        for(j = 0; j < n-i-1; j++)
        {
        if(priority[j] < priority[j+1])
        {
        temp = priority[j];
        priority[j] = priority[j+1];
        priority[j+1] = temp; 
        temp = burst_time[j];
        burst_time[j] = burst_time[j+1];
        burst_time[j+1] = temp;
        temp = process[j];
        process[j] = process[j+1];
        process[j+1] = temp;
    	}
    	}
	}
  
	waiting_time[0] = 0;
    for(i = 1; i < n; i++)
    {
        waiting_time[i] = 0;
        for(j = 0; j < i; j++)
        {
            waiting_time[i] = waiting_time[i] + burst_time[j];
        }
        sum = sum + waiting_time[i];
    }
    avg_waiting_time = sum/n;
    printf("\nProcess Id\tNo. of gifts\tBurst Time\t Waiting Time \n");
    for(i = 0; i < n; i++)
	{
		printf("\nProcess[%d]\t\t%d\t\t%d\t\t %d \n", process[i],priority[i], burst_time[i], waiting_time[i]);
	}
    printf("\nAverage Waiting Time:\t%f", avg_waiting_time);
      
    return 0;
}  
