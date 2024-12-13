# balaganesh1
1a)Even Natural Number
#include<stdio.h>
void main()
{
int n,sum=0,even,i;
clrscr();
printf("Enter no. of terms: ");
scanf("%d",&n);
printf("First %d even natural numbers are: \n",n);
for(i=1;i<=n;i++)
{
even=2*i;
printf("%d ",even);
sum+=even;
}
printf("\nSum of first %d even natural nums: %d\n",n,sum);
getch();
}


1b)Harmonic Series
#include<stdio.h>
void main()
{
int n,i;
double sum = 0.0;
clrscr();
printf("Enter no. of terms: ");
scanf("%d", &n);
printf("Harmonic series up to %d terms: \n",n);
for(i=1;i<=n;i++)
{
printf("1/%d ",i);
if(i<n)
{
printf("+ ");
}
sum+=1.0/i;
}
printf("\nSum of Harmonic series up to %d terms: %.6f\n",n,sum);
getch();
}


1c)Armstrong Number
#include<stdio.h>
#include<math.h>
void main()
{
int num,originalNum,remainder,result=0,n=0;
clrscr();
printf("Enter an integer: ");
scanf("%d",&num);
originalNum=num;
while(originalNum!=0)
{
originalNum/=10;
++n;
}
originalNum=num;
while(originalNum!=0)
{
remainder=originalNum%10;
result+=pow(remainder,n);
originalNum/=10;
}
if(result==num)
printf("%d is Armstrong Num\n",num);
else
printf("%d is not Armstrong Num\n",num);
getch();
}


1d)Factorial
#include<stdio.h>
void main()
{
int n,i,fact=1;
clrscr();
printf("Enter a num: ");
scanf("%d",&n);
if(n<0)
printf("Factorial of negative num doesn't exist.\n");
else
{
for(i=1;i<=n;i++)
fact*=i;
printf("Factorial of %d is: %d\n",n,fact);
}
getch();
}


2a)Matrix Multiplication
#include<stdio.h>
void main()
#define SIZE 2
{
int a[SIZE][SIZE];
int b[SIZE][SIZE];
int c[SIZE][SIZE];
int i,j,k;
clrscr();
printf("Enter elements of matrix A(%dx%d):\n",SIZE,SIZE);
for(i=0;i<SIZE;i++)
{
for(j=0;j<SIZE;j++)
{
scanf("%d",&a[i][j]);
}
}
printf("Enter elements of matrix B(%dx%d):\n",SIZE,SIZE);
for(i=0;i<SIZE;i++)
{
for(j=0;j<SIZE;j++)
{
scanf("%d",&b[i][j]);
}
}
for(i=0;i<SIZE;i++)
for(j=0;j<SIZE;j++)
{
c[i][j]=0;
for(k=0;k<SIZE;k++)
c[i][j]+=a[i][k]*b[k][j];
}
printf("Result Matrix:\n");
for(i=0;i<SIZE;i++)
{
for(j=0;j<SIZE;j++)
printf("%d ",c[i][j]);
printf("\n");
}
getch();
}


2b)Transpose matrix
#include<stdio.h>
void main()
{
int i,j,rows,cols,matrix[10][10],transpose[10][10];
clrscr();
printf("Enter rows and columns: \n");
scanf("%d%d",&rows,&cols);
printf("Enter matrix elements:\n");
for(i=0;i<rows;i++)
for(j=0;j<cols;j++)
scanf("%d",&matrix[i][j]);
for(i=0;i<rows;i++)
for(j=0;j<cols;j++)
transpose[j][i] = matrix[i][j];
printf("Transpose:\n");
for(i=0;i<cols;i++)
{
for(j=0;j<rows;j++)
{
printf("%d ",transpose[i][j]);
}
printf("\n");
}
getch();
}


3a)Prime number
#include<stdio.h>
int isPrime(int n)
{
int i;
if(n<=1) return 0;
for(i=2;i*i<=n;i++)
{
if(n%i==0) return 0;
}
return 1;
}
void main()
{
int n;
clrscr();
printf("Enter a number: ");
scanf("%d",&n);
if(isPrime(n))
printf("%d is prime\n",n);
else
printf("%d is not prime\n",n);
getch();
}


3b)Fibonacci Number
#include<stdio.h>
int fibonacci(int n)
{
if(n<=1) return n;
return fibonacci(n-1)+fibonacci(n-2);
}
void main()
{
int n;
clrscr();
printf("Enter the value of n: ");
scanf("%d",&n);
if(n<0)
{
printf("Fibonacci is undefined for negative numbers\n");
}
else
{
printf("Fibonacci number at position %d is %d\n",n,fibonacci(n));
}
getch();
}

3c)Add 2 nums using call by reference
#include<stdio.h>
void addNumbers(int *a,int *b,int *result)
{
*result = *a + *b;
}
void main()
{
int num1,num2,sum;
clrscr();
printf("Enter first num: \n");
scanf("%d",&num1);
printf("Enter second num:\n");
scanf("%d",&num2);
addNumbers(&num1,&num2,&sum);
printf("Sum of %d and %d is %d.\n",num1,num2,sum);
getch();
}


