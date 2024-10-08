# Performance Testing Results for HTTP Server

이 문서는 ApacheBench(`ab`) 도구를 사용하여 HTTP 서버의 성능을 테스트한 결과를 정리한 내용입니다. 이번 테스트의 목표는 서버가 다양한 동시 접속 요청(concurrency level) 하에서 얼마나 빠르고 안정적으로 응답할 수 있는지를 평가하는 것입니다.

## Test Configuration

- **Server Hostname**: 3.36.105.15
- **Server Port**: 8080
- **Document Path**: `/test`
- **Document Length**: 35 bytes
- **Total Requests (`-n`)**: 1,000 requests
- **Concurrency Levels Tested (`-c`)**: 100, 200, 300, 400, 500, 600, 700, 800, 900, 1,000

각 테스트는 총 1,000개의 요청을 보내며, 동시 접속자 수를 다양하게 설정하여 서버가 다른 부하에서 어떻게 반응하는지 확인했습니다.

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
- 초당 요청 수(RPS)는 동시 접속자 수가 증가함에 따라 함께 증가하여, 동시 접속자 수 1,000명에서 최고 1,795.78 RPS를 기록하였습니다.
- 이 수치는 서버가 더 많은 동시 요청을 처리할 수 있음을 나타내며, 서버의 최대 처리량을 확인할 수 있습니다.

### 2. Average Time per Request
- 요청당 평균 응답 시간은 동시 접속자 수가 증가함에 따라 점진적으로 증가하였습니다. 이는 서버가 동시에 더 많은 요청을 처리해야 하므로 각 요청을 처리하는 데 더 많은 시간이 소요되기 때문입니다.
- 동시 접속자 수가 100일 때 평균 응답 시간은 95.691 ms였으나, 동시 접속자 수가 1,000으로 증가하면 556.862 ms로 늘어났습니다.

### 3. Maximum Response Time
- 최대 응답 시간도 동시 접속자 수가 증가함에 따라 증가하였습니다. 이는 서버가 많은 요청을 동시에 처리할 때 일부 요청에 대한 응답 시간이 크게 지연될 수 있음을 보여줍니다.
- 동시 접속자 수 100명일 때 최대 응답 시간은 230 ms였으나, 동시 접속자 수 1,000명일 때 최대 응답 시간은 741 ms였습니다.

### 4. Transfer Rate
- 전송 속도(Kbytes/sec) 역시 동시 접속자 수가 증가함에 따라 증가하여, 동시 접속자 수가 1,000명일 때 최고 294.62 Kbytes/sec를 기록하였습니다.
- 이는 서버가 동시 요청 수가 증가할수록 더 많은 데이터를 전송할 수 있음을 나타냅니다.


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

- 서버는 동시 접속자 수 1,000명까지 안정적인 성능을 보여주며, 초당 요청 수(RPS)가 꾸준히 증가했습니다.
- 동시 접속자 수가 1,000명일 때 가장 높은 처리량인 1,795.78 RPS를 기록했지만, 응답 시간이 증가하는 경향을 보였습니다.
- 이 결과는 서버가 높은 동시 요청을 효과적으로 처리할 수 있음을 나타내지만, 동시 접속자 수가 증가할수록 응답 시간이 늘어날 수 있음을 보여줍니다.

## Recommendations

- **Optimize Resource Allocation**: 서버의 자원(CPU, 메모리) 할당을 최적화하여 더 높은 동시 접속자 수를 효과적으로 처리할 수 있도록 설정을 조정해보세요.
- **Implement Load Balancing**: 더 높은 동시 접속자 수를 처리하려면, 로드 밸런서를 사용하여 여러 서버에 요청을 분산시키는 것을 고려해보세요.
- **Monitor and Tune Application Performance**: 애플리케이션의 성능 병목 현상을 파악하고, 응답 시간을 줄이고 처리량을 증가시키기 위한 최적화를 수행하세요.
