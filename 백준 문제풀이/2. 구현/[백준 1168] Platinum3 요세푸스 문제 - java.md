## 요세푸스 문제

https://www.acmicpc.net/problem/1168

## 내 풀이

* 세그먼크 트리 사용!


```java
package baekjoon;

import java.io.*;
import java.util.StringTokenizer;

public class P_1168 {

    static int n, k;
    static int[] tree;

    // 초기화
    static void build(int node, int start, int end) {
        if (start == end) {
            tree[node] = 1;
        } else {
            int mid = (start + end) / 2;
            build(node * 2, start, mid);
            build(node * 2 + 1, mid + 1, end);
            tree[node] = tree[node * 2] + tree[node * 2 + 1];
        }
    }

    static void update(int node, int start, int end, int idx) {
        if (start == end) {
            tree[node] = 0;
        } else {
            int mid = (start + end) / 2;
            if (idx <= mid) update(node * 2, start, mid, idx);
            else update(node * 2 + 1, mid + 1, end, idx);
            tree[node] = tree[node * 2] + tree[node * 2 + 1];
        }
    }

    static int query(int node, int start, int end, int k) {
        if (start == end) return start;

        int mid = (start + end) / 2;

        if (tree[node * 2] >= k)
            return query(node * 2, start, mid, k);
        else
            return query(node * 2 + 1, mid + 1, end, k - tree[node * 2]);
    }

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());

        n = Integer.parseInt(st.nextToken());
        k = Integer.parseInt(st.nextToken());

        tree = new int[4 * n];
        build(1, 1, n);

        StringBuilder sb = new StringBuilder();
        sb.append("<");

        int idx = k;   // 첫 번째 K번째부터 시작

        for (int i = 0; i < n; i++) {

            int alive = tree[1];  // 현재 살아있는 사람 수

            idx = ( (idx - 1) % alive ) + 1;

            int person = query(1, 1, n, idx);
            sb.append(person);
            if (i != n - 1) sb.append(", ");

            update(1, 1, n, person);

            idx = idx + k - 1;  // 다음 k번째로 이동
        }

        sb.append(">");
        System.out.println(sb);
    }
}

```
