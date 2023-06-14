#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>

struct tree{
  char d;
  struct tree *left,*right;
};

struct tree *stack[50];
int top=-1;

void operand(char);
void operator1(char);
void push(struct tree *);
struct tree *pop();
void inorder(struct tree *);
void postorder(struct tree *);
void preorder(struct tree *);

void main(){
    int i=0;
    char postfix[20];
    printf("\n************************************************\n");
    printf("Enter postfix expression : ");
    
    scanf(" %s",postfix);
    printf("\n************************************************\n");
    while(postfix[i]!='\0'){
        if(isalnum(postfix[i])){
            operand(postfix[i]);
        }
        else{
            operator1(postfix[i]);
        }
        i++;
    }
    printf("\n************************************************\n");
    printf("Inorder traversal : ");
    inorder(stack[top]);
    printf("\n");
    printf("Postorder traversal : ");
    postorder(stack[top]);
    printf("\n");
    printf("Preorder traversal : ");
    preorder(stack[top]);
    printf("\n************************************************\n");
}

void operand(char c){
    struct tree *node = malloc(sizeof(struct tree));
    node->d=c;
    node->left=node->right=NULL;
    push(node);
}
void operator1(char c){
    struct tree *node = malloc(sizeof(struct tree));
    node->d=c;
    node->right=pop();
    node->left=pop();
    push(node);
}
void push(struct tree *node){
    top++;
    stack[top]=node;
}
struct tree *pop(){
    return stack[top--];
}
void inorder(struct tree *node){
    if(node==NULL){
        return;
    }
    else{
        inorder(node->left);
        printf("%c",node->d);
        inorder(node->right);
    }
}
void postorder(struct tree *node){
    if(node==NULL){
        return;
    }
    else{
        postorder(node->left);
        postorder(node->right);
        printf("%c",node->d);
    }
}
void preorder(struct tree *node){
    if(node==NULL){
        return;
    }
    else{
        printf("%c",node->d);
        preorder(node->left);
        preorder(node->right);
    }
}