4a)Append lines at end of txt file
#include<stdio.h>
#include<conio.h>
void main()
{
FILE *p;
int i,n;
char str[100];
char fname[20];
char str1;
clrscr();
printf("Input the file name to be opened: ");
scanf("%s",fname);
p = fopen(fname,"a");
printf("Input the number of lines to be written: ");
scanf("%d",&n);
printf("The lines are: \n");
for(i=0;i<(n+1);i++)
{
fgets(str,sizeof(str),stdin);
fputs(str,p);
}
fclose(p);
p = fopen(fname,"r");
printf("\nThe content of the file is:\n",fname);
str1 = fgetc(p);
while(str1!=EOF)
{
printf("%c",str1);
str1 = fgetc(p);
}
fclose(p);
getch();
}


4b)Copy a file
#include<stdio.h>
#include<stdlib.h>
void main()
{
FILE *sf,*tf;
char sp[100],tp[100],c;
clrscr();
printf("Enter source path: \n");
scanf("%s",sp);
printf("Enter target path: \n");
scanf("%s",tp);
if((sf=fopen(sp,"r"))==NULL)
{
printf("Error: Cannot open source file\n");
exit(EXIT_FAILURE);
}
if((tf=fopen(tp,"w"))==NULL)
{
fclose(sf);
printf("Error: Cannot open target file\n");
exit(EXIT_FAILURE);
}
while((c=fgetc(sf))!=EOF)
fputc(c,tf);
printf("File Copied Successfully\n");
fclose(sf);
fclose(tf);
getch();
}


5a)Factorial
//Recursive
#include<stdio.h>
int fact(int n)
{
return n<=1 ? 1:n*fact(n-1);
}
void main()
{
int n;
clrscr();
printf("Enter num: ");
scanf("%d",&n);
printf("Factorial of %d is %d\n",n,fact(n));
getch();
}
//Non-recursive
#include<stdio.h>
int fact(int n)
{
int f=1;
while(n>1)
f*=n--;
return f;
}
void main()
{
int n;
clrscr();
printf("Enter a num: ");
scanf("%d",&n);
printf("Factorial of %d is %d\n",n,fact(n));
getch();
}


5b)GCD
//recursive
#include<stdio.h>
int gcd(int a,int b)
{
return b==0 ? a:gcd(b,a%b);
}
void main()
{
int n,m;
clrscr();
printf("Enter values\n");
scanf("%d%d",&n,&m);
printf("GCD is %d\n",gcd(n,m));
getch();
}
//non-recursive
#include<stdio.h>
int gcd(int a,int b)
{
while(b)
{
int temp=b;
b=a%b;
a=temp;
}
return a;
}
void main()
{
int n,m;
clrscr();
printf("Enter values\n");
scanf("%d%d",&n,&m);
printf("GCD is %d\n",gcd(n,m));
getch();
}


5c)Towers of Hanoi
//recursive
#include<stdio.h>
void hanoi(int n,char S,char D,char I)
{
if(n==1)
{
printf("Move disk 1 from %c to %c\n",S,D);
return;
}
hanoi(n-1,S,I,D);
printf("Move disk %d from %c to %c\n",n,S,D);
hanoi(n-1,I,D,S);
}
void main()
{
int n;
clrscr();
printf("Enter no. of disks: ");
scanf("%d",&n);
printf("S-Source\nI-Intermediary\nD-Destination\n");
hanoi(n,'S','D','I');
getch();
}
//non-recursive
#include<stdio.h>
int z(int n)
{
int c=0;
while((n&1)==0)
{
c++;
n>>=1;
}
return c;
}
void h(int n,char s,char d,char i)
{
int k,m=(1<<n)-1;
for(k=1;k<=m;k++)
{
int f=(k&k-1)%3, t=(3-f-(k%3))%3, d=z(k)+1;
printf("Move disk %d from %c to %c\n",d,"SDI"[f],"SDI"[t]);
}
}
void main()
{
int n;
clrscr();
printf("Enter no. of disks: ");
scanf("%d",&n);
printf("S-Source\nI-Intermediary\nD-Destination\n");
h(n,'S','D','I');
getch();
}


6a)Linear search
#include<stdio.h>
int linearSearchNonRecursive(int arr[],int n,int key)
{
int i;
for(i=0;i<n;i++)
if(arr[i]==key)
return i;
return -1;
}
int linearSearchRecursive(int arr[],int n,int key)
{
return n==0 ? -1:(arr[n-1]==key ? n-1:linearSearchRecursive(arr,n-1,key));
}
void main()
{
int i,n,key,res1,res2;
int arr[30];
clrscr();
printf("Enter number of elements: ");
scanf("%d",&n);
printf("Enter %d elements: \n",n);
for(i=0;i<n;i++)
scanf("%d",&arr[i]);
printf("Enter key to search: ");
scanf("%d",&key);
res1=linearSearchNonRecursive(arr,n,key);
res2=linearSearchRecursive(arr,n,key);
printf("Non-Recursive : %s\n",res1!=-1?"Key found":"Key not found");
printf("Recursive : %s\n",res2!=-1?"Key found":"Key not found");
getch();
}


