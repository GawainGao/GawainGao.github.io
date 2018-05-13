







```
class Solution {
    public boolean repeatedSubstringPattern(String s) {
        int ll = s.length();
        if (ll == 0) { return false; }
        if (ll == 1) { return false; }
        for (int i=1; i<ll/2+1; i++){
            if (ll % i == 0){
                int jj = ll/i;
                String t = "";
                for (int j=0;j<jj;j++){
                    t += s.substring(0,i);
                    
                }
                System.out.println(t);
                System.out.println(s);
                if ( t.equals(s) ) { 
                    
                    return true; 
                }
            }
        }
        return false;
    }
}

```