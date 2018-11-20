## 1) TCP connection
iperf3 -s    //server side
iperf3 -c <server_address> -f -m //client side -m (Mbps)
iperf3 -c <server_address> -P 8 -t 30


## 2) UDP connection
iperf3 -s 
iperf3 -c <server_address> -u

## 3) Reverse mode connection
iperf3 -c <remotehost> -R   //TCP test Reverse mode (server sends, client receives)

## 4) UDP testing
iperf3 -c <remotehost> -u  -b 6MB    //video traffic (run 6 Mbps UDP test to server)

## 5) Multiple streams test from a single client to multiple servers 
iperf3 -c remotehost1 -T s1 & iperf3 -c remotehost2 -T s2

## 6) Multiple clients to a server
   * Server:
     iperf3 -s -p 5000 & iperf3 -s -p 5001

   * Client A:
     iperf3 -c remotehost1 -p 5000

   * Client B:
     iperf3 -c remotehost2 -p 5001