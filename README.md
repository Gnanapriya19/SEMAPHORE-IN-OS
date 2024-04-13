PRODUCER CONSUMER PROBLEM USING SEMAPHORE 
AIM:
To write a C program to implement the Producer & consumer Problem (Semaphore)
DESCRIPTION:
Producer-consumer problem, is a common paradigm for cooperating processes. A producer process produces information that is consumed by a consumer process. One solution to the producer-consumer problem uses shared memory. To allow producer and consumer processes to run concurrently, there must be available  a buffer of items that can be filled by the producer and emptied by the consumer. This buffer will reside in a region of memory that is shared by the producer and consumer processes. A producer can produce one item while the consumer is consuming another item. The producer and consumer must be synchronized, so that the consumer does not try to consume an item that has not yet been produced.
ALGORITHM:
Step 1: The Semaphore mutex, full & empty are initialized.
Step 2: In the case of producer process
i)	Produce an item in to temporary variable.
ii)	If there is empty space in the buffer check the mutex value for enter into the critical section.
iii)	If the mutex value is 0, allow the producer to add value in the temporary variable to the buffer.
Step 3: In the case of consumer process
i)	It should wait if the buffer is empty
ii)	If there is any item in the buffer check for mutex value, if the mutex==0, remove item from buffer
iii)	Signal the mutex value and reduce the empty value by 1.
iv)	Consume the item. Step 4: Print the result
PROGRAM :
#define BUFFERSIZE 10
int mutex,n,empty,full=0,item,item1; int buffer[20];
int in=0,out=0,mutex=1; void wait(int s)
{
while(s<0)
{
 }
s--;
} 
printf(“\nCannot add an item\n”); exit(0);
 
void signal(int s)
{
s++;
}
void producer()
{
do
{
wait (empty); wait(mutex);
printf(“\nEnter an item:”); scanf(“%d”,&item); buffer[in]=item;
in=in+1; signal(mutex); signal(full);
}
while(in<n);
}
void consumer()
{
do
{
wait(full); wait(mutex); item1=buffer[out];
printf(“\nConsumed item =%d”,item1); out=out+1;
signal(mutex); signal(empty);
}
while(out<n);
}
void main()
{
printf(“Enter the value of n:”); scanf(“%d “,&n);
empty=n; while(in<n)
producer(); while(in!=out)
consumer();
}
OUTPUT:
$ cc prco.c
$ a.out
Enter the value of n :3 Enter the item:2
Enter the item:5 Enter the item:9 consumed item=2 consumed item=5 consumed item=9
$
RESULT:
Thus the program for solving producer and consumer problem using semaphore was executed successfully.

