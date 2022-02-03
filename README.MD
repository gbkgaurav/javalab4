#WAP to create an Echo server and client in java.

##Networking in Java
Networking supplements a lot of power to simple programs. With networks, a single program can regain information stored in millions of computers positioned anywhere in the world. Java is the leading programming language composed from scratch with networking in mind. Java Networking is a notion of combining two or more computing devices together to share resources.

All the Java program communications over the network are done at the application layer. The java.net package of the J2SE APIs comprises various classes and interfaces that execute the low-level communication features, enabling the user to formulate programs that focus on resolving the problem.
###Socket Programming
Java Socket programming is used for communication between the applications running on different JRE.

Java Socket programming can be connection-oriented or connection-less.

Socket and ServerSocket classes are used for connection-oriented socket programming and DatagramSocket and DatagramPacket classes are used for connection-less socket programming.

The client in socket programming must know two information:

*IP Address of Server, and
*Port number.

####Server code:
``` 
import java.net.*;
import java.io.*;
public class Server {
	public static void main(String args[]) throws Exception,UnknownHostException{
		
		ServerSocket ss=new ServerSocket(8088);
		
		Socket s=ss.accept();;
		
		DataInputStream din=new DataInputStream(s.getInputStream());
		DataOutputStream dout=new DataOutputStream(s.getOutputStream());
		
		BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
		
		String str="",str2="";
		
		while(str!="stop")
		{
			System.out.println("Waiting for client's Reply...");
			str=din.readUTF();
			System.out.println("Client: "+str);
			System.out.println("Enter Message:");
			str2=br.readLine();  
			dout.writeUTF(str2);  
			dout.flush();
		}
		
		din.close();
		s.close();
		ss.close();
	}
} 
```

####Client code:
```
import java.net.*;
import java.io.*;
public class Client  {

	public static void main(String[] args)  throws Exception {
		
		Socket s=new Socket("localhost",8088);
		
		DataInputStream din=new DataInputStream(s.getInputStream());
		DataOutputStream dout=new DataOutputStream(s.getOutputStream());
		
		BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
		
		String str="",str2="";
		
		while(!str.equals("stop")){ 
			System.out.println("\nEnter Response: ");
			str=br.readLine();  
			dout.writeUTF(str);  
			dout.flush();  
			System.out.println("Waiting for Server's Reply...");
			str2=din.readUTF();  
			System.out.println("Server says: "+str2);  
			}  
			  
			dout.close();  
			s.close();  
		
	}
}
```

## Draw a cricle, ellipse, traingle, hexagon, pentagon in different colors.
```
import java.awt.Graphics;
import javax.swing.JFrame;
import java.awt.Color;
public class Shapes extends JFrame{
    Shapes(){
        setSize(1000,900);
        setVisible(true);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
    }
    public void paint(Graphics g){
        g.drawOval(50,50,60,60);
        g.setColor(Color.PINK);
        g.fillOval(50,50,60,60);
        g.setColor(Color.YELLOW);
        g.fillPolygon(new int[]{190,120,110}, new int[]{190,200,110} ,3);
        g.setColor(Color.ORANGE);
        g.fillOval(300,350,100,60);
        g.setColor(Color.BLUE);
        g.fillPolygon(new int[]{90,160,200,160,90,50}, new int[]{200,220,270,350,350,270},6);
        g.setColor(Color.GREEN);
        g.fillPolygon(new int[]{90,160,200,160,90}, new int[]{400,400,470,550,550},5);
    }
    public static void main(String[] args) {
        new Shapes();
    }
}
```
