ipconfig/all
nslookup www.sfit.ac.in
ping -t www.sfit.ac.in
tracert -n 5 www.sfit.ac.in
arp -a
route print
netstat
netsh lan dump
pathping -h 3 www.sfit.ac.in
getmac
hostname
nbstat -r
systeminfo

----------------------------------

import java.util.Scanner;

class Framing {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Data: ");
        String data = sc.nextLine();
        System.out.print("Choice (1: Count 2: Byte 3: Bit 4: Violation): ");
        
        String result = switch (sc.nextInt()) {
            case 1 -> (data.length() + 1) + data;
            case 2 -> "F" + data.replace("F", "EF").replace("E", "EE") + "F";
            case 3 -> data.replaceAll("11111", "111110");
            case 4 -> data + "01";
            default -> "Invalid!";
        };
        
        System.out.println("Result: " + result);
        sc.close();
    }
}


-----------------------------------------


import java.io.*;
import java.net.*;

public class MyServer {
    public static void main(String[] args) {
        try {
            ServerSocket ss = new ServerSocket(6666); 
            Socket s = ss.accept(); // establishes connection
            
            DataInputStream dis = new DataInputStream(s.getInputStream()); 
            String str = (String) dis.readUTF();
            System.out.println("message= " + str); 
            
            ss.close();
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}




import java.io.*;
import java.net.*;

public class MyClient {
    public static void main(String[] args) {
        try {
            Socket s = new Socket("localhost", 6666);

            DataOutputStream dout = new DataOutputStream(s.getOutputStream());
            dout.writeUTF("Hello Server");
            dout.flush();
            dout.close();
            s.close();
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}


----------------------------------------

ping scan
regular scan
pingless scanning: t4 -A -v -Pn
os scanning: -O
quick scanning
traceroute: -sn --traceroute
version scanning: -sV
udp scanning
quick scan plus
quick traceroute
icmp and arp scans with traceroute: -sn -PE -PP --traceroute

------------------------------------------

VLAN: go to switch1 and cli

VLAN 
enable  
config t  
vlan 20 
name purchase  
exit 
vlan 30  
name sales  
exit 
int fa0/2 
switchport access vlan 20  
exit 
int fa0/3 
switchport access vlan 20  
exit 
int fa0/4 
switchport access vlan 30  
exit 
int fa0/5 
switchport access vlan 30  
exit


