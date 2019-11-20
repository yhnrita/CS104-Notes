#### BST

How to check if it's a BST and if it's balanced:
```c++
#include "bst.h"

#include <stack>
#include <queue>
#include <set>
#include <vector>
#include <iostream>
#include <cstdlib>
#include <algorithm>
#include <climits>

using namespace std;

//Helper functions?
bool isBST(Node *root) {
    if(root == NULL)
    	return false;

    if(root->left == NULL && root->right == NULL)
    	return true;

    if(root->left != NULL && root->right != NULL) {
    	Node *temp = root->left;
    	while(temp->right != NULL)
    		temp = temp->right;
    	if(root->key < temp->key)
    		return false;

    	temp = root->right;
    	while(temp->left != NULL)
    		temp = temp->left;
    	if(root->key > temp->key)
			return false;

		return isBST(root->left);
		return isBST(root->right);
    }

    if(root->left != NULL) {
    	Node *temp = root->left;
    	while(temp->right != NULL)
    		temp = temp->right;
    	if(root->key < temp->key)
    		return false;
    	else
    		return isBST(root->left);
	}
	if(root->right != NULL) {
		Node *temp = root->right;
    	while(temp->left != NULL)
    		temp = temp->left;
    	if(root->key > temp->key)
			return false;
		else
			return isBST(root->right);
	}


}
 
int height(Node *currNode) {
	if(currNode == NULL)
		return 0;

	if(height(currNode->left) > height(currNode->right))
		return height(currNode->left) + 1;
	else
		return height(currNode->right) + 1;
}

//Helper functions?
bool isBalanced(Node *root) {
	if(root == NULL)
		return true;

	if(abs(height(root->left) - height(root->right)) <= 1)
		return true;
	else
		return false;
}

```