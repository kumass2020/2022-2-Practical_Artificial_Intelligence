# 220922 인공지능응용 과제

Created: 2022년 9월 22일 오전 8:15
Last Edited Time: 2022년 9월 22일 오전 10:05

## Week-3 실습 내용

### Centralized Learning

로컬 학습을 수행하였음.

Dataset: CIFAR-10

실행 결과:

```
/Users/hoho/opt/anaconda3/envs/test_fed/bin/python /Users/hoho/PycharmProjects/pythonProject/Centralized_to_Federated/centralized.py 
Centralized PyTorch training
Load data
Files already downloaded and verified
Files already downloaded and verified
Start training
Training 2 epoch(s) w/ 1563 batches each
[1,   100] loss: 0.115
[1,   200] loss: 0.115
[1,   300] loss: 0.115
[1,   400] loss: 0.115
[1,   500] loss: 0.115
[1,   600] loss: 0.115
[1,   700] loss: 0.114
[1,   800] loss: 0.114
[1,   900] loss: 0.113
[1,  1000] loss: 0.111
[1,  1100] loss: 0.109
[1,  1200] loss: 0.107
[1,  1300] loss: 0.105
[1,  1400] loss: 0.104
[1,  1500] loss: 0.103
[2,   100] loss: 0.101
[2,   200] loss: 0.101
[2,   300] loss: 0.099
[2,   400] loss: 0.097
[2,   500] loss: 0.097
[2,   600] loss: 0.096
[2,   700] loss: 0.094
[2,   800] loss: 0.094
[2,   900] loss: 0.092
[2,  1000] loss: 0.088
[2,  1100] loss: 0.087
[2,  1200] loss: 0.087
[2,  1300] loss: 0.085
[2,  1400] loss: 0.084
[2,  1500] loss: 0.086
Evaluate model
Loss:  517.412575006485
Accuracy:  0.3851

Process finished with exit code 0
```

### Federated Learning

1개의 서버와 2개의 클라이언트를 실행해 연합학습을 수행

Dataset: CIFAR-10

server 실행 결과:

```
(test_fed) hoho@hohos-MacBookPro Centralized_to_Federated % python server.py 
INFO flower 2022-09-22 08:33:38,039 | app.py:119 | Starting Flower server, config: ServerConfig(num_rounds=3, round_timeout=None)
INFO flower 2022-09-22 08:33:38,049 | app.py:132 | Flower ECE: gRPC server running (3 rounds), SSL is disabled
INFO flower 2022-09-22 08:33:38,049 | server.py:86 | Initializing global parameters
INFO flower 2022-09-22 08:33:38,049 | server.py:270 | Requesting initial parameters from one random client
INFO flower 2022-09-22 08:33:51,076 | server.py:274 | Received initial parameters from one random client
INFO flower 2022-09-22 08:33:51,076 | server.py:88 | Evaluating initial parameters
INFO flower 2022-09-22 08:33:51,076 | server.py:101 | FL starting
DEBUG flower 2022-09-22 08:33:54,500 | server.py:215 | fit_round 1: strategy sampled 2 clients (out of 2)
DEBUG flower 2022-09-22 08:34:18,146 | server.py:229 | fit_round 1 received 2 results and 0 failures
WARNING flower 2022-09-22 08:34:18,176 | fedavg.py:243 | No fit_metrics_aggregation_fn provided
DEBUG flower 2022-09-22 08:34:18,179 | server.py:165 | evaluate_round 1: strategy sampled 2 clients (out of 2)
DEBUG flower 2022-09-22 08:34:23,884 | server.py:179 | evaluate_round 1 received 2 results and 0 failures
DEBUG flower 2022-09-22 08:34:23,885 | server.py:215 | fit_round 2: strategy sampled 2 clients (out of 2)
DEBUG flower 2022-09-22 08:34:45,506 | server.py:229 | fit_round 2 received 2 results and 0 failures
DEBUG flower 2022-09-22 08:34:45,517 | server.py:165 | evaluate_round 2: strategy sampled 2 clients (out of 2)
DEBUG flower 2022-09-22 08:34:51,080 | server.py:179 | evaluate_round 2 received 2 results and 0 failures
DEBUG flower 2022-09-22 08:34:51,081 | server.py:215 | fit_round 3: strategy sampled 2 clients (out of 2)
DEBUG flower 2022-09-22 08:35:13,624 | server.py:229 | fit_round 3 received 2 results and 0 failures
DEBUG flower 2022-09-22 08:35:13,634 | server.py:165 | evaluate_round 3: strategy sampled 2 clients (out of 2)
DEBUG flower 2022-09-22 08:35:19,649 | server.py:179 | evaluate_round 3 received 2 results and 0 failures
INFO flower 2022-09-22 08:35:19,649 | server.py:144 | FL finished in 88.57333987499999
INFO flower 2022-09-22 08:35:19,654 | app.py:180 | app_fit: losses_distributed [(1, 2.0815765857696533), (2, 1.807611346244812), (3, 1.5555431842803955)]
INFO flower 2022-09-22 08:35:19,654 | app.py:181 | app_fit: metrics_distributed {'accuracy': [(1, 0.2429), (2, 0.3454), (3, 0.4338)]}
INFO flower 2022-09-22 08:35:19,654 | app.py:182 | app_fit: losses_centralized []
INFO flower 2022-09-22 08:35:19,654 | app.py:183 | app_fit: metrics_centralized {}
```

