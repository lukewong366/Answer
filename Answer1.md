    public static Boolean isSubset(String[] mainArray, String[] subArray) {
        for (int i = 0; i < subArray.length; i++) {
            boolean isMatch = true;
            for (int j = 0; j < mainArray.length; j++) {
                if (subArray[i].equals(mainArray[j])) {
                    isMatch = true;
                    break;
                } else {
                    isMatch = false;
                }
            }
            if (!isMatch) {
                return false;
            }
         }
        return true;
    }
    
    // I am using  O(n ^2) as this function's algorithm.
    // This way is make the time will be longer when the input is more and more. 
    // However, I am not run the whole array in my function.
    // I will break the second loop when the sub array index matched a main array index.

    // Or have more easy way to get the boolean
    
    public static Boolean isSubset(String[] mainArray, String[] subArray) {
        boolean isMatch = true;
        HashSet<String> mainValue = new HashSet<>(Arrays.asList(mainArray));

        for(int j=0;j<subArray.length;j++) {
            if(mainValue.contains(subArray[j])) {
                isMatch = true;
            } else {
                isMatch = false;
            }
        }
        return isMatch;
    }
    
    // In this function, I am using o(n) because the hashSet "contains" logic is same as o(n). Therefore, it may take less time.
