alert tcp 192.168.20.0/24 any -> 192.168.10.0/24 22 (msg:"DMZ host attempting SSH into internal segment"; flags:S; sid:1000001; rev:1;)
alert tcp !192.168.20.100 any -> 192.168.10.10 6443 (msg:"Unexpected host contacting k3s API server"; flags:S; sid:1000002; rev:1;)
alert udp 192.168.20.0/24 any -> !192.168.20.1 53 (msg:"DMZ DNS query not going to pfSense"; sid:1000003; rev:1;)
alert tcp any any -> 192.168.20.100 ![22,10250,3030] (msg:"Connection to unexpected port on DMZ worker"; flags:S; sid:1000004; rev:1;)
