# LEETCODE819-Most-Common-Word

class Solution {
    fun mostCommonWord(paragraph: String, banned: Array<String>): String {
        
        // convert list to array in KT is easier
        var bannedList : List<String> = banned.toList()
        
        // remember not Int, not Integer
        val map = hashMapOf<String,Int>()
        
        // remove everything except a-z and A-Z
        // you need to create regex object and use it
        val re = Regex("[^A-Z^a-z]")
        val p =   paragraph.replace(re," ").toLowerCase()
        val arr = p.split(" ")
        for(s in arr) {            
            if(s == "") continue
            if(bannedList.contains(s)) continue
            
            map.put(s,map.getOrDefault(s,0)+1);        
        }
        
        
        var max         = Integer.MIN_VALUE;
        var topWord     = "";
        
        for((k,v) in map) {
            if(v>max) {
                print("key: "   + k)
                print("value: " + v)
                max = v
                topWord = k
            }
            
        }
        
        return topWord;
                
    }
}

/*
//Java:
class Solution {
    
    public String mostCommonWord(String paragraph, String[] banned) {
        
        List<String> list = Arrays.asList(banned);
        Map<String,Integer> map = new HashMap<>();
        
        paragraph  = paragraph.replaceAll("[^a-z^A-Z]"," ").toLowerCase();
        String[] a = paragraph.split(" ");
        
        for(String s : a) {
            
            if(s.equals("")) continue;
            if(list.contains(s)) continue;
            
            map.put(s,map.getOrDefault(s,0)+1);
                        
        }
        
        int    max         = Integer.MIN_VALUE;
        String topWord     = "";
        for(Map.Entry<String,Integer> e : map.entrySet()) {
            
            if(e.getValue()>max) {
                max = e.getValue();
                topWord = e.getKey();
            }
            
        }
        
        return topWord;
        
    }
    
}
*/
