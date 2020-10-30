class Cache {
    int currentTime = Calendar.getInstance().getTime().hashCode();;
    int capacity;

    public Cache(int capacity) {
        this.capacity = capacity;
    }

    static class Data {
        int value;
        int weight;
        int lastAccessTime;

        Data(int value, int weight, int lastAccessTime) {
            this.value = value;
            this.lastAccessTime = lastAccessTime;
            this.weight = weight;
        }
    }

    private HashMap<String, Data> hashMap = new HashMap<>();

    public int get(String key) {
        // Get the value of the key if the key exists in the cache, otherwise return -1
        if (hashMap.containsKey(key)) {
            // update access time and return value
            hashMap.get(key).lastAccessTime = currentTime;
            hashMap.put(key, hashMap.get(key));

            return hashMap.get(key).value;
        } else {
            return -1;
        }
    }

    public void put(String key, int value, int weight) {
        Data data = new Data(value, weight, currentTime);
        if (hashMap.size() > capacity && !hashMap.containsKey(key)) {
            // capacity is full and key is new and the key is not exist
            String isLowestKey = "";
            int lowestScore = Integer.MAX_VALUE;
            for ( String keys : hashMap.keySet() ) {
                // get lowest score key
                int keyScore = getScore(hashMap.get(keys));
                if (keyScore < lowestScore) {
                    lowestScore = keyScore;
                    isLowestKey = keys;
                }
            }
            // remove lowest score key
            hashMap.remove(isLowestKey);
        }
        // add the new key
        hashMap.put(key, data);
    }

    public int getScore(Data data) {
        if (currentTime != data.lastAccessTime) {
            return data.weight / currentTime - data.lastAccessTime;
        } else {
            return data.weight / -100;
        }
    }
}
// get method is using O(1) because the hashSet "containsKey" logic is same as o(1). 
// put method is using O(n) because the for-loop logic is same as o(n). When the hashmap size is big, the for loop process time will be longer
