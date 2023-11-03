# EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS

## AIM:
To implement First-Come-First-Serve (FCFS) Scheduling

## ALGORITHM:
Start with a queue (or a list) to represent the ready queue of processes.
Initialize a timer or clock to 0.
Read the number of processes (n) and create a data structure to store process information, including arrival time (AT) and burst time (BT) for each process.
Read the arrival time and burst time for each process and store them in the data structure.
Sort the processes in the ready queue based on their arrival times in ascending order. This step ensures that processes are executed in the order they arrive.
Initialize the waiting time (WT) and turnaround time (TAT) for the first process to 0.
For each process in the ready queue (in the order of arrival): a. Calculate the start time (ST) as the maximum of the current time and the arrival time of the process. b. Calculate the finish time (FT) as the start time plus the burst time of the process. c. Calculate the waiting time (WT) for the process as the start time minus the arrival time. d. Calculate the turnaround time (TAT) for the process as the finish time minus the arrival time. e. Update the current time to the finish time.
Calculate the average waiting time (AWT) and average turnaround time (ATAT) for all processes by summing up the individual waiting times and turnaround times and dividing by the total number of processes.
Display the waiting time, turnaround time, and other relevant information for each process.
Display the average waiting time and average turnaround time for all processes.
End.

## PROGRAM:
```
#include<stdio.h>
int main()
{
int c=0,i,n,bt[10],at[10],wt[10],ft[10];
int st[10],tat[10];
float awt=0,atat=0,rr[10];
printf("Enter the number of process : ");
scanf("%d",&n);
for(i=1;i<=n;i++)
{
printf("Enter the arrival time and burst time for the process %d",i);
scanf("%d %d",&at[i],&bt[i]);


}
for(i=1;i<=n;i++)
{
st[i]=c;
c=c+bt[i];
wt[i]=st[i]-at[i];
ft[i]=st[i]+bt[i];
tat[i]=wt[i]+bt[i];
rr[i]=tat[i]/bt[i];
}
for(i=1;i<=n;i++)
{
awt=awt+wt[i];
atat=atat+tat[i];
}
awt=awt/n;
atat=atat/n;
printf("\n\t\t CPU SCHEDULING\n\t\t ***************");
printf("\n\t\t FIRST COME FIRST SERVE\n\t\t **********************");
printf("\n--------------------------------------------------------------\n");
printf("proc\t at\t bt\t st\t ft\t wt\t tat\t rr\t\n");
printf("--------------------------------------------------------------");
for(i=1;i<=n;i++)
{
printf("\n %d\t %d\t %d\t %d\t %d\t %d\t %d\t%5.2f",i,at[i],bt[i],st[i],ft[i],wt[i],tat[i],rr[i]);
}
printf("\n--------------------------------------------------------------");
printf("\n Average waiting time is %5.2f\n average tat is%5.2f",awt,atat); }
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/121418437/a5c35f1d-1077-45da-b734-32db52064e6f)

## RESULT: 
 First-Come-First-Serve Scheduling is implemented successfully.
# Shortest Job First (SJF) Preemptive Scheduling
## AIM: 
To implement Shortest Job First (SJF) Preemptive Scheduling

## ALGORITHM:
Initialize variables and arrays to store process information, such as process ID (p), arrival time (at), burst time (bt), start time (st), finish time (ft), waiting time (wt), turnaround time (tt), response ratio (rr), and a flag to mark completed processes (iscompleted).

Read the number of processes (n) from the user.

Read the process ID, arrival time, and burst time for each process and store them in respective arrays (p, at, bt).

Initialize variables, such as nextst (next start time) and counters.

Loop until all processes are completed: a. Find the process with the minimum burst time among the processes that have arrived and are not completed. b. Update the start time, finish time, waiting time, and turnaround time for the selected process. c. Calculate the response ratio (rr) for the selected process (rr = turnaround time / burst time). d. Mark the selected process as completed. e. Update the nextst to the finish time of the selected process.

Calculate the average waiting time (AWT) and average turnaround time (ATT) by summing up the individual waiting times and turnaround times and dividing by the total number of processes.

Display the process information, including process ID, arrival time, burst time, start time, finish time, waiting time, turnaround time, and response ratio.

Display the average waiting time and average turnaround time.

## PROGRAM:
```
#include<stdio.h>
int main()
{
int i,n,p[10],st[10],at[10],bt[10],ft[10],wt[10],tt[10];
int nextst,count,minsrt,minpos;
static int  iscompleted[10];
float rr[10],awt=0,att=0;
printf("\n\t SHORTEST JOB FIRST\n\t ******************");
printf("\nEnter the no. of process to be executed :");
scanf("%d",&n);
printf("\nEnter the process,arrival time and burst time\n");
for(i=0;i<n;i++)
{
scanf("%d %d %d",&p[i],&at[i],&bt[i]);
}
nextst=0;
for(count=0;count<n;count++)
{
minsrt=100;
minpos=0;
for(i=0;i<n;i++)
{
if(at[i]<=nextst&&iscompleted[i]==0)
{
if(minsrt>bt[i])
{
minsrt=bt[i];
minpos=i;
}
}
}
i=minpos;
st[i]=nextst;
ft[i]=st[i]+bt[i];
wt[i]=st[i]-at[i];
tt[i]=wt[i]+bt[i];
rr[i]=tt[i]/bt[i];
iscompleted[i]=1;
nextst=ft[i];
}
printf("\n---------------------------------------");
printf("\nPRO AT bT ST FT WT TT RR \n");
printf("---------------------------------------\n");
for(i=0;i<n;i++)
{
printf("%3d %2d %2d",p[i],at[i],bt[i]);
printf(" %3d %2d %2d %2d %4.2f\n",st[i],ft[i],wt[i],tt[i],rr[i]);
}
printf("---------------------------------------");
for(i=0;i<n;i++)
{
awt=awt+wt[i];
att=att+tt[i];
}
awt=awt/n;
att=att/n;
printf("\nAverage waiting time is %5.2f",awt);
printf("\nAverage turn around time is %5.2f",att);
}
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/121418437/bbc6916d-a323-4ec4-aba8-b0d66b4fc7f9)


