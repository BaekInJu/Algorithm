# DFS - 너비 우선 탐색

```
public static int distance(int[][] arr) {
        //배열 세로 길이
        int N = arr.length;

        //배열 가로 길이
        int M = arr[0].length;

        // 방문 여부를 저장하는 배열
        boolean[][] visited = new boolean[N][M];

        // 상, 하, 좌, 우로 이동하는 배열
        int[] dx = {-1, 1, 0, 0};
        int[] dy = {0, 0, -1, 1};

        Queue<int[]> queue = new LinkedList<>();
        queue.offer(new int[]{0, 0, 0}); // 시작점 (0,0)과 거리 1을 큐에 추가
        visited[0][0] = true; // 시작점 방문 표시

        while (!queue.isEmpty()) {
            int[] current = queue.poll();
            int x = current[0];
            int y = current[1];
            int distance = current[2];

            // 출구에 도착하면 거리 반환
            if (x == N - 1 && y == M - 1) {
                return distance;
            }

            // 상하좌우로 이동
            for (int i = 0; i < 4; i++) {
                int nx = x + dx[i];
                int ny = y + dy[i];

                // 이동 가능한 위치이고 방문하지 않았다면 큐에 추가
                if (nx >= 0 && nx < N && ny >= 0 && ny < M && arr[nx][ny] == 1 && !visited[nx][ny]) {
                    queue.offer(new int[]{nx, ny, distance + 1});
                    visited[nx][ny] = true; // 방문 표시
                }
            }
        }
```