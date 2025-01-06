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


int removeDuplicates(int* nums, int numsSize) {
  int c=1;
  for(int i=0;i<numsSize;i++){
    if( nums[i]!=nums[c-1]){
        nums[c]=nums[i];
        c++;
    }
  }
  return c;
}


int removeElement(int *nums, int numsSize, int val) {
    int count = 0;

    for (int i = 0; i < numsSize; i++)
        if (nums[i] == val) 
            count++;
        else 
            nums[i - count] = nums[i];
    return (numsSize - count);
}

int strStr(char* str, char* substr) {
    int substr_len = 0;
    while (substr[substr_len] != '\0') {
        substr_len++;
    }

    int i, j;

    for (i = 0; str[i] != '\0'; i++) {
        for (j = 0; j < substr_len && str[i + j] == substr[j]; j++)
            ;
        if (j == substr_len) {
            return i;
        }
    }

    return -1;
}


int searchInsert(int* nums, int numsSize, int target) {
    int low = 0;
    int high = numsSize - 1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        if (nums[mid] == target) {
            return mid; 
        }
        if (nums[mid] < target) {
            low = mid + 1;  
        } else {
            high = mid - 1; 
        }
    }
    
    return low;
}



int lengthOfLastWord(char* s) {
    int c=0;
    int l=strlen(s);
    for(int i=l-1;i>=0;i--){
        if(s[i]==' '){
            if(c>0){
            break;
        }
        }
        else{
        c++;
    }
    }
    return c;
}


/** Note: The returned array must be malloced, assume     */
/** caller calls free().                                  */
int *plusOne(int *digits, int digitsSize, int *returnSize) {
    *returnSize = digitsSize;
    int *plusOne = malloc(digitsSize * sizeof(int));
    if (plusOne == NULL)
        return (NULL);
    for (int i = 0; i < digitsSize; i++)
        plusOne[i] = digits[i];
    
    plusOne[digitsSize - 1]++;
    for (int i = digitsSize - 1; i - 1 >= 0; i--)
        if (plusOne[i] == 10) {
            plusOne[i] = 0;
            plusOne[i - 1]++;
        }

    if (plusOne[0] == 10) {
        (*returnSize)++;
        plusOne = realloc(plusOne, *returnSize * sizeof(int));
        if (plusOne == NULL)
            return (NULL);
        memmove(plusOne + 1, plusOne, digitsSize * sizeof(int));
        plusOne[0] = 1;
        plusOne[1] = 0;
    }
    return (plusOne);
}


char * addBinary(char * a, char * b){
    int sizeA = strlen(a);
    int sizeB = strlen(b);
    int sizeOutput = (sizeA > sizeB ? sizeA : sizeB) + 1;
    char * output = (char *)malloc(sizeOutput + 1);
    int sum = 0;
    
    output[sizeOutput] = '\0';
    
    while(sizeA > 0 || sizeB > 0 || sum > 0) {
        
        if(sizeA > 0) {
            sum += a[--sizeA] - '0';
        }
        if(sizeB > 0) {
            sum += b[--sizeB] - '0';
        }
        output[--sizeOutput] = sum % 2 + '0';
        sum /= 2;
    }
    return output + sizeOutput;   
}


class Solution {
public:
    int solve(int n,vector<int> &dp){
        //base case
        if(n<=2)
          return n;
        
        if(dp[n]!=-1) 
          return dp[n]; 
        
        dp[n]=solve(n-1,dp)+solve(n-2,dp);
        return dp[n];
    }
    int climbStairs(int n) {
        if(n<=2)
         return n;
        vector<int> dp(n+1,-1);
        return solve(n,dp);
    }
};


struct ListNode* deleteDuplicates(struct ListNode* head) {
    struct ListNode* temp=head;
    while (temp&&temp->next)
    {
        if (temp->next->val==temp->val)
        {
            temp->next=temp->next->next;
            continue;
        }
        temp=temp->next;
    }
    return head;
}