client 실행 결과:

```
(test_fed) hoho@hohos-MacBookPro Centralized_to_Federated % python client.py 
Files already downloaded and verified
Files already downloaded and verified
INFO flower 2022-09-22 08:33:51,060 | connection.py:102 | Opened insecure gRPC connection (no certificates were passed)
DEBUG flower 2022-09-22 08:33:51,061 | connection.py:39 | ChannelConnectivity.IDLE
DEBUG flower 2022-09-22 08:33:51,062 | connection.py:39 | ChannelConnectivity.CONNECTING
DEBUG flower 2022-09-22 08:33:51,063 | connection.py:39 | ChannelConnectivity.READY
100%|███████████████████████████████████████████████████████████████████████████████████████████████| 1563/1563 [00:23<00:00, 67.78it/s]
100%|███████████████████████████████████████████████████████████████████████████████████████████| 10000/10000 [00:05<00:00, 1785.61it/s]
100%|███████████████████████████████████████████████████████████████████████████████████████████████| 1563/1563 [00:21<00:00, 73.25it/s]
100%|███████████████████████████████████████████████████████████████████████████████████████████| 10000/10000 [00:05<00:00, 1799.83it/s]
100%|███████████████████████████████████████████████████████████████████████████████████████████████| 1563/1563 [00:22<00:00, 69.37it/s]
100%|███████████████████████████████████████████████████████████████████████████████████████████| 10000/10000 [00:05<00:00, 1668.50it/s]
DEBUG flower 2022-09-22 08:35:19,660 | connection.py:121 | gRPC channel closed
INFO flower 2022-09-22 08:35:19,660 | app.py:149 | Disconnect and shut down
```

### Federated Learning - Realistic heterogeneous case

1개의 서버와 9개의 client로 구성하였음.

Dataset: FEMNIST

server 실행 결과:

