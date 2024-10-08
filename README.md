# Performance Testing Results for HTTP Server

This document presents the results of performance testing conducted using ApacheBench (`ab`) on the HTTP server. The goal was to evaluate the server's response time and throughput under varying levels of concurrent requests.

## Test Configuration

- **Server Hostname**: 3.36.105.15
- **Server Port**: 8080
- **Document Path**: `/test`
- **Document Length**: 35 bytes
- **Total Requests (`-n`)**: 1,000 requests
- **Concurrency Levels Tested (`-c`)**: 100, 200, 300, 400, 500, 600, 700, 800, 900, 1,000

Each test was conducted with a total of 1,000 requests while varying the concurrency level to measure the server's performance under different loads.

## Summary of Test Results

| Concurrency Level | Total Time (sec) | Requests per Second (RPS) | Average Time per Request (ms) | Max Response Time (ms) | Transfer Rate (Kbytes/sec) |
|-------------------|------------------|--------------------------|-----------------------------|-----------------------|--------------------------|
| **100**           | 0.957            | 1,045.03                 | 95.691                      | 230                   | 171.45                   |
| **200**           | 0.914            | 1,093.80                 | 182.849                     | 356                   | 179.45                   |
| **300**           | 0.885            | 1,129.38                 | 265.634                     | 519                   | 185.29                   |
| **400**           | 0.886            | 1,129.07                 | 354.273                     | 572                   | 185.24                   |
| **500**           | 0.752            | 1,329.01                 | 376.221                     | 622                   | 218.04                   |
| **600**           | 0.765            | 1,308.00                 | 458.714                     | 741                   | 214.59                   |
| **700**           | 0.702            | 1,425.22                 | 491.151                     | 675                   | 233.83                   |
| **800**           | 0.642            | 1,558.50                 | 513.313                     | 573                   | 255.69                   |
| **900**           | 0.693            | 1,442.98                 | 623.710                     | 652                   | 236.74                   |
| **1,000**         | 0.557            | 1,795.78                 | 556.862                     | 520                   | 294.62                   |

## Analysis of Results

### 1. Requests per Second (RPS)
- The Requests per Second (RPS) increased as the concurrency level increased, reaching a peak of 1,795.78 RPS at a concurrency level of 1,000.
- The RPS indicates that the server was able to handle more simultaneous requests with increasing concurrency.

### 2. Average Time per Request
- The average time per request increased as the concurrency level increased. This is expected since the server has to handle more concurrent requests, resulting in longer processing times for individual requests.
- At a concurrency level of 100, the average time per request was 95.691 ms. At the highest concurrency level (1,000), the average time per request increased to 556.862 ms.

### 3. Maximum Response Time
- The maximum response time also increased with higher concurrency levels, which suggests that some requests took significantly longer to complete as the server handled more simultaneous requests.
- At a concurrency level of 100, the maximum response time was 230 ms, while at a concurrency level of 1,000, the maximum response time reached 741 ms.

### 4. Transfer Rate
- The transfer rate (Kbytes/sec) increased with concurrency levels, indicating that the server could serve more data as more requests were processed simultaneously.
- The highest transfer rate observed was 294.62 Kbytes/sec at a concurrency level of 1,000.

## Detailed Results

### 1. Concurrency Level: 100
- **Total Time**: 0.957 sec
- **Requests per Second**: 1,045.03
- **Average Time per Request**: 95.691 ms
- **Max Response Time**: 230 ms
- **Transfer Rate**: 171.45 Kbytes/sec

### 2. Concurrency Level: 200
- **Total Time**: 0.914 sec
- **Requests per Second**: 1,093.80
- **Average Time per Request**: 182.849 ms
- **Max Response Time**: 356 ms
- **Transfer Rate**: 179.45 Kbytes/sec

### 3. Concurrency Level: 300
- **Total Time**: 0.885 sec
- **Requests per Second**: 1,129.38
- **Average Time per Request**: 265.634 ms
- **Max Response Time**: 519 ms
- **Transfer Rate**: 185.29 Kbytes/sec

### 4. Concurrency Level: 400
- **Total Time**: 0.886 sec
- **Requests per Second**: 1,129.07
- **Average Time per Request**: 354.273 ms
- **Max Response Time**: 572 ms
- **Transfer Rate**: 185.24 Kbytes/sec

### 5. Concurrency Level: 500
- **Total Time**: 0.752 sec
- **Requests per Second**: 1,329.01
- **Average Time per Request**: 376.221 ms
- **Max Response Time**: 622 ms
- **Transfer Rate**: 218.04 Kbytes/sec

### 6. Concurrency Level: 600
- **Total Time**: 0.765 sec
- **Requests per Second**: 1,308.00
- **Average Time per Request**: 458.714 ms
- **Max Response Time**: 741 ms
- **Transfer Rate**: 214.59 Kbytes/sec

### 7. Concurrency Level: 700
- **Total Time**: 0.702 sec
- **Requests per Second**: 1,425.22
- **Average Time per Request**: 491.151 ms
- **Max Response Time**: 675 ms
- **Transfer Rate**: 233.83 Kbytes/sec