6b)Binary search
#include<stdio.h>
int binarySearchRecursive(int arr[],int low,int high,int key)
{
if(low<=high)
{
int mid=low+(high-low)/2;
if(arr[mid]==key) return mid;
return (arr[mid]<key)?binarySearchRecursive(arr,mid+1,high,key):binarySearchRecursive(arr,low,mid-1,key);
}
return -1;
}
int binarySearchIterative(int arr[],int n,int key)
{
int low=0,high=n-1,mid;
while(low<=high)
{
mid=low+(high-low)/2;
if(arr[mid]==key) return mid;
(arr[mid]<key)?(low=mid+1):(high=mid-1);
}
return -1;
}
void main()
{
int n,key,result,i,arr[30];
clrscr();
printf("Number of elements: ");
scanf("%d",&n);
printf("Enter %d elements: \n",n);
for(i=0;i<n;i++)
scanf("%d",&arr[i]);
printf("Key: ");
scanf("%d",&key);
result=binarySearchIterative(arr,n,key);
printf("Non-recursive : %s\n",result!=-1?"Key found":"Key not found");
result=binarySearchRecursive(arr,0,n-1,key);
printf("Recursive : %s\n",result!=-1?"Key found":"Key not found");
getch();
}


7a)Stack using array
#include <stdio.h>
#define MAX 3
typedef struct {
int items[3];
int top;
} Stack;
void initStack(Stack* s) {
s->top = -1;
}
int isFull(Stack* s) {
return s->top == MAX - 1;
}

int isEmpty(Stack* s) {
return s->top == -1;
}
void push(Stack* s, int value) {
if (isFull(s))
printf("Stack Overflow! Cannot push %d\n", value);
else
s->items[++s->top] = value;
}
int pop(Stack* s) {
return isEmpty(s) ? (printf("Stack Underflow!\n"), -1) : s->items[s->top--];
}
int peek(Stack* s) {
return isEmpty(s) ? (printf("Stack is empty\n"), -1) : s->items[s->top];
}
void display(Stack* s) {
int i;
if (isEmpty(s))
printf("Stack is empty\n");
else
for (i = s->top; i >= 0; i--)
printf("%d\n", s->items[i]);
}
void main() {
int choice, value;
Stack s;
clrscr();
initStack(&s);
do {
printf("\n1. Push\n2. Pop\n3. Peek\n4. Display\n5. Exit\nChoice: ");
scanf("%d", &choice);
switch (choice) {
case 1: printf("Enter value to push: ");
		scanf("%d", &value);
		push(&s, value);
		break;
case 2: value = pop(&s);
		if (value != -1)
		printf("Popped value: %d\n", value);
		break;
case 3: value = peek(&s);
		if (value != -1)
		printf("Top element: %d\n", value);
		break;
case 4: printf("Stack elements:\n");
		display(&s);
		break;
case 5: printf("Exiting...\n");
		break;
default:printf("Invalid choice! Please enter a valid option.\n");
}
} while (choice != 5);
}


7b)stack using linked list
#include <stdio.h>
#include <stdlib.h>
struct Node {
int data;
struct Node* next;
} *top = NULL;
void push(int value) {
struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
if (!newNode) return;
newNode->data = value;
newNode->next = top;
top = newNode;
}
void pop() {
struct Node* temp = top;
if (!top) {
printf("Stack Underflow\n");
return;
}
printf("Popped %d\n", temp->data);
top = top->next;
free(temp);
}
void peek() {
if (top) printf("Top element is %d\n", top->data);
else printf("Stack is empty\n");
}
void display() {
struct Node* temp = top;
while (temp) {
printf("%d ", temp->data);
temp = temp->next;
}
printf("\n");
}
void main() {
int choice, value;
clrscr();
while (1) {
printf("\n1. Push\n2. Pop\n3. Peek\n4. Display\n5. Exit\nChoose: ");
scanf("%d", &choice);
switch (choice) {
case 1: printf("Enter value: "); scanf("%d", &value); push(value); break;
case 2: pop(); break;
case 3: peek(); break;
case 4: display(); break;
case 5: exit(0);
default: printf("Invalid choice.\n");
}
}
}


8a)Infix to postfix
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#define MAX 30
typedef struct { int top; char items[30]; } Stack;
void initStack(Stack *s) { s->top = -1; }
int isEmpty(Stack *s) { return s->top == -1; }
void push(Stack *s, char item) { s->items[++s->top] = item; }
char pop(Stack *s) { return s->items[s->top--]; }
char peek(Stack *s) { return s->items[s->top]; }
int precedence(char op) { return (op == '+' || op == '-') ? 1 : (op == '*' || op == '/') ? 2 : (op == '^') ? 3 : 0; }
void infixToPostfix(char* infix, char* postfix) {
int i = 0, j = 0;
Stack s;
initStack(&s);
    while (infix[i]) {
        char ch = infix[i++];
        if (isalnum(ch)) postfix[j++] = ch;
        else if (ch == '(') push(&s, ch);
        else if (ch == ')') { while (!isEmpty(&s) && peek(&s) != '(') postfix[j++] = pop(&s); pop(&s); }
        else { while (!isEmpty(&s) && precedence(peek(&s)) >= precedence(ch)) postfix[j++] = pop(&s); push(&s, ch); }
    }
    while (!isEmpty(&s)) postfix[j++] = pop(&s);
    postfix[j] = '\0';
}
void main() {
    char infix[MAX], postfix[MAX];
    clrscr();
    printf("Enter infix expression: ");
    scanf("%s", infix);
    infixToPostfix(infix, postfix);
    printf("Postfix: %s\n", postfix);
    getch();
}


