
# 基于UDP的网络编程

TCP: 




客户端：Socket                                         程序感受到的 使用流  ：输出流 

服务器端：  ServerSocket --->Socket     程序感受到的 使用流  ：输入流 

（客户端和服务器端地位不平等。） 










UDP: 

发送方：DatagramSocket   发送：数据包  DatagramPacket 

接收方：DatagramSocket   接收：数据包  DatagramPacket 

（发送方和接收方的地址是平等的。） 







UDP案例：  完成网站的咨询聊天 















------------------------------------------------------------

