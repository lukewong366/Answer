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
    
    // I am using o(n) because the hashSet "contains" logic is same as o(n). Therefore, it may take less time.