8b)Queue using array
#include <stdio.h>
#include <stdlib.h>
#define MAX 3
struct Queue {
    int arr[3];
    int front, rear;
};
void initQueue(struct Queue* q) {
    q->front = q->rear = -1;
}
int isFull(struct Queue* q) {
    return q->rear == MAX - 1;
}
int isEmpty(struct Queue* q) {
    return q->front == -1;
}
void enqueue(struct Queue* q, int value) {
    if (isFull(q)) {
	printf("Queue is full!\n");
    } else {
	if (q->front == -1) q->front = 0;
	q->arr[++q->rear] = value;
	printf("%d enqueued.\n", value);
    }
}
int dequeue(struct Queue* q) {
    if (isEmpty(q)) {
	printf("Queue is empty!\n");
	return -1;
    } else {
	int value = q->arr[q->front];
	if (q->front == q->rear) {
	    q->front = q->rear = -1;
	} else {
	    q->front++;
	}
	return value;
    }
}
void display(struct Queue* q) {
	int i;
    if (isEmpty(q)) {
	printf("Queue is empty.\n");
    } else {
	printf("Queue: ");
	for ( i = q->front; i <= q->rear; i++) {
	    printf("%d ", q->arr[i]);
	}
	printf("\n");
    }
}
void main() {
struct Queue q;
int choice, value;
clrscr();
initQueue(&q);
    do {
	printf("\n1. Enqueue\n2. Dequeue\n3. Display\n4. Exit\nChoice: ");
	scanf("%d", &choice);
	switch (choice) {
	case 1:
	    printf("Enter value to enqueue: ");
	    scanf("%d", &value);
	    enqueue(&q, value);
	    break;
	case 2:
	    value = dequeue(&q);
	    if (value != -1) {
		printf("Dequeued: %d\n", value);
	    }
	    break;
	case 3:
	    display(&q);
	    break;
	case 4:
	    printf("Exiting...\n");
	    break;
	default:
	    printf("Invalid choice. Try again.\n");
	}
    } while (choice != 4);
}


8c)Queue using linked list
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node* next;
};
struct Queue {
    struct Node *front, *rear;
};
void initQueue(struct Queue* q) { q->front = q->rear = NULL; }
int isEmpty(struct Queue* q) { return !q->front; }
void enqueue(struct Queue* q, int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value; newNode->next = NULL;
    if (isEmpty(q)) q->front = q->rear = newNode;
    else { q->rear->next = newNode; q->rear = newNode; }
}
int dequeue(struct Queue* q) {
struct Node* temp;
int value;
    if (isEmpty(q)) return -1;
    temp = q->front;
    value = temp->data; q->front = q->front->next;
    if (!q->front) q->rear = NULL;
    free(temp);
    return value;
}
int peek(struct Queue* q) { return isEmpty(q) ? -1 : q->front->data; }
void display(struct Queue* q) {
    struct Node* temp;
    for (temp = q->front; temp; temp = temp->next) 
        printf("%d ", temp->data);
    printf("\n");
}
void main() {
    struct Queue q;
    int choice, value;
    clrscr();
    initQueue(&q);
    do {
	printf("\n1. Enqueue\n2. Dequeue\n3. Peek \n4. Display \n5. Exit\nChoice:");
	scanf("%d", &choice);
	switch (choice) {
	    case 1: printf("Enter value to enqueue: "); scanf("%d", &value); enqueue(&q, value); break;
	    case 2: value = dequeue(&q); if (value == -1) printf("Queue is empty.\n"); else printf("Dequeued: %d\n", value); break;
	    case 3: value = peek(&q); if (value == -1) printf("Queue is empty.\n"); else printf("Front : %d\n", value); break;
	    case 4: display(&q); break;
	    case 5: printf("Exiting program.\n"); break;
	    default: printf("Invalid choice. Try again.\n");
	}
    } while (choice != 5);
}


