#### 二分查找（binary search）

简要来说就是通过不断找新的中点来“砍一半”,2^n个数据,最后只需要n次就可以找到结果

因此时间复杂度是log2n



二分查找(有序列表)

```java
 public static boolean exsit(int[] arr, int num){
        if(arr == null || arr.length == 0){
            return false;
        }
        int l = 0, r = arr.length - 1, m = 0;
        while(l <= r){
            //更加安全的写法，意思是l向r移动了一般的位置
            m = l + (r - l) / 2;
            //m = l + ((r - l) >> 1);
            if(arr[m] == num){
                return true;
            }else if(arr[m] > num){
                //...........150........
                //            m
                // ..........r............
                r = m - 1;
            }else{
                l = m + 1;
            }
        }
        return false;
    }
```

二分查找(大于target的最左侧的数)

```java
public static int findleft(int[] arr, int num){
        int l = 0, r = arr.length - 1, m = 0;
        int ans = -1;
        while(l <= r){
            m = l + ((r - l) >> 1);
            if(arr[m] >= num){
                ans = m;
                r = m - 1;
            }else{
                r = m + 1;
            }
        }
        return ans;
    }
```

二分查找(小于target最右侧的数)

```java
public static int findRight(int[] arr, int num){
        int l = 0, r = arr.length - 1, m = 0;
        int ans = -1;
        while(l <= r){
            m = l + ((r - l) >> 1);
            if(arr[m] <= num){
                //满足记下ans，往右二分
                l = m + 1;
                ans = m;
            }else{
                //不满足不记ans，往左二分
                r = m - 1;
            }
        }
        return ans;
    }
```

