# aditi1508
int* twoSum(int* nums, int numsSize, int target, int* returnSize) {
    for (int i = 0; i < numsSize; i++) {
        for (int j = i + 1; j < numsSize; j++) {
            if (nums[j] == target - nums[i]) {
                int* result = malloc(sizeof(int) * 2);
                result[0] = i;
                result[1] = j;
                *returnSize = 2;
                return result;
            }
        }
    }
    // Return an empty array if no solution is found
    *returnSize = 0;
    return malloc(sizeof(int) * 0);
}


bool isPalindrome(int x) {

     double rev=0, rem, orignal=x;
    
    
        while(x>0)
        {
            rem = x % 10;
            rev = rev * 10 + rem;
            x/=10;
        }

        if(rev == orignal)
            return true;
        
         else
       return false;
    
}


{
    int t['X' + 1] = {
        ['I'] = 1,
        ['V'] = 5,
        ['X'] = 10,
        ['L'] = 50,
        ['C'] = 100,
        ['D'] = 500,
        ['M'] = 1000,
    };
    int res = 0;
    for (int i = 0; s[i]; i++) {
        if (t[s[i]] < t[s[i+1]])
            res -= t[s[i]];
        else
            res += t[s[i]];
    }
    return res;
}


char * longestCommonPrefix(char ** str, int size){

    int i,j,flag=0,k=0,min=100000;
    char *s = (char *)malloc(127*sizeof(char));
    strcpy(s,"");
    if(size==0)
        return s;
    char c;
    for(i=0;i<size;i++)
    {
        if(min>strlen(str[i]))
            min = strlen(str[i]);
    }
    for(i=0;i<min;i++,k++)
    {
        c = str[0][i];
        for(j=0;j<size;j++)
        {
            if(str[j][i]!=c)
            {
                flag = 1;
                break;
            }
        }
    //    printf("%d ",flag);
    //    printf("%d ",strlen(str[i]));
        if(flag)
            break;
        else
        {
            s[k] = c;
            s[k+1] = '\0';
        }
    }
 //   printf("%s",s);
    return s;
}


bool isValid(char* s) {
    int len =strlen(s);
    char stack[len];
    int top = -1;
    for(int i=0;i<len;i++){
        if(s[i]=='(' || s[i] == '{' || s[i] == '[' ){
            stack[++top] = s[i];
        }else{
            if(top == -1 ||( s[i]==')'&&stack[top] != '(')||(s[i]=='}'&&stack[top] != '{')||(s[i]==']'&&stack[top]!='[')){
                return false;
            } 
            top--;
        } 
    }  
    return top == -1; 
}



/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* mergeTwoLists(struct ListNode* list1, struct ListNode* list2) {
    // Step 1 -- Check some special situations..
    if (list1 == NULL) 
        return list2;
    else if (list2 == NULL) 
        return list1;
    if (list1 == NULL && list2 == NULL)
        return NULL;

    // Step 2 -- Create Linked List and add first element.
    struct ListNode* root=(struct ListNode*)malloc(sizeof(struct ListNode));
    if(list1->val > list2->val){
        root->val=list2->val;
        list2=list2->next;
    }
    else{
        root->val=list1->val;
        list1=list1->next;
    }
    struct ListNode* iter=root; // I will use iteration to continue on our new list.
   
    // Step 3 -- While both lists are not NULL, do the necessary operations.
    while(list1 != NULL && list2 != NULL){
        iter->next=(struct ListNode*)malloc(sizeof(struct ListNode));
        iter=iter->next;
        if(list1->val >list2->val){
            iter->val=list2->val;
            list2=list2->next;
        }
        else{
            iter->val=list1->val;
            list1=list1->next;
        }

    }

    // Step 4 -- One of them reach NULL, but other list is still NOT NULL. So, continue to add.
    if(list1 == NULL && list2 != NULL){
        while(list2 != NULL){
            iter->next=(struct ListNode*)malloc(sizeof(struct ListNode));
            iter=iter->next;
            iter->val=list2->val;
            list2=list2->next;
        }
    }
    else if(list1 != NULL && list2 == NULL){
        while(list1 != NULL){
            iter->next=(struct ListNode*)malloc(sizeof(struct ListNode));
            iter=iter->next;
            iter->val=list1->val;
            list1=list1->next;
        }
    }

    iter->next=NULL; // Last node's pointer must point somewhere and that is NULL.
    return root; // return our merged list !!
}


