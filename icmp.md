# ICMP

## ICMP Unreachable Error Messages

Type 3 error messages are sent when a message cannot be delivered completely to the application at a destination host. Six codes contained in the ICMP header describe the unreachable condition as follows:

- 0—Network unreachable
- 1—Host unreachable
- 2—Protocol unreachable
- 3—Port unreachable
- 4—Fragmentation needed and the “don’t fragment�? (DF) bit is set
- 5—Source route failed
  
Cisco IOS XE software can suppress the generation of ICMP unreachable destination error messages, which is called rate-limiting. The default is no unreachable messages more often than once every half second. Separate intervals can be configured for code 4 and all other unreachable destination error messages. However, there is no method of displaying how many ICMP messages have not been sent.

```
ip icmp rate-limit unreachable 500
```

![image](https://github.com/phph9/Foundation/assets/116812447/b3cd1bce-c83a-42ac-9bf8-68672020549c)
