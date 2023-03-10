# Binary-Search-tree
Create a BST of user defined values
/*Create a BST of user defined values. Keep asking user values until he/she enters any negative 
number. Now display the elements of the tree in In-order, Post-order and Pre-order form. Your 
program should also contain a search function which should find a particular number entered by 
user. Search function should be recursive.*/

#include<iostream>
using namespace std;
struct node 
{
    int data;
    node *left;
    node *right;
};
node *createnode(int d)
{
    node *nn=new node;
    nn->data=d;
    nn->left=NULL;
    nn->right=NULL;
    return nn;
}
    node *insert(node *r,int d)
    {
    
        if(r==NULL)
        {
           return createnode(d);
        }
        if(d<r->data)
        {
            r->left=insert(r->left,d);
        }
        if(d>r->data)
        {
            r->right=insert(r->right,d);
        }
        
        return r;
    }
    void printinorder(node *r)
    {
        if(r==NULL)
        {
            return;
        }
        printinorder(r->left);
        cout<<r->data;
         cout<<endl;
        printinorder(r->right);
       
    }
    
      void printpostorder(node *r)
    {
        if(r==NULL)
        {
            return;
        }
        printpostorder(r->left);
        printpostorder(r->right);
         cout<<r->data;
         cout<<endl;
       
    }
    

    void printpreorder(node *r)
    {
        if(r==NULL)
        {
            return;
        }
        cout<<r->data;
         cout<<endl;
        printpreorder(r->left);
        printpreorder(r->right);
         
       
    }
    
bool search(node *r,int d)
{
    if(r==NULL)
    {
     return false;
    }
    if(r->data==d)
    {
      return true;
    }
    if(d<r->data)
    {
        return search(r->left,d);
    }
    else
    return search(r->right,d);
}
int main()
{
    node *root=new node;
    root=NULL;
    int c;
    do 
    {
       cout<<"Enter 1 for inserting data \n Enter 2 to search the data \n Enter 3 to print data in inorder \n Enter 4 to print in postorder\n Enter 5 to print data in preorder \n Enter -100 to exit"<<endl;
       cin>>c;
    if(c==1)
    {
        int k;
        cout<<"enter the data you want to insert"<<endl;
        cin>>k;
        root=insert(root,k);
    }
    if(c==2)
    {
        int k;
    cout<<"enter the data you want to search"<<endl;
    cin>>k;
     cout<<search(root,k)<<endl;
    }
   if(c==3)
   { cout<<"Printing the data in inorder"<<endl;
    printinorder(root);
    }
    if(c==4)
    {
        cout<<"Printing the data in postorder"<<endl;
        printpostorder(root);
    }
    if(c==5)
    {
        cout<<"Printing the data in preorder"<<endl;
        printpreorder(root);
    }
    }
    while(c!=-100);
}
