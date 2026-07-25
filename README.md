# Packet Tracer - Connect to a Web Server

## Objective

Observe how packets are sent across the Internet using IP addresses, by verifying connectivity to a web server and then connecting to it through a web client.

## Topology Summary

- **PC0**: source host
- **Web Server**: `172.33.100.50`

## Part 1: Verify Connectivity to the Web Server

From PC0's command prompt, connectivity was tested using:

```
PC> ping 172.33.100.50
```

**Result:**

```
Pinging 172.33.100.50 with 32 bytes of data:

Request timed out.
Reply from 172.33.100.50: bytes=32 time<1ms TTL=127
Reply from 172.33.100.50: bytes=32 time<1ms TTL=127
Reply from 172.33.100.50: bytes=32 time<1ms TTL=127

Ping statistics for 172.33.100.50:
    Packets: Sent = 4, Received = 3, Lost = 1 (25% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```

![Ping result](ping-result.jpeg)

The first ping request timed out because ARP had to resolve the destination's MAC address before the ICMP request could actually be delivered. Once ARP completed, the remaining three requests succeeded, confirming Layer 3 connectivity between PC0 and the web server.

## Part 2: Connect to the Web Server via the Web Client

On PC0's Desktop tab, the Web Browser app was opened and `172.33.100.50` was entered into the URL field.

![Web browser result](web-browser-result.png)

The browser successfully loaded the page titled "Welcome to the Learn IP Web Site," confirming that PC0 was able to reach the server, and that the server had a working web service (HTTP) responding to the request.

## Reflection Question

**What messages did you see after the web page had finished loading?**

The page displayed a welcome message confirming the connection: "You were able to reach this website because you had the IP address of the web server. The connecting PC also had a web client running on the device." This confirms that a successful HTTP connection depends on two things: the client knowing the correct destination IP address, and the client having a web browser (HTTP client) capable of sending the request and rendering the response.

## Key Takeaways

- Ping verifies basic IP reachability (Layer 3) before attempting any application-layer connection.
- An initial "Request timed out" on the first ping is normal and is usually caused by ARP resolution delay, not an actual connectivity failure.
- A functioning HTTP connection requires both a reachable IP address and a running web client/server pair.