## RESULT: Shortest Job First (SJF)  scheduling is implemented successfully.

# Round Robin (RR) Scheduling

## AIM:
 To implement Round Robin (RR) Scheduling
## ALGORITHM:
1.Start the process
2.Get the number of elements to be inserted
3.Get the value for burst time for individual processes
4.Get the value for time quantum
5.Make the CPU scheduler go around the ready queue allocating CPU to each process for the time interval specified
6.Make the CPU scheduler pick the first process and set time to interrupt after quantum. And after it's expiry dispatch the process
7.If the process has burst time less than the time quantum then the process is released by the CPU
8.If the process has burst time greater than time quantum then it is interrupted by the OS and the process is put to the tail of ready queue and the schedule selects next process from head of the queue
9.Calculate the total and average waiting time and turnaround time
10.Display the results

## PROGRAM:
```
#include<stdio.h>
int main()
{
int n,i,pro[10],at[10],srt[10],st[10],ft[10],wt[10],tt[10];
static int iscompleted[10],isstarted[10],isentered[10];
int queue[10],f,r,count,tq,j,timer,totalsrt,tempsrt[10];
float rr[10],awt=0,atat=0;
printf("\n\t ROUND ROBIN");
printf("\nEnter the no. of process :");
scanf("%d",&n);

printf("\nEnter the value for Time Quantum:");
scanf("%d",&tq);
printf("\nEnter the process id for n process:\n");
for(i=0;i<n;i++)
{
scanf("%d",&pro[i]);
}
printf("\nEnter the arrival time for n process :\n");
for(i=0;i<n;i++)
{
scanf("%d",&at[i]);
}
printf("\nEnter the Burst time for n process:\n");
for(i=0;i<n;i++)
{
scanf("%d",&srt[i]);
}
totalsrt=0;
for(i=0;i<n;i++)
{
totalsrt=totalsrt+srt[i];
tempsrt[i]=srt[i];
}
f=0;
r=-1;
count=0;
timer=0;
for(i=0;i<n;i++)
{
if(at[i]==0)
{
r=(r+1)%n;
queue[r]=i;
isentered[i]=1;
count=count+1;
}
}
while(timer<totalsrt)
{
j=queue[f];
f=(f+1)%n;
if(isstarted[j]==0)
{
st[j]=timer;
wt[j]=st[j]-at[j];
isstarted[j]=1;
}
if(srt[j]>=tq)

{
timer=timer+tq;
srt[j]=srt[j]-tq;
}
else
{
timer=timer+srt[j];
srt[j]=srt[j]-srt[j];
}
if(srt[j]==0)
{
ft[j]=timer;
wt[j]=wt[j]+(ft[j]-(st[j]+tempsrt[j]));
tt[j]=wt[j]+tempsrt[j];
rr[j]=(float)tt[j]/tempsrt[j];
iscompleted[j]=1;
}
for(i=0;i<n&&count<n;i++)
{
if(at[i]<=timer&&isentered[i]==0)
{
r=(r+1)%n;
queue[r]=i;
isentered[i]=1;
count=count+1;
}
}
if(iscompleted[j]==0)
{
r=(r+1)%n;
queue[r]=j;
}
}
printf("\n\t CPU SCHEDULING\n\t **************");
printf("\n\t ROUND ROBIN\n\t ***********\n");
printf("------------------------------------------- \n");
printf("PRO AT BUT ST FT WT TT RR");
printf("\n------------------------------------------- \n");
for(i=0;i<n;i++)
{
printf("%3d %2d %2d",pro[i],at[i],tempsrt[i]);
printf(" %3d %3d %2d",st[i],ft[i],wt[i]);
printf(" %3d %4.2f\n",tt[i],rr[i]);
}
printf("------------------------------------------ ");

for(i=0;i<n;i++)
{
awt=awt+wt[i];
atat=atat+tt[i];
}
awt=awt/n;
atat=atat/n;
printf("\nAvg waiting time is %5.2f ",awt );
printf("\nAvg turn around time is %5.2f",atat);
}
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/121418437/4aec1b24-fa98-4afc-bf7d-a0f092ac45bc)


## RESULT: 
Round Robin (RR) Scheduling is implemented successfully.

## AIM:
To implement Priority Preemptive Scheduling

## ALGORITHM:
1.Input process information for n processes and initialize variables. 2.Implement priority-based scheduling to determine process execution order. 3.Calculate waiting times and turnaround times for each process. 4.Compute the average waiting time and average turnaround time. 5.Display the results, including process details and averages

## PROGRAM:
```
#include<stdio.h>
int main()
{
int i,n,pid[10],at[10],srt[10],st[10],ft[10],wt[10],tt[10],pri[10];
int timer,totalsrt,tempsrt[10],minsrt,minpos; static int iscompleted[10],isstarted[10];
float rr[10],awt,atat;
printf("\n\t PRIORITY PRE-EMPTIVE\n\t ********************");
printf("\nENTER THE NO.OF PROCESSES TO BE EXECUTED\n");
scanf("%d",&n);
printf("ENTER THE PROCESSES ID,ARRIVAL TIME,BURST TIME AND PRIORITY \n");
for(i=0;i<n;i++)
scanf("%d %d %d %d",&pid[i],&at[i],&srt[i],&pri[i]);

totalsrt=0;
for(i=0;i<n;i++)
{
totalsrt=totalsrt+srt[i];
tempsrt[i]=srt[i];
}
timer=0;
while(timer<totalsrt)
{
minsrt=100;
minpos=0;
for(i=0;i<n;i++)
{
if(at[i]<=timer && iscompleted[i]==0)
{
if(minsrt>pri[i])
{
minsrt=pri[i];
minpos=i;
}
}
}
i=minpos;
if(isstarted[i]==0)
{
st[i]=timer;
wt[i]=st[i]-at[i];
isstarted[i]=1;
}
srt[i]=srt[i]-1;
timer=timer+1;
if(srt[i]==0)
{
ft[i]=timer;
wt[i]=wt[i]+(ft[i]-(st[i]+tempsrt[i]));
tt[i]=wt[i]+tempsrt[i];
rr[i]=tt[i]/tempsrt[i];
iscompleted[i]=1;
}
}
printf("\n\t CPU SCHEDULING ALGORITHM\n\t ************************");
printf("\n\t PRIORITY PRE-EMPTIVE\n\t ********************");
printf("\n--------------------------------------------------");
printf("\nPID AT SRT ST FT WT TT RR PRIORITY\n");
printf("--------------------------------------------------\n");
for(i=0;i<n;i++)
{
printf("%2d %2d %2d ",pid[i],at[i],tempsrt[i]);
printf("%2d %2d %2d %2d %2.2f %3d\n",st[i],ft[i],wt[i],tt[i],rr[i],pri[i]);

}
printf("--------------------------------------------------\n");
for(i=0;i<n;i++)
{
awt=awt+wt[i];
atat=atat+tt[i];
}
atat=atat/n;
awt=awt/n;
printf("The average waiting time is: %5.2f\n",awt);
printf("The average turn around time is: %5.2f",atat);
}
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/121418437/e2d650b8-7c58-44eb-9c9d-3d8fa556058e)


## RESULT: 
Priority preemptive scheduling is implemented successfully.