### 8. Concurrency Level: 800
- **Total Time**: 0.642 sec
- **Requests per Second**: 1,558.50
- **Average Time per Request**: 513.313 ms
- **Max Response Time**: 573 ms
- **Transfer Rate**: 255.69 Kbytes/sec

### 9. Concurrency Level: 900
- **Total Time**: 0.693 sec
- **Requests per Second**: 1,442.98
- **Average Time per Request**: 623.710 ms
- **Max Response Time**: 652 ms
- **Transfer Rate**: 236.74 Kbytes/sec

### 10. Concurrency Level: 1,000
- **Total Time**: 0.557 sec
- **Requests per Second**: 1,795.78
- **Average Time per Request**: 556.862 ms
- **Max Response Time**: 520 ms
- **Transfer Rate**: 294.62 Kbytes/sec

## Conclusion

- The server showed stable performance up to a concurrency level of 1,000, maintaining a steady increase in Requests per Second (RPS).
- The highest throughput was observed at a concurrency level of 1,000, with 1,795.78 RPS, at the cost of increased response times.
- The results indicate that the server can handle a high number of concurrent requests effectively, but response times will increase as the concurrency level rises.

## Recommendations

- **Optimize Resource Allocation**: Consider optimizing the server's resource allocation (CPU, Memory) to better handle higher concurrency levels.
- **Implement Load Balancing**: For even higher concurrency levels, consider implementing a load balancer to distribute requests across multiple servers.
- **Monitor and Tune Application Performance**: Continuously monitor server performance and identify any performance bottlenecks in the application to reduce response times and increase throughput.




# HTTP 서버 성능 테스트 결과

이 문서는 ApacheBench(`ab`) 도구를 사용하여 HTTP 서버의 성능을 테스트한 결과를 정리한 내용입니다. 이번 테스트의 목표는 서버가 다양한 동시 접속 요청(concurrency level) 하에서 얼마나 빠르고 안정적으로 응답할 수 있는지를 평가하는 것이었습니다.

## 테스트 환경

- **서버 호스트명**: 3.36.105.15
- **서버 포트**: 8080
- **문서 경로**: `/test`
- **문서 크기**: 35 bytes
- **총 요청 수 (`-n`)**: 1,000 요청
- **테스트한 동시 접속자 수 (`-c`)**: 100, 200, 300, 400, 500, 600, 700, 800, 900, 1,000

각 테스트는 총 1,000개의 요청을 보내며, 동시 접속자 수를 다양하게 설정하여 서버가 다른 부하에서 어떻게 반응하는지 확인했습니다.

## 테스트 결과 요약

| 동시 접속자 수 | 총 처리 시간 (초) | 초당 요청 수 (RPS) | 요청당 평균 응답 시간 (ms) | 최대 응답 시간 (ms) | 전송 속도 (Kbytes/sec) |
|----------------|------------------|-------------------|--------------------------|--------------------|-----------------------|
| **100**        | 0.957            | 1,045.03          | 95.691                   | 230                | 171.45                |
| **200**        | 0.914            | 1,093.80          | 182.849                  | 356                | 179.45                |
| **300**        | 0.885            | 1,129.38          | 265.634                  | 519                | 185.29                |
| **400**        | 0.886            | 1,129.07          | 354.273                  | 572                | 185.24                |
| **500**        | 0.752            | 1,329.01          | 376.221                  | 622                | 218.04                |
| **600**        | 0.765            | 1,308.00          | 458.714                  | 741                | 214.59                |
| **700**        | 0.702            | 1,425.22          | 491.151                  | 675                | 233.83                |
| **800**        | 0.642            | 1,558.50          | 513.313                  | 573                | 255.69                |
| **900**        | 0.693            | 1,442.98          | 623.710                  | 652                | 236.74                |
| **1,000**      | 0.557            | 1,795.78          | 556.862                  | 520                | 294.62                |

## 결과 분석

### 1. 초당 요청 수 (Requests per Second, RPS)
- 초당 요청 수(RPS)는 동시 접속자 수가 증가함에 따라 함께 증가하여, 동시 접속자 수 1,000명에서 최고 1,795.78 RPS를 기록하였습니다.
- 이 수치는 서버가 더 많은 동시 요청을 처리할 수 있음을 나타내며, 서버의 최대 처리량을 확인할 수 있습니다.

### 2. 요청당 평균 응답 시간
- 요청당 평균 응답 시간은 동시 접속자 수가 증가함에 따라 점진적으로 증가하였습니다. 이는 서버가 동시에 더 많은 요청을 처리해야 하므로 각 요청을 처리하는 데 더 많은 시간이 소요되기 때문입니다.
- 동시 접속자 수가 100일 때 평균 응답 시간은 95.691 ms였으나, 동시 접속자 수가 1,000으로 증가하면 556.862 ms로 늘어났습니다.