```
/Users/hoho/opt/anaconda3/envs/test_fed/bin/python /Users/hoho/PycharmProjects/pythonProject/Femnist/server.py 
INFO flower 2022-09-22 08:44:37,295 | app.py:119 | Starting Flower server, config: ServerConfig(num_rounds=1000, round_timeout=None)
INFO flower 2022-09-22 08:44:37,314 | app.py:132 | Flower ECE: gRPC server running (1000 rounds), SSL is disabled
INFO flower 2022-09-22 08:44:37,314 | server.py:86 | Initializing global parameters
INFO flower 2022-09-22 08:44:37,314 | server.py:270 | Requesting initial parameters from one random client
INFO flower 2022-09-22 08:44:44,346 | server.py:274 | Received initial parameters from one random client
INFO flower 2022-09-22 08:44:44,347 | server.py:88 | Evaluating initial parameters
INFO flower 2022-09-22 08:44:44,347 | server.py:101 | FL starting
DEBUG flower 2022-09-22 08:44:44,348 | server.py:215 | fit_round 1: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:45:11,620 | server.py:229 | fit_round 1 received 9 results and 0 failures
WARNING flower 2022-09-22 08:45:12,125 | fedavg.py:243 | No fit_metrics_aggregation_fn provided
DEBUG flower 2022-09-22 08:45:12,132 | server.py:165 | evaluate_round 1: strategy sampled 9 clients (out of 9)
accuracy : 0.05555555555555555
DEBUG flower 2022-09-22 08:45:21,878 | server.py:179 | evaluate_round 1 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:45:21,880 | server.py:215 | fit_round 2: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:45:45,138 | server.py:229 | fit_round 2 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:45:45,447 | server.py:165 | evaluate_round 2: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:45:52,280 | server.py:179 | evaluate_round 2 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:45:52,281 | server.py:215 | fit_round 3: strategy sampled 9 clients (out of 9)
accuracy : 0.06358381502890173
DEBUG flower 2022-09-22 08:46:24,235 | server.py:229 | fit_round 3 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:46:24,733 | server.py:165 | evaluate_round 3: strategy sampled 9 clients (out of 9)
accuracy : 0.05365853658536585
DEBUG flower 2022-09-22 08:46:34,819 | server.py:179 | evaluate_round 3 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:46:34,820 | server.py:215 | fit_round 4: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:46:58,886 | server.py:229 | fit_round 4 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:46:59,167 | server.py:165 | evaluate_round 4: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:47:07,645 | server.py:179 | evaluate_round 4 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:47:07,646 | server.py:215 | fit_round 5: strategy sampled 9 clients (out of 9)
accuracy : 0.05027932960893855
DEBUG flower 2022-09-22 08:47:38,902 | server.py:229 | fit_round 5 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:47:39,296 | server.py:165 | evaluate_round 5: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:47:48,544 | server.py:179 | evaluate_round 5 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:47:48,545 | server.py:215 | fit_round 6: strategy sampled 9 clients (out of 9)
accuracy : 0.043478260869565216
DEBUG flower 2022-09-22 08:48:13,918 | server.py:229 | fit_round 6 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:48:14,363 | server.py:165 | evaluate_round 6: strategy sampled 9 clients (out of 9)
accuracy : 0.04371584699453552
DEBUG flower 2022-09-22 08:48:24,483 | server.py:179 | evaluate_round 6 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:48:24,485 | server.py:215 | fit_round 7: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:48:47,795 | server.py:229 | fit_round 7 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:48:48,246 | server.py:165 | evaluate_round 7: strategy sampled 9 clients (out of 9)
accuracy : 0.05092592592592592
DEBUG flower 2022-09-22 08:48:59,994 | server.py:179 | evaluate_round 7 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:48:59,995 | server.py:215 | fit_round 8: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:49:27,169 | server.py:229 | fit_round 8 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:49:27,632 | server.py:165 | evaluate_round 8: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:49:39,012 | server.py:179 | evaluate_round 8 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:49:39,013 | server.py:215 | fit_round 9: strategy sampled 9 clients (out of 9)
accuracy : 0.04568527918781726
DEBUG flower 2022-09-22 08:50:10,282 | server.py:229 | fit_round 9 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:50:10,666 | server.py:165 | evaluate_round 9: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:50:19,121 | server.py:179 | evaluate_round 9 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:50:19,122 | server.py:215 | fit_round 10: strategy sampled 9 clients (out of 9)
accuracy : 0.0594059405940594
DEBUG flower 2022-09-22 08:50:46,247 | server.py:229 | fit_round 10 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:50:46,586 | server.py:165 | evaluate_round 10: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:50:56,296 | server.py:179 | evaluate_round 10 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:50:56,297 | server.py:215 | fit_round 11: strategy sampled 9 clients (out of 9)
accuracy : 0.06
DEBUG flower 2022-09-22 08:51:30,243 | server.py:229 | fit_round 11 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:51:30,639 | server.py:165 | evaluate_round 11: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:51:40,657 | server.py:179 | evaluate_round 11 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:51:40,661 | server.py:215 | fit_round 12: strategy sampled 9 clients (out of 9)
accuracy : 0.06808510638297872
DEBUG flower 2022-09-22 08:52:10,823 | server.py:229 | fit_round 12 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:52:11,150 | server.py:165 | evaluate_round 12: strategy sampled 9 clients (out of 9)
accuracy : 0.04455445544554455
DEBUG flower 2022-09-22 08:52:21,769 | server.py:179 | evaluate_round 12 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:52:21,770 | server.py:215 | fit_round 13: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:52:49,961 | server.py:229 | fit_round 13 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:52:50,304 | server.py:165 | evaluate_round 13: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:53:02,525 | server.py:179 | evaluate_round 13 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:53:02,525 | server.py:215 | fit_round 14: strategy sampled 9 clients (out of 9)
accuracy : 0.05976095617529881
DEBUG flower 2022-09-22 08:53:26,321 | server.py:229 | fit_round 14 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:53:26,679 | server.py:165 | evaluate_round 14: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:53:33,571 | server.py:179 | evaluate_round 14 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:53:33,571 | server.py:215 | fit_round 15: strategy sampled 9 clients (out of 9)
accuracy : 0.08441558441558442
DEBUG flower 2022-09-22 08:53:55,022 | server.py:229 | fit_round 15 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:53:55,396 | server.py:165 | evaluate_round 15: strategy sampled 9 clients (out of 9)
accuracy : 0.09316770186335403
DEBUG flower 2022-09-22 08:54:03,781 | server.py:179 | evaluate_round 15 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:54:03,784 | server.py:215 | fit_round 16: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:54:31,759 | server.py:229 | fit_round 16 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:54:32,100 | server.py:165 | evaluate_round 16: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:54:45,032 | server.py:179 | evaluate_round 16 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:54:45,037 | server.py:215 | fit_round 17: strategy sampled 9 clients (out of 9)
accuracy : 0.055793991416309016
DEBUG flower 2022-09-22 08:55:16,324 | server.py:229 | fit_round 17 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:55:19,548 | server.py:165 | evaluate_round 17: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 08:56:14,565 | server.py:179 | evaluate_round 17 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:56:14,583 | server.py:215 | fit_round 18: strategy sampled 9 clients (out of 9)
accuracy : 0.046153846153846156
DEBUG flower 2022-09-22 08:56:41,670 | server.py:229 | fit_round 18 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:56:42,558 | server.py:165 | evaluate_round 18: strategy sampled 9 clients (out of 9)
accuracy : 0.08653846153846154
DEBUG flower 2022-09-22 08:56:50,933 | server.py:179 | evaluate_round 18 received 9 results and 0 failures
DEBUG flower 2022-09-22 08:56:50,933 | server.py:215 | fit_round 19: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 09:04:33,064 | server.py:229 | fit_round 19 received 9 results and 0 failures
DEBUG flower 2022-09-22 09:04:35,130 | server.py:165 | evaluate_round 19: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 09:04:47,255 | server.py:179 | evaluate_round 19 received 9 results and 0 failures
DEBUG flower 2022-09-22 09:04:47,257 | server.py:215 | fit_round 20: strategy sampled 9 clients (out of 9)
accuracy : 0.062146892655367235
DEBUG flower 2022-09-22 09:37:17,466 | server.py:229 | fit_round 20 received 9 results and 0 failures
DEBUG flower 2022-09-22 09:37:18,647 | server.py:165 | evaluate_round 20: strategy sampled 9 clients (out of 9)
accuracy : 0.05454545454545454
DEBUG flower 2022-09-22 09:40:51,396 | server.py:179 | evaluate_round 20 received 9 results and 0 failures
DEBUG flower 2022-09-22 09:40:51,424 | server.py:215 | fit_round 21: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 09:43:33,052 | server.py:229 | fit_round 21 received 9 results and 0 failures
DEBUG flower 2022-09-22 09:43:33,986 | server.py:165 | evaluate_round 21: strategy sampled 9 clients (out of 9)
DEBUG flower 2022-09-22 09:53:12,840 | server.py:179 | evaluate_round 21 received 9 results and 0 failures
DEBUG flower 2022-09-22 09:53:12,863 | server.py:215 | fit_round 22: strategy sampled 9 clients (out of 9)
accuracy : 0.04310344827586207
Traceback (most recent call last):
  File "/Users/hoho/PycharmProjects/pythonProject/Femnist/server.py", line 28, in <module>
    fl.server.start_server(
  File "/Users/hoho/opt/anaconda3/envs/test_fed/lib/python3.8/site-packages/flwr/server/app.py", line 140, in start_server
    hist = _fl(
  File "/Users/hoho/opt/anaconda3/envs/test_fed/lib/python3.8/site-packages/flwr/server/app.py", line 179, in _fl
    hist = server.fit(num_rounds=config.num_rounds, timeout=config.round_timeout)
  File "/Users/hoho/opt/anaconda3/envs/test_fed/lib/python3.8/site-packages/flwr/server/server.py", line 106, in fit
    res_fit = self.fit_round(server_round=current_round, timeout=timeout)
  File "/Users/hoho/opt/anaconda3/envs/test_fed/lib/python3.8/site-packages/flwr/server/server.py", line 224, in fit_round
    results, failures = fit_clients(
  File "/Users/hoho/opt/anaconda3/envs/test_fed/lib/python3.8/site-packages/flwr/server/server.py", line 331, in fit_clients
    finished_fs, _ = concurrent.futures.wait(
  File "/Users/hoho/opt/anaconda3/envs/test_fed/lib/python3.8/concurrent/futures/_base.py", line 305, in wait
    waiter.event.wait(timeout)
  File "/Users/hoho/opt/anaconda3/envs/test_fed/lib/python3.8/threading.py", line 558, in wait
    signaled = self._cond.wait(timeout)
  File "/Users/hoho/opt/anaconda3/envs/test_fed/lib/python3.8/threading.py", line 302, in wait
    waiter.acquire()
KeyboardInterrupt

Process finished with exit code 130 (interrupted by signal 2: SIGINT)
```

