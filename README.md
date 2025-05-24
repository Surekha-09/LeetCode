# Anagram
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) {
            return false;
        }
        int[] freq = new int[26];
        for (int i = 0; i < s.length(); i++) {
            freq[s.charAt(i) - 'a']++;
            freq[t.charAt(i) - 'a']--;
        }
        for (int i = 0; i < freq.length; i++) {
            if (freq[i] != 0) {
                return false;
            }
        }
        return true;
    }
}


# delete node in BST
class Solution {
    public TreeNode deleteNode(TreeNode root, int key) {
        if(root == null ) {
            return null;
        }
        if(root.val<key){
            root.right = deleteNode(root.right,key);
        }
        else if(root.val>key) {
            root.left = deleteNode(root.left,key);
        }
        else{
            if(root.left == null && root.right == null ) {
                return null;
            }
            if(root.left ==  null){
                return root.right;
            }
            else if(root.right ==  null ) {
                return root.left;
            }
            TreeNode IS = findInOrderSuccessor(root.right);
            root.val = IS.val;  
            root.right = deleteNode(root.right,IS.val);
        }
        return root;
    }
    private TreeNode findInOrderSuccessor(TreeNode root){
        while(root.left != null){
            root = root.left;
        }
        return root;
    }
}


# Number of senior citizens
class Solution {
    public int countSeniors(String[] details) {
        int ans=0;
        for(int i=0;i<details.length;i++){
            int age=(details[i].charAt(11)-'0')*10+(details[i].charAt(12)-'0');
            if(age>60) ans++;
        }
        return ans;
    }
}

# Bulb Switcher
class Solution:
    def bulbSwitch(self, n: int)-> int:
        return int(sqrt(n))

# House Robber
class Solution {
    public int rob(int[] nums) {
        int rob = 0;
        int norob = 0;
        for (int i = 0; i < nums.length; i ++) {
            int newRob = norob + nums[i];
            int newNoRob = Math.max(norob, rob);
            rob = newRob;
            norob = newNoRob;
        }
        return Math.max(rob, norob);
    }
}


# Bulls and Cows
class Solution:
    def getHint(self, secret: str, guess: str) -> str:
        b,c=0,0
        s,g=[],[]
        for i in range(len(secret)):
            if secret[i]==guess[i]:
                b+=1
            else:
                s.append(secret[i])
                g.append(guess[i])
        print(g,s)
        for i in g:
            if i in s:
                c+=1
                s.remove(i)
        return str(b)+'A'+str(c)+'B'


# Count good numbers
class Solution {
    int mod=(int)1e9+7;
    public int countGoodNumbers(long n) {
        long even=(n+1)/2;
        long odd=n/2;
        long a=pow(4,odd)%mod;
        long b=pow(5,even)%mod;
        return(int)((a*b)%mod);
    }
    public long pow(long a,long b){
    if(b==0){
        return 1;
    }
    long temp=pow(a,b/2);
    if(b%2==0){
        return(temp*temp)%mod;
    }
    else{
        return(a*temp*temp)%mod;
    }
    }
}

# Hamming distance
class Solution {
    public int hammingDistance(int x, int y) {
        int count = 0;
        while(x > 0 || y > 0){
            count += ((x & 1) ^ (y & 1));
            x >>= 1;
            y >>= 1;
        }
        return count;
    }
} 
