# Data-Structures-2-Binary-Trees
public class BinaryTree {
private BinaryTreeNode overallRoot;

public BinaryTree(){
overallRoot=null;
}

public void add(int data){
overallRoot=add(overallRoot,data);
}
private BinaryTreeNode add(BinaryTreeNode overallRoot,int data){
if(overallRoot==null){
 overallRoot=new BinaryTreeNode(data);
 return overallRoot;
}else if(overallRoot.data<data){
overallRoot.right=add(overallRoot.right,data);
}else if(overallRoot.data>data){
overallRoot.left=add(overallRoot.left,data);
}
return overallRoot;
}

public boolean contains(int data){
return contains(overallRoot,data);
}
private boolean contains(BinaryTreeNode overallRoot,int data){
if(overallRoot==null) return false;
if(overallRoot.data==data) return true;
if(overallRoot.data>data) return contains(overallRoot.left,data);
return contains(overallRoot.right,data);
}

public int getMin(){
return getMin(overallRoot);
}
private int getMin(BinaryTreeNode overallRoot){
 if(overallRoot!= null&& overallRoot.left==null) return overallRoot.data;
 else return getMin(overallRoot.left);
}
public int getMax(){
return getMax(overallRoot);
}
private int getMax(BinaryTreeNode overallRoot){
if(overallRoot!=null && overallRoot.right==null) return overallRoot.data;
 else return getMax(overallRoot.right);
}
public void remove(int value){
overallRoot=remove(overallRoot,value);
/////return num;
}
private BinaryTreeNode remove(BinaryTreeNode overallRoot,int value){
if(overallRoot==null) return null;
else if(overallRoot.data<value){
overallRoot.right=remove(overallRoot.right,value);
}else if(overallRoot.data>value){
overallRoot.left=remove(overallRoot.left,value);
}else{
 if(overallRoot.left==null){
  return overallRoot.right;
 }else if(overallRoot.right==null){
 return overallRoot.left;
 }else{
 overallRoot.data=getMin(overallRoot.right);
 overallRoot.right=remove(overallRoot.right,overallRoot.data);
 }
}
return overallRoot;
}
public void print(){
print(overallRoot);
}
private void print(BinaryTreeNode overallRoot){
if(overallRoot!=null){
print(overallRoot.left);
System.out.print(overallRoot.data+" ");
print(overallRoot.right);
}

}
public int countLevels(){
return countLevels(overallRoot);
}
private int countLevels(BinaryTreeNode root){
if(root!=null){
return 1+Math.max(countLevels(root.left),countLevels(root.right));
}else{
return 0;
}
}
public int countLeaves2(){
return countLeaves2(overallRoot);
}
private int countLeaves2(BinaryTreeNode root){
if(root!=null){
 if(root.left==null && root.right==null) return 1;
return countLeaves2(root.left)+countLeaves2(root.right);
 }else{
return 0;
 }
}
public int sum(){
return sum(overallRoot);
}
private int sum(BinaryTreeNode root){
if(root!=null){
return root.data+sum(root.left)+sum(root.right);
 }else{
 return 0;
 }
}
public void printLevel(int num){
int start=1;
 printLevel(num,overallRoot,start);
 }
 private void printLevel(int num, BinaryTreeNode overallRoot,int start){
 if(overallRoot!=null){
  System.out.print(overallRoot.data+" ");
 
  
  //System.out.println();
  printLevel(num,overallRoot.left,start+1);
  printLevel(num,overallRoot.right,start+1);
 }
}
public void reverseTree(){
overallRoot=reverseTree(overallRoot);
}
private BinaryTreeNode reverseTree(BinaryTreeNode overallRoot){
if(overallRoot!=null){
BinaryTreeNode left=overallRoot.left;
overallRoot.left=overallRoot.right;
overallRoot.right=left;
 }
 return overallRoot;
}
public void removeLeaves(){
overallRoot=removeLeaves(overallRoot);
}
private BinaryTreeNode removeLeaves(BinaryTreeNode overallRoot){
if(overallRoot!=null){
 if(overallRoot.left==null && overallRoot.right==null) return null;
overallRoot.left=removeLeaves(overallRoot.left);
overallRoot.right=removeLeaves(overallRoot.right);
 }
 return overallRoot;
}
public int numberOfBranches(){
return numberOfBranches(overallRoot);
}
private int numberOfBranches(BinaryTreeNode overallRoot){
if(overallRoot!=null){
if(overallRoot.left==null && overallRoot.right==null){
return 0; 
}else{
return 1+numberOfBranches(overallRoot.left)+numberOfBranches(overallRoot.right);
  }
 }
 return 0;
}
public int numberOfLeaves(){
return numberOfLeaves(overallRoot);
}
private int numberOfLeaves(BinaryTreeNode overallRoot){
if(overallRoot!=null){
 if(overallRoot.left==null && overallRoot.right==null) return 1;
 else return numberOfLeaves(overallRoot.left)+numberOfLeaves(overallRoot.right);
 }
 return 0;
 }
public void printAllLevels(){
printAllLevels(overallRoot,1);
}
private void printAllLevels(BinaryTreeNode overallRoot,int a){
 if(overallRoot!=null){
 printAllLevels(overallRoot.right,a+1);
 for(int i=0; i<a; i++){
 System.out.print("    ");
 }
System.out.println(overallRoot.data);
printAllLevels(overallRoot.left,a+1);
 }
}
private class BinaryTreeNode {
 private int data;
 private BinaryTreeNode left;
 private BinaryTreeNode right;
 
 public BinaryTreeNode(int data){
 this(data,null,null);
 }
 public BinaryTreeNode(int data, BinaryTreeNode left,BinaryTreeNode right){
 this.data=data;
 this.left=left;
 this.right=right;
  }
 }
}