### 3. 최대 응답 시간
- 최대 응답 시간도 동시 접속자 수가 증가함에 따라 증가하였습니다. 이는 서버가 많은 요청을 동시에 처리할 때 일부 요청에 대한 응답 시간이 크게 지연될 수 있음을 보여줍니다.
- 동시 접속자 수 100명일 때 최대 응답 시간은 230 ms였으나, 동시 접속자 수 1,000명일 때 최대 응답 시간은 741 ms였습니다.

### 4. 전송 속도 (Transfer Rate)
- 전송 속도(Kbytes/sec) 역시 동시 접속자 수가 증가함에 따라 증가하여, 동시 접속자 수가 1,000명일 때 최고 294.62 Kbytes/sec를 기록하였습니다.
- 이는 서버가 동시 요청 수가 증가할수록 더 많은 데이터를 전송할 수 있음을 나타냅니다.

## 세부 결과

### 1. 동시 접속자 수: 100
- **총 처리 시간**: 0.957 초
- **초당 요청 수**: 1,045.03
- **요청당 평균 응답 시간**: 95.691 ms
- **최대 응답 시간**: 230 ms
- **전송 속도**: 171.45 Kbytes/sec

### 2. 동시 접속자 수: 200
- **총 처리 시간**: 0.914 초
- **초당 요청 수**: 1,093.80
- **요청당 평균 응답 시간**: 182.849 ms
- **최대 응답 시간**: 356 ms
- **전송 속도**: 179.45 Kbytes/sec

### 3. 동시 접속자 수: 300
- **총 처리 시간**: 0.885 초
- **초당 요청 수**: 1,129.38
- **요청당 평균 응답 시간**: 265.634 ms
- **최대 응답 시간**: 519 ms
- **전송 속도**: 185.29 Kbytes/sec

### 4. 동시 접속자 수: 400
- **총 처리 시간**: 0.886 초
- **초당 요청 수**: 1,129.07
- **요청당 평균 응답 시간**: 354.273 ms
- **최대 응답 시간**: 572 ms
- **전송 속도**: 185.24 Kbytes/sec

### 5. 동시 접속자 수: 500
- **총 처리 시간**: 0.752 초
- **초당 요청 수**: 1,329.01
- **요청당 평균 응답 시간**: 376.221 ms
- **최대 응답 시간**: 622 ms
- **전송 속도**: 218.04 Kbytes/sec

### 6. 동시 접속자 수: 600
- **총 처리 시간**: 0.765 초
- **초당 요청 수**: 1,308.00
- **요청당 평균 응답 시간**: 458.714 ms
- **최대 응답 시간**: 741 ms
- **전송 속도**: 214.59 Kbytes/sec

### 7. 동시 접속자 수: 700
- **총 처리 시간**: 0.702 초
- **초당 요청 수**: 1,425.22
- **요청당 평균 응답 시간**: 491.151 ms
- **최대 응답 시간**: 675 ms
- **전송 속도**: 233.83 Kbytes/sec

### 8. 동시 접속자 수: 800
- **총 처리 시간**: 0.642 초
- **초당 요청 수**: 1,558.50
- **요청당 평균 응답 시간**: 513.313 ms
- **최대 응답 시간**: 573 ms
- **전송 속도**: 255.69 Kbytes/sec

### 9. 동시 접속자 수: 900
- **총 처리 시간**: 0.693 초
- **초당 요청 수**: 1,442.98
- **요청당 평균 응답 시간**: 623.710 ms
- **최대 응답 시간**: 652 ms
- **전송 속도**: 236.74 Kbytes/sec

### 10. 동시 접속자 수: 1,000
- **총 처리 시간**: 0.557 초
- **초당 요청 수**: 1,795.78
- **요청당 평균 응답 시간**: 556.862 ms
- **최대 응답 시간**: 520 ms
- **전송 속도**: 294.62 Kbytes/sec

## 결론

- 서버는 동시 접속자 수 1,000명까지 안정적인 성능을 보여주며, 초당 요청 수(RPS)가 꾸준히 증가했습니다.
- 동시 접속자 수가 1,000명일 때 가장 높은 처리량인 1,795.78 RPS를 기록했지만, 응답 시간이 증가하는 경향을 보였습니다.
- 이 결과는 서버가 높은 동시 요청을 효과적으로 처리할 수 있음을 나타내지만, 동시 접속자 수가 증가할수록 응답 시간이 늘어날 수 있음을 보여줍니다.

## 권장 사항

- **자원 최적화**: 서버의 자원(CPU, 메모리) 할당을 최적화하여 더 높은 동시 접속자 수를 효과적으로 처리할 수 있도록 설정을 조정해보세요.
- **로드 밸런싱**: 더 높은 동시 접속자 수를 처리하려면, 로드 밸런서를 사용하여 여러 서버에 요청을 분산시키는 것을 고려해보세요.
- **애플리케이션 성능 모니터링 및 조정**: 애플리케이션의 성능 병목 현상을 파악하고, 응답 시간을 줄이고 처리량을 증가시키기 위한 최적화를 수행하세요.