9)Singly linked list
#include <stdio.h>
#include <stdlib.h>
struct node {
    int data;
    struct node *next;
} *head = NULL;
void insert(int pos, int val) {
	int i;
    struct node *new_node = (struct node *)malloc(sizeof(struct node)), *temp = head;
    new_node->data = val;
    if (pos == 1 || !head) {
        new_node->next = head;
        head = new_node;
    } else {
        for ( i = 1; i < pos - 1 && temp->next; i++) temp = temp->next;
        new_node->next = temp->next;
        temp->next = new_node;
    }
    printf("%d inserted at position %d\n", val, pos);
}
void delet(int pos) {
int i;
struct node *temp = head, *prev = NULL;
    if (!head) { printf("List is empty\n"); return; }
    if (pos == 1) { head = head->next; }
    else {
        for ( i = 1; i < pos && temp; i++) { prev = temp; temp = temp->next; }
        if (!temp) { printf("Position out of bounds\n"); return; }
        prev->next = temp->next;
    }
    printf("%d deleted from position %d\n", temp->data, pos);
    free(temp);
}
int display() { int i=0;
    struct node *temp = head;
    printf("START -> ");
    while (temp) { printf("%d -> ", temp->data); temp = temp->next; i++;}
    printf("NULL\n"); printf("Length=%d\n",i);
}
void search(int val) {
    struct node *temp = head;
    int pos = 1;
    while (temp) {
        if (temp->data == val) {
            printf("Value %d found at position %d\n", val, pos);
            return;
        }
        temp = temp->next;
        pos++;
    }
    printf("Value %d not found\n", val);
}
void main() {
    int choice, value, pos;
    clrscr();
    while (1) {
printf("\n1. Insert\n2. Delete\n3. Display\n4. Search\n5. Exit\nChoose: ");
	scanf("%d", &choice);
	if (choice == 5) break;
	switch (choice) {
	    case 1: printf("Enter position and value: \n"); scanf("%d %d", &pos, &value); insert(pos, value); break;
	    case 2: printf("Enter position: "); scanf("%d", &pos); delet(pos); break;
	    case 3: display(); break;
	    case 4: printf("Enter value to search: "); scanf("%d", &value); search(value); break;
	    default: printf("Invalid choice\n");
	}
    }
}


10)Polynomial addition
#include<stdio.h>
#include<conio.h>
typedef struct Node{int coeff, exp;
struct Node* next;
}Node;
Node* insert(Node* h,int c,int e){
Node* n = (Node*)malloc(sizeof(Node)), *t=h;
n->coeff=c;
n->exp=e;
n->next=NULL;
if(!h||e > h->exp)
{
n->next=h;
return n;
}
while(t->next && t->next->exp >= e)
t=t->next;
n->next=t->next;
t->next=n;
return h;
}
Node* addPoly(Node* p1,Node* p2)
{
Node* r = NULL;
while(p1||p2)
{
int c=0,e;
if(p1 && (!p2 || p1->exp > p2->exp))
c=p1->coeff,e=p1->exp,p1=p1->next;
else if(p2&&(!p1||p2->exp > p1->exp))
c=p2->coeff,e=p2->exp,p2=p2->next;
else
c=p1->coeff+p2->coeff,e=p1->exp,p1=p1->next,p2=p2->next;
if(c)
r=insert(r,c,e);
}
return r;
}
void printPoly(Node* h)
{
while(h)
{
printf(h->next?"%dx^%d + ":"%dx^%d",h->coeff,h->exp);
h=h->next;
}
printf("\n");
}
void main()
{
Node *p1=NULL, *p2=NULL;
clrscr();
p1=insert(p1,5,3);
p1=insert(p1,3,2);
p1=insert(p1,6,0);
p2=insert(p2,6,2);
p2=insert(p2,2,1);
printf("P1: ");
printPoly(p1);
printf("P2: ");
printPoly(p2);
printf("P1+P2: ");
printPoly(addPoly(p1,p2));
getch();
}


11a)Binary tree - recursive
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node *left, *right;
};
struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = newNode->right = NULL;
    return newNode;
}
void preorderTraversal(struct Node* root) {
    if (!root) return;
    printf("%d ", root->data);
    preorderTraversal(root->left);
    preorderTraversal(root->right);
}
void inorderTraversal(struct Node* root) {
    if (!root) return;
    inorderTraversal(root->left);
    printf("%d ", root->data);
    inorderTraversal(root->right);
}
void postorderTraversal(struct Node* root) {
    if (!root) return;
    postorderTraversal(root->left);
    postorderTraversal(root->right);
    printf("%d ", root->data);
}
void main() {
    struct Node* root = createNode(1);
    clrscr();
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);
    printf("Preorder Traversal: ");
    preorderTraversal(root);
    printf("\nInorder Traversal: ");
    inorderTraversal(root);
    printf("\nPostorder Traversal: ");
    postorderTraversal(root);
    printf("\n");
    getch();
}


11b)Binary tree - non-recursive
#include <stdio.h>
#include <stdlib.h>
struct Node { int data; struct Node* left; struct Node* right; };
struct Stack { struct Node* node; struct Stack* next; };
struct Node* createNode(int data) { 
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node)); 
    newNode->data = data; 
    newNode->left = newNode->right = NULL; 
    return newNode; }
void push(struct Stack** top, struct Node* node) {
    struct Stack* newStackNode = (struct Stack*)malloc(sizeof(struct Stack));
    newStackNode->node = node; newStackNode->next = *top; *top = newStackNode; }
struct Node* pop(struct Stack** top) {
    struct Stack* temp;
    struct Node* node;
    if (*top == NULL) return NULL;
    temp = *top; node = temp->node;
    *top = (*top)->next; free(temp); return node; }