void merge(int* nums1, int nums1Size, int m, int* nums2, int nums2Size, int n) {
    if(n == 0)return;
    int len1 = nums1Size;
    int end_idx = len1-1;
    while(n > 0 && m > 0){
        if(nums2[n-1] >= nums1[m-1]){
        nums1[end_idx] = nums2[n-1];
        n--;
        }else{
            nums1[end_idx] = nums1[m-1];
            m--;
        }
        end_idx--;
    }
    while (n > 0) {
        nums1[end_idx] = nums2[n-1];
        n--;
        end_idx--;
    }
}


//iterative solution using stack
int* inorderTraversal(struct TreeNode* root, int* returnSize){
    int*ans=malloc(100*sizeof(int));
    *returnSize=0;
    struct TreeNode**stack=malloc(100*sizeof(struct TreeNode*));
    int top=0;
    while(top||root){
        if(root){
            stack[top++]=root;
            root=root->left;
        }
        else{
            root=stack[--top];
            ans[(*returnSize)++]=root->val;
            root=root->right;
        }
    }
    free(stack);
    ans=realloc(ans,(*returnSize)*sizeof(int));
    return ans;
}


/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */
bool isSameTree(struct TreeNode* p, struct TreeNode* q) {
    if (p == NULL && q == NULL) {
        return true;
    } else if (p == NULL || q == NULL) {
        return false;
    } else {
        return p->val == q->val && isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
    }
}


/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */
bool isSymmetricHelp(struct TreeNode* left, struct TreeNode* right) {
    if (left == NULL || right == NULL) {
        return left == right;
    }
    if (left->val != right->val) {
        return false;
    }

    return isSymmetricHelp(left->left, right->right) && isSymmetricHelp(left->right, right->left);
}

bool isSymmetric(struct TreeNode* root) {
    return root == NULL || isSymmetricHelp(root->left, root->right);
}


/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */
int max(int a, int b) { return (a > b) ? a : b; }
int depth(struct TreeNode* root) {
    if(root==NULL)
    {
        return 0;
    }
    return 1+max(depth(root->left),depth(root->right));
}
int maxDepth(struct TreeNode* root) { return depth(root); }


struct TreeNode* ConvToBST(int *nums, int beg, int end){
    if(end < beg)
        return NULL ;
    int mid = (beg + end)/2 ;
    struct TreeNode* root = (struct TreeNode*)malloc(sizeof(struct TreeNode));
    root->val = nums[mid];
    root->left = ConvToBST(nums, beg, mid-1);
    root->right = ConvToBST(nums, mid+1, end);
    return root;
}
struct TreeNode* sortedArrayToBST(int* nums, int numsSize){
    if(numsSize <= 0)
        return NULL;
    else
        return ConvToBST(nums, 0, numsSize-1);
}


class Solution {
public:
    bool isBalanced(TreeNode* root) {
        if(root == nullptr)
            return true;
        else{
            int leftH = height(root->left);
            int rightH = height(root->right);
            int diff = abs(rightH - leftH);
            return diff <= 1 && isBalanced(root->left) && isBalanced(root->right);   
        } 
    }
    int height(TreeNode* root){
        if(root == nullptr){
            return 0;
        }else{
            return 1 + max(height(root->left), height(root->right));
        }
    }
};


int minDepth(struct TreeNode* root) {
    if (!root) return 0;
    int L = minDepth(root->left), R = minDepth(root->right);
    return L<R && L || !R ? 1+L : 1+R;
}


/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool rootToLeafPathSum(TreeNode* root, int targetSum, int sum){
        if(root == nullptr)
            return false;
        if(root -> left == nullptr && root -> right == nullptr){
            sum = sum + root -> val;
            if(sum == targetSum)
                return true;   
        }
        return rootToLeafPathSum(root -> left, targetSum, sum + root -> val) || rootToLeafPathSum(root -> right, targetSum, sum + root -> val);
    }
    bool hasPathSum(TreeNode* root, int targetSum) {
        int sum = 0;
        return rootToLeafPathSum(root, targetSum, sum);
    }

};