client 실행 결과:

```
/Users/hoho/opt/anaconda3/envs/test_fed/bin/python /Users/hoho/PycharmProjects/pythonProject/Femnist/client.py 
INFO flower 2022-09-22 08:44:44,204 | connection.py:102 | Opened insecure gRPC connection (no certificates were passed)
INFO flower 2022-09-22 08:44:44,205 | connection.py:102 | Opened insecure gRPC connection (no certificates were passed)
INFO flower 2022-09-22 08:44:44,205 | connection.py:102 | Opened insecure gRPC connection (no certificates were passed)
INFO flower 2022-09-22 08:44:44,205 | connection.py:102 | Opened insecure gRPC connection (no certificates were passed)
INFO flower 2022-09-22 08:44:44,205 | connection.py:102 | Opened insecure gRPC connection (no certificates were passed)
INFO flower 2022-09-22 08:44:44,205 | connection.py:102 | Opened insecure gRPC connection (no certificates were passed)
INFO flower 2022-09-22 08:44:44,205 | connection.py:102 | Opened insecure gRPC connection (no certificates were passed)
DEBUG flower 2022-09-22 08:44:44,206 | connection.py:39 | ChannelConnectivity.IDLE
DEBUG flower 2022-09-22 08:44:44,206 | connection.py:39 | ChannelConnectivity.IDLE
DEBUG flower 2022-09-22 08:44:44,206 | connection.py:39 | ChannelConnectivity.IDLE
DEBUG flower 2022-09-22 08:44:44,206 | connection.py:39 | ChannelConnectivity.IDLE
DEBUG flower 2022-09-22 08:44:44,206 | connection.py:39 | ChannelConnectivity.IDLE
DEBUG flower 2022-09-22 08:44:44,206 | connection.py:39 | ChannelConnectivity.IDLE
DEBUG flower 2022-09-22 08:44:44,206 | connection.py:39 | ChannelConnectivity.IDLE
DEBUG flower 2022-09-22 08:44:44,207 | connection.py:39 | ChannelConnectivity.CONNECTING
DEBUG flower 2022-09-22 08:44:44,208 | connection.py:39 | ChannelConnectivity.CONNECTING
DEBUG flower 2022-09-22 08:44:44,208 | connection.py:39 | ChannelConnectivity.CONNECTING
DEBUG flower 2022-09-22 08:44:44,209 | connection.py:39 | ChannelConnectivity.CONNECTING
DEBUG flower 2022-09-22 08:44:44,209 | connection.py:39 | ChannelConnectivity.CONNECTING
DEBUG flower 2022-09-22 08:44:44,209 | connection.py:39 | ChannelConnectivity.CONNECTING
DEBUG flower 2022-09-22 08:44:44,211 | connection.py:39 | ChannelConnectivity.CONNECTING
INFO flower 2022-09-22 08:44:44,223 | connection.py:102 | Opened insecure gRPC connection (no certificates were passed)
DEBUG flower 2022-09-22 08:44:44,224 | connection.py:39 | ChannelConnectivity.IDLE
DEBUG flower 2022-09-22 08:44:44,224 | connection.py:39 | ChannelConnectivity.CONNECTING
DEBUG flower 2022-09-22 08:44:44,239 | connection.py:39 | ChannelConnectivity.READY
DEBUG flower 2022-09-22 08:44:44,239 | connection.py:39 | ChannelConnectivity.READY
DEBUG flower 2022-09-22 08:44:44,239 | connection.py:39 | ChannelConnectivity.READY
DEBUG flower 2022-09-22 08:44:44,239 | connection.py:39 | ChannelConnectivity.READY
DEBUG flower 2022-09-22 08:44:44,239 | connection.py:39 | ChannelConnectivity.READY
DEBUG flower 2022-09-22 08:44:44,239 | connection.py:39 | ChannelConnectivity.READY
DEBUG flower 2022-09-22 08:44:44,239 | connection.py:39 | ChannelConnectivity.READY
DEBUG flower 2022-09-22 08:44:44,239 | connection.py:39 | ChannelConnectivity.READY
INFO flower 2022-09-22 08:44:44,251 | connection.py:102 | Opened insecure gRPC connection (no certificates were passed)
DEBUG flower 2022-09-22 08:44:44,252 | connection.py:39 | ChannelConnectivity.IDLE
DEBUG flower 2022-09-22 08:44:44,253 | connection.py:39 | ChannelConnectivity.CONNECTING
DEBUG flower 2022-09-22 08:44:44,270 | connection.py:39 | ChannelConnectivity.READY
number : 33, subject number : 66
number : 30, subject number : 17
number : 6, subject number : 95
number : 10, subject number : 92
number : 19, subject number : 36
number : 20, subject number : 68
number : 25, subject number : 68
number : 35, subject number : 96
number : 25, subject number : 21
number : 13, subject number : 33
number : 24, subject number : 31
number : 16, subject number : 62
number : 31, subject number : 95
number : 35, subject number : 20
number : 29, subject number : 16
number : 12, subject number : 62
number : 9, subject number : 72
number : 19, subject number : 29
number : 22, subject number : 42
number : 10, subject number : 57
number : 1, subject number : 46
number : 32, subject number : 96
number : 28, subject number : 21
number : 19, subject number : 67
number : 14, subject number : 18number : 17, subject number : 22

number : 16, subject number : 54
number : 31, subject number : 86
number : 22, subject number : 41
number : 34, subject number : 8
number : 34, subject number : 0
number : 14, subject number : 21
number : 14, subject number : 10
number : 27, subject number : 73
number : 24, subject number : 45
number : 10, subject number : 74
number : 18, subject number : 26
number : 6, subject number : 32
number : 1, subject number : 25
number : 32, subject number : 25
number : 4, subject number : 34
number : 9, subject number : 90
number : 25, subject number : 57
number : 3, subject number : 30
number : 13, subject number : 73
number : 3, subject number : 90
number : 30, subject number : 2
number : 31, subject number : 74
number : 9, subject number : 69
number : 34, subject number : 99
number : 16, subject number : 4
number : 21, subject number : 64
number : 10, subject number : 54
number : 19, subject number : 47
number : 4, subject number : 27
number : 22, subject number : 31
number : 33, subject number : 56
number : 33, subject number : 84
number : 4, subject number : 11
number : 10, subject number : 39
number : 26, subject number : 13
number : 20, subject number : 7
number : 10, subject number : 68
number : 18, subject number : 85
number : 21, subject number : 12
number : 23, subject number : 74
number : 15, subject number : 44
number : 8, subject number : 72
number : 27, subject number : 96
number : 25, subject number : 1
number : 24, subject number : 40
number : 16, subject number : 10
number : 17, subject number : 23
number : 9, subject number : 29
number : 17, subject number : 55
number : 4, subject number : 57
number : 2, subject number : 77
number : 34, subject number : 83
number : 31, subject number : 27
number : 5, subject number : 11
number : 14, subject number : 71
number : 13, subject number : 98
number : 16, subject number : 84
number : 4, subject number : 52
number : 5, subject number : 48
number : 21, subject number : 25
number : 30, subject number : 15
number : 12, subject number : 59
number : 25, subject number : 22
number : 9, subject number : 9
number : 24, subject number : 59
number : 1, subject number : 18
number : 2, subject number : 80
number : 31, subject number : 35
number : 27, subject number : 77
number : 10, subject number : 96
number : 33, subject number : 43
number : 24, subject number : 13
number : 34, subject number : 41
number : 28, subject number : 14
number : 7, subject number : 82
number : 16, subject number : 34
number : 26, subject number : 66
number : 34, subject number : 17
number : 24, subject number : 88
number : 17, subject number : 95
number : 9, subject number : 55
number : 5, subject number : 15
number : 23, subject number : 44
number : 29, subject number : 68
number : 20, subject number : 97
number : 35, subject number : 4
number : 29, subject number : 23
number : 15, subject number : 14
number : 8, subject number : 7
number : 15, subject number : 97
number : 18, subject number : 0
number : 1, subject number : 93
number : 15, subject number : 50
number : 6, subject number : 34
number : 14, subject number : 30
number : 31, subject number : 80
number : 8, subject number : 56
number : 19, subject number : 49
number : 23, subject number : 29
number : 9, subject number : 99
number : 1, subject number : 80
number : 15, subject number : 0
number : 31, subject number : 47
number : 13, subject number : 77
number : 4, subject number : 50
number : 34, subject number : 83
number : 17, subject number : 31
number : 15, subject number : 42
number : 18, subject number : 25
number : 32, subject number : 55
number : 2, subject number : 4
number : 27, subject number : 33
number : 11, subject number : 81
number : 13, subject number : 96
number : 31, subject number : 85
number : 0, subject number : 4
number : 17, subject number : 22
number : 27, subject number : 92
number : 4, subject number : 98
number : 30, subject number : 31
number : 10, subject number : 0
number : 30, subject number : 88
number : 22, subject number : 91
number : 14, subject number : 62
number : 10, subject number : 4
number : 7, subject number : 70
number : 24, subject number : 2
number : 31, subject number : 59
number : 21, subject number : 1
number : 29, subject number : 62
number : 0, subject number : 18
number : 10, subject number : 76
number : 17, subject number : 88
number : 34, subject number : 14
number : 29, subject number : 87
number : 0, subject number : 2
number : 8, subject number : 91
number : 1, subject number : 6
number : 32, subject number : 45
number : 26, subject number : 11
number : 34, subject number : 13
number : 19, subject number : 7
number : 2, subject number : 57
number : 0, subject number : 30
number : 32, subject number : 20
number : 16, subject number : 18
number : 25, subject number : 0
number : 32, subject number : 40
number : 22, subject number : 85
number : 18, subject number : 19
number : 16, subject number : 78
number : 4, subject number : 71
number : 15, subject number : 56
number : 0, subject number : 83
number : 6, subject number : 53
number : 3, subject number : 53
number : 0, subject number : 89
number : 20, subject number : 63
number : 35, subject number : 9
number : 3, subject number : 3
number : 23, subject number : 70
number : 14, subject number : 55
number : 25, subject number : 59
number : 9, subject number : 78
number : 4, subject number : 95
number : 5, subject number : 93
number : 8, subject number : 93
number : 33, subject number : 14
number : 2, subject number : 0
number : 18, subject number : 80
number : 24, subject number : 1
number : 27, subject number : 76
number : 6, subject number : 50
number : 1, subject number : 16
number : 5, subject number : 14
number : 29, subject number : 64
number : 4, subject number : 84
number : 26, subject number : 32
number : 32, subject number : 87
number : 7, subject number : 78
number : 6, subject number : 15
number : 20, subject number : 60
number : 0, subject number : 55
number : 23, subject number : 18
number : 33, subject number : 80
number : 3, subject number : 43
number : 30, subject number : 84
number : 0, subject number : 73
number : 22, subject number : 56
number : 11, subject number : 16
number : 0, subject number : 37
number : 26, subject number : 30
number : 15, subject number : 17
number : 14, subject number : 43
number : 19, subject number : 69
number : 2, subject number : 18
number : 31, subject number : 83
number : 1, subject number : 60
number : 26, subject number : 29
number : 23, subject number : 98
number : 3, subject number : 94
number : 33, subject number : 9
number : 13, subject number : 8
number : 8, subject number : 31
number : 4, subject number : 55
number : 34, subject number : 57
number : 6, subject number : 37number : 11, subject number : 20

number : 12, subject number : 26
number : 29, subject number : 13
number : 18, subject number : 60
number : 14, subject number : 22
number : 31, subject number : 55
number : 10, subject number : 59
number : 32, subject number : 67
number : 34, subject number : 37
number : 10, subject number : 77
number : 18, subject number : 73
number : 11, subject number : 63
number : 35, subject number : 22
number : 33, subject number : 53
number : 19, subject number : 54
number : 34, subject number : 22
number : 23, subject number : 8
number : 35, subject number : 9
number : 27, subject number : 81
number : 22, subject number : 82
number : 35, subject number : 82
number : 19, subject number : 25
number : 35, subject number : 13
number : 19, subject number : 52
number : 24, subject number : 39
number : 13, subject number : 78
number : 22, subject number : 32
number : 28, subject number : 30
number : 18, subject number : 19
number : 18, subject number : 85
number : 18, subject number : 30
number : 30, subject number : 82
number : 35, subject number : 23
number : 17, subject number : 21
number : 32, subject number : 50
number : 12, subject number : 21
number : 22, subject number : 77
number : 35, subject number : 4
number : 26, subject number : 43
number : 24, subject number : 73
number : 5, subject number : 83
number : 34, subject number : 54
number : 4, subject number : 5
number : 28, subject number : 0
number : 9, subject number : 5
number : 29, subject number : 67
number : 0, subject number : 9
number : 4, subject number : 66
number : 35, subject number : 73
number : 18, subject number : 74
number : 8, subject number : 2
number : 3, subject number : 43
number : 17, subject number : 8
number : 3, subject number : 58
number : 6, subject number : 31
number : 25, subject number : 97
number : 16, subject number : 61
number : 5, subject number : 69
number : 4, subject number : 53
number : 31, subject number : 9
number : 12, subject number : 87
number : 4, subject number : 44
number : 16, subject number : 34
number : 18, subject number : 57
number : 30, subject number : 51
number : 6, subject number : 67
number : 10, subject number : 54
number : 26, subject number : 38
number : 20, subject number : 24
number : 22, subject number : 82
number : 26, subject number : 43
number : 1, subject number : 14
number : 31, subject number : 69
number : 23, subject number : 4
number : 30, subject number : 98
number : 22, subject number : 38
number : 1, subject number : 2
number : 13, subject number : 32
number : 5, subject number : 62
number : 13, subject number : 69
number : 21, subject number : 15
number : 10, subject number : 68
number : 25, subject number : 21
number : 18, subject number : 93
number : 6, subject number : 77
number : 0, subject number : 43
number : 19, subject number : 83
number : 17, subject number : 14
number : 26, subject number : 51
number : 25, subject number : 59
number : 10, subject number : 49
number : 7, subject number : 14
number : 31, subject number : 73
number : 35, subject number : 41
number : 23, subject number : 82
number : 13, subject number : 73
number : 34, subject number : 17
number : 14, subject number : 3
number : 6, subject number : 18
number : 16, subject number : 48
number : 24, subject number : 41
number : 22, subject number : 60
number : 15, subject number : 61
number : 17, subject number : 55
number : 10, subject number : 83
number : 17, subject number : 75
number : 22, subject number : 27
number : 5, subject number : 24
number : 16, subject number : 78
number : 26, subject number : 79
number : 21, subject number : 6
number : 18, subject number : 41
number : 27, subject number : 6
number : 0, subject number : 6
number : 32, subject number : 56
number : 27, subject number : 15
number : 7, subject number : 15
number : 33, subject number : 73
number : 31, subject number : 8
number : 27, subject number : 24
number : 5, subject number : 35
number : 4, subject number : 58
number : 33, subject number : 46
number : 3, subject number : 36
number : 4, subject number : 49
number : 30, subject number : 23
number : 32, subject number : 17
number : 29, subject number : 12
number : 19, subject number : 97
number : 34, subject number : 29
number : 34, subject number : 48
number : 15, subject number : 87
number : 22, subject number : 24
number : 0, subject number : 95
number : 26, subject number : 14
number : 3, subject number : 49
number : 34, subject number : 86
number : 4, subject number : 18
number : 9, subject number : 29
number : 9, subject number : 56
number : 34, subject number : 93
number : 29, subject number : 11
number : 17, subject number : 75
number : 5, subject number : 0
number : 13, subject number : 57
number : 3, subject number : 76number : 11, subject number : 58
number : 5, subject number : 17number : 19, subject number : 73

number : 0, subject number : 7
number : 17, subject number : 23
number : 33, subject number : 53
number : 20, subject number : 7
number : 13, subject number : 49
DEBUG flower 2022-09-22 09:54:00,719 | connection.py:121 | gRPC channel closed
DEBUG flower 2022-09-22 09:54:00,711 | connection.py:121 | gRPC channel closed
```

## + alpha

### M1 Mac FL 환경 설정

M1 프로세서를 사용하는 MAC은 FL 환경 설정에 있어서 오류 발생

- flower 설치 중 grpcio 설치 오류 시
    
    다음 명령어를 입력.
    
    ```bash
    export GRPC_PYTHON_BUILD_SYSTEM_OPENSSL=1
    export GRPC_PYTHON_BUILD_SYSTEM_ZLIB=1
    ```
    
- 위 실행에도 불구하고 Anaconda 환경에서 오류 시
    
    ```bash
    pip uninstall grpcio
    conda install grpcio
    ```
    
-