void preorder(struct Node* root) {
    struct Stack* stack;
    if (!root) return;
    stack = NULL;
    push(&stack, root);
    while (stack) {
        struct Node* curr = pop(&stack);
        printf("%d ", curr->data);
        if (curr->right) push(&stack, curr->right);
        if (curr->left) push(&stack, curr->left); }}
void inorder(struct Node* root) {
    struct Stack* stack = NULL; struct Node* curr = root;
    while (curr || stack) {
        while (curr) { push(&stack, curr); curr = curr->left; }
        curr = pop(&stack);
        printf("%d ", curr->data); curr = curr->right; }}
void postorder(struct Node* root) {
    struct Stack *stack1,*stack2;
    if (!root) return;
    stack1 = NULL; stack2 = NULL;
    push(&stack1, root);
    while (stack1) {
        struct Node* curr = pop(&stack1);
        push(&stack2, curr);
        if (curr->left) push(&stack1, curr->left);
        if (curr->right) push(&stack1, curr->right);
    }
    while (stack2) printf("%d ", pop(&stack2)->data); }
void main()
{
    struct Node* root = createNode(1);
    clrscr();
    root->left = createNode(2); root->right = createNode(3);
    root->left->left = createNode(4); root->left->right = createNode(5);
    root->right->left = createNode(6); root->right->right = createNode(7);
    printf("Preorder: "); preorder(root);
    printf("\nInorder: "); inorder(root);
    printf("\nPostorder: "); postorder(root);
    getch();
}


12a)Prim's algorithm
#include <stdio.h>
#include <limits.h>
#define V 5
int minKey(int key[], int mstSet[]) {
    int v, min = INT_MAX, min_index;
    for (v = 0; v < V; v++) {
        if (mstSet[v] == 0 && key[v] < min) {
            min = key[v];
            min_index = v;
        }
    }
    return min_index;
}
void printMST(int parent[], int graph[V][V]) { int i;
    for ( i = 1; i < V; i++) {
        printf("%d - %d \t%d\n", parent[i], i, graph[i][parent[i]]);
    }
}
void primMST(int graph[V][V]) {
    int i, v, count, parent[V], key[V], mstSet[V];
    for ( i = 0; i < V; i++) {
        key[i] = INT_MAX;
        mstSet[i] = 0;
    }
    key[0] = 0;
    parent[0] = -1;
    for ( count = 0; count < V - 1; count++) {
        int u = minKey(key, mstSet);
        mstSet[u] = 1;
        for ( v = 0; v < V; v++) {
            if (graph[u][v] && mstSet[v] == 0 && graph[u][v] < key[v]) {
                parent[v] = u;
                key[v] = graph[u][v];
            }
        }
    }
    printf("\nMST:\n");
    printMST(parent, graph);
}
void main() {
    int i, j, graph[V][V];
    clrscr();
    printf("Enter the adjacency matrix of the graph (%dx%d):\n", V, V);
    for ( i = 0; i < V; i++) {
	for ( j = 0; j < V; j++) {
	    scanf("%d", &graph[i][j]);
	}
    }
    primMST(graph);
    getch();
}


12b)Kruskal's algorithm
#include <stdio.h>
#include <stdlib.h>
struct Edge { int src, dest, weight; };
struct Subset { int parent, rank; };
int compare(const void *a, const void *b) {
    return ((struct Edge*)a)->weight - ((struct Edge*)b)->weight;
}
int find(struct Subset subsets[], int i) {
    if (subsets[i].parent != i) subsets[i].parent = find(subsets, subsets[i].parent);
    return subsets[i].parent;
}
void unionSets(struct Subset subsets[], int x, int y) {
    int xroot = find(subsets, x), yroot = find(subsets, y);
    if (subsets[xroot].rank < subsets[yroot].rank) subsets[xroot].parent = yroot;
    else if (subsets[xroot].rank > subsets[yroot].rank) subsets[yroot].parent = xroot;
    else { subsets[yroot].parent = xroot; subsets[xroot].rank++; }
}
void kruskal(struct Edge edges[], int V, int E) {
    struct Edge result[25];
    int v, e = 0, i = 0, j, minimumCost = 0;
    struct Subset subsets[25];
    for ( v = 0; v < V; v++) { subsets[v].parent = v; subsets[v].rank = 0; }
    qsort(edges, E, sizeof(edges[0]), compare);
    printf("Edges sorted by weight:\n");
    for ( j = 0; j < E; j++) {
	printf("%d -- %d == %d\n", edges[j].src, edges[j].dest, edges[j].weight);
    }
    while (e < V - 1 && i < E) {
	struct Edge nextEdge = edges[i++];
	int x = find(subsets, nextEdge.src), y = find(subsets, nextEdge.dest);
	if (x != y) { result[e++] = nextEdge; unionSets(subsets, x, y); }
    }
    if (e < V - 1) {
	printf("Graph is disconnected. No MST exists.\n");
	return;
    }
    for (i = 0; i < e; i++) {
	printf("%d -- %d == %d\n", result[i].src, result[i].dest, result[i].weight);
	minimumCost += result[i].weight;
    }
    printf("Minimum cost of the spanning tree: %d\n", minimumCost);
}
void main() {
    int i, V, E;
    struct Edge edges[25];
    clrscr();
    printf("Enter the number of vertices and edges: ");
    scanf("%d %d", &V, &E);
    printf("Enter the edges in the format: src dest weight\n");
    for ( i = 0; i < E; i++) scanf("%d %d %d", &edges[i].src, &edges[i].dest, &edges[i].weight);
    kruskal(edges, V, E);
    getch();
}


13)Hash table
#include <stdio.h>
#include <stdlib.h>
#define TABLE_SIZE 11
#define EMPTY -1
#define DELETED -2
typedef struct { int key, value; } HashItem;
HashItem* table[TABLE_SIZE] = {NULL};
int h1(int key) { return key % TABLE_SIZE; }
int h2(int key) { return 1 + (key % (TABLE_SIZE - 1)); }
void insert(int key, int value) {int i, idx;
for ( i = 0, idx = h1(key); ; idx = (h1(key) + ++i * h2(key)) % TABLE_SIZE) {
if (!table[idx] || table[idx]->key == EMPTY || table[idx]->key == DELETED) {
if (!table[idx]) table[idx] = malloc(sizeof(HashItem));
table[idx]->key = key, table[idx]->value = value;
return;
}}}
int search(int key) {
int i, idx;
for ( i = 0, idx = h1(key); table[idx]; idx = (h1(key) + ++i * h2(key)) % TABLE_SIZE)
if (table[idx]->key == key) return table[idx]->value;
return -1;
}
void delete(int key) {
int i, idx;
for ( i = 0, idx = h1(key); table[idx]; idx = (h1(key) + ++i * h2(key)) % TABLE_SIZE)
if (table[idx]->key == key) { table[idx]->key = DELETED; return; }
}
void display() {
int i;
for ( i = 0; i < TABLE_SIZE; i++) {
if (!table[i])
printf("[%d]: EMPTY\n", i);
else if (table[i]->key == DELETED)
printf("[%d]: DELETED\n", i);
else
printf("[%d]: Key=%d, Value=%d\n", i, table[i]->key, table[i]->value);
}
}
void main()
{
clrscr();
insert(12, 120), insert(26, 260), insert(31, 310), insert(17, 170), insert(90, 900);
display(), printf("Search key 31: %d\n", search(31));
delete(31), display();
getch();
}


14)Binary search tree
#include <stdio.h>
#include <stdlib.h>
struct Node {
int value;
struct Node *left, *right;
};
struct Node* newNode(int value) {
struct Node* n = (struct Node*)malloc(sizeof(struct Node));
n->value = value;
n->left = n->right = NULL;
return n;
}
struct Node* insert(struct Node* root, int value) {
if (!root) return newNode(value);
if (value < root->value) root->left = insert(root->left, value);
else if (value > root->value) root->right = insert(root->right, value);
return root;
}
struct Node* minNode(struct Node* root) {
while (root && root->left) root = root->left;
return root;
}
struct Node* deleteNode(struct Node* root, int value) {
struct Node* temp;
if (!root) return root;
if (value < root->value) root->left = deleteNode(root->left, value);
else if (value > root->value) root->right = deleteNode(root->right, value);
else {
if (!root->left) { struct Node* temp = root->right; free(root); return temp; }
else if (!root->right) { struct Node* temp = root->left; free(root); return temp; }
temp = minNode(root->right);
root->value = temp->value;
root->right = deleteNode(root->right, temp->value);
}
return root;
}
void inorder(struct Node* root) {
if (root) { inorder(root->left); printf("%d ", root->value); inorder(root->right); }
}
void main() {
struct Node* root = NULL;
clrscr();
root = insert(root, 50); root = insert(root, 30); root = insert(root, 20);
root = insert(root, 40); root = insert(root, 70); root = insert(root, 60); root = insert(root, 80);
inorder(root); printf("\n");
root = deleteNode(root, 20); inorder(root); printf("\n");
root = deleteNode(root, 30); inorder(root); printf("\n");
getch();
}


15)AVL tree
#include <stdio.h>
#include <stdlib.h>
struct Node { int key, height; struct Node *left, *right; };
int height(struct Node* N) { return N ? N->height : 0; }
int maxi(int a,int b) { return a > b ? a : b; }
struct Node* newNode(int key) {
struct Node* n = malloc(sizeof(struct Node));
n->key = key; n->left = n->right = NULL; n->height = 1;
return n;
}
struct Node* rightRotate(struct Node* y) {
struct Node* x = y->left, *T2 = x->right;
x->right = y; y->left = T2;
y->height = maxi(height(y->left), height(y->right)) + 1;
x->height = maxi(height(x->left), height(x->right)) + 1;
return x;
}
struct Node* leftRotate(struct Node* x) {
struct Node* y = x->right, *T2 = y->left;
y->left = x; x->right = T2;
x->height = maxi(height(x->left), height(x->right)) + 1;
y->height = maxi(height(y->left), height(y->right)) + 1;
return y;
}
int getBalance(struct Node* N) {
return N ? height(N->left) - height(N->right) : 0; }
struct Node* insert(struct Node* node, int key) { int balance;
if (!node) return newNode(key);
if (key < node->key) node->left = insert(node->left, key);
else if (key > node->key) node->right = insert(node->right, key);
else return node;
node->height = 1 + maxi(height(node->left), height(node->right));
balance = getBalance(node);
if (balance > 1 && key < node->left->key) return rightRotate(node);
if (balance < -1 && key > node->right->key) return leftRotate(node);
if (balance > 1 && key > node->left->key) { node->left = leftRotate(node->left); return rightRotate(node); }
if (balance < -1 && key < node->right->key) { node->right = rightRotate(node->right); return leftRotate(node); }
return node;
}
struct Node* minValueNode(struct Node* node) { while (node->left) node = node->left; return node; }
struct Node* deleteNode(struct Node* root, int key) { int balance;
if (!root) return root;
if (key < root->key) root->left = deleteNode(root->left, key);
else if (key > root->key) root->right = deleteNode(root->right, key);
else {
if (!root->left || !root->right) {
struct Node* temp = root->left ? root->left : root->right;
if (!temp) { temp = root; root = NULL; } else *root = *temp;
free(temp);
}
else {
struct Node* temp = minValueNode(root->right);
root->key = temp->key;
root->right = deleteNode(root->right, temp->key);
}
}
if (!root) return root;
root->height = 1 + maxi(height(root->left), height(root->right));
balance = getBalance(root);
if (balance > 1 && getBalance(root->left) >= 0) return rightRotate(root);
if (balance > 1 && getBalance(root->left) < 0) { root->left = leftRotate(root->left); return rightRotate(root); }
if (balance < -1 && getBalance(root->right) <= 0) return leftRotate(root);
if (balance < -1 && getBalance(root->right) > 0) { root->right = rightRotate(root->right); return leftRotate(root); }
return root;
}
void preOrder(struct Node* root) {
if (root) { printf("%d ", root->key); preOrder(root->left); preOrder(root->right); }
}
void main() {
struct Node* root = NULL;
clrscr();
root = insert(root, 10); root = insert(root, 20); root = insert(root, 30); root = insert(root, 15);
preOrder(root); printf("\n");
root = deleteNode(root, 20); preOrder(root); printf("\n");
getch();
}


16a)Bubble sort
#include <stdio.h>
void bubbleSort(int arr[], int n){
int i,j;
for( i=0;i<n-1;i++){
for( j=0;j<n-1-i;j++){
if(arr[j]>arr[j+1]){
int temp=arr[j];
arr[j]=arr[j+1];
arr[j+1]=temp;
}}
}}
void main()
{
int i,n,arr[26];
clrscr();
printf("Enter the number of elements: ");
scanf("%d",&n);
printf("Enter the elements:\n");
for( i=0;i<n;i++){
scanf("%d",&arr[i]);}
bubbleSort(arr,n);
printf("Sorted list in ascending order:\n");
for( i=0;i<n;i++){
printf("%d ",arr[i]);}
printf("\n");
getch();
}


16b)Quick sort
#include <stdio.h>
int partition(int arr[], int low, int high) {
int pivot = arr[high], i = low - 1, j, temp;
for ( j = low; j < high; j++) {
if (arr[j] < pivot) {
i++;
temp = arr[i]; arr[i] = arr[j]; arr[j] = temp; }}
temp = arr[i + 1]; arr[i + 1] = arr[high]; arr[high] = temp;
return i + 1; }
void quickSort(int arr[], int low, int high) {
if (low < high) {
int pi = partition(arr, low, high);
quickSort(arr, low, pi - 1);
quickSort(arr, pi + 1, high); }}
void main()
{
int i,n,arr[26];
clrscr();
printf("Enter the number of elements: ");
scanf("%d", &n);
printf("Enter %d elements: ", n);
for ( i = 0; i < n; i++) scanf("%d", &arr[i]);
quickSort(arr, 0, n - 1);
printf("Sorted array: ");
for ( i = 0; i < n; i++) printf("%d ", arr[i]);
printf("\n");
getch();
}


16c)Merge sort
#include <stdio.h>
void merge(int arr[], int left, int mid, int right) {
int n1 = mid - left + 1, n2 = right - mid, L[26], R[26], i, j = 0, k = left;
for (i = 0; i < n1; i++) L[i] = arr[left + i];
for (i = 0; i < n2; i++) R[i] = arr[mid + 1 + i];
i = 0;
while (i < n1 && j < n2) arr[k++] = (L[i] <= R[j]) ? L[i++] : R[j++];
while (i < n1) arr[k++] = L[i++];
while (j < n2) arr[k++] = R[j++]; }
void mergeSort(int arr[], int left, int right) {
if (left < right) {
int mid = left + (right - left) / 2;
mergeSort(arr, left, mid);
mergeSort(arr, mid + 1, right);
merge(arr, left, mid, right); }}
void main()
{
int n, i, arr[26];
clrscr();
printf("Enter the number of elements: ");
scanf("%d", &n);
printf("Enter %d elements:\n", n);
for (i = 0; i < n; i++) scanf("%d", &arr[i]);
mergeSort(arr, 0, n - 1);
printf("Sorted array: ");
for (i = 0; i < n; i++) printf("%d ", arr[i]);
printf("\n");
getch();
}
