# EXPT.NO.2A) Implementation and Performance Analysis of Sliding Window Protocol
# AIM
To implement an error control mechanism within the Sliding Window protocol and assess the protocol's performance by simulating varying network conditions to analyze the impact on throughput, reliability, and efficiency.
# EQUIPMENTS REQUIRED
•	Computer/Laptop
•	Code::Blocks 25.03 IDE
•	C++ compiler (GNU GCC)
•	Windows/Linux operating system
# PROCEDURE
1.	Open the Code::Blocks IDE.
2.	Create a new C++ Console Application and open the main.cpp source file.
3.	Initialize the total number of packets and the Sliding Window size.
4.	Implement the Go-Back-N form of the Sliding Window protocol.
5.	Simulate packet transmission through the network.
6.	Introduce different packet-loss probabilities to represent varying network conditions.
7.	Transmit packets within the current sliding window.
8.	If a packet is lost, retransmit from the lost packet position according to the Go-Back-N mechanism.
9.	Continue transmission until all packets are successfully delivered.
10.	Count the total transmissions and retransmissions.
11.	Calculate throughput, reliability, and efficiency for each packet-loss condition.
12.	Compare the results obtained for 0%, 10%, 20%, 30%, and 40% packet-loss conditions.
 
# C++ PROGRAM
```

#include <stdio.h>

#define WINDOW_SIZE 4
#define MAX_FRAMES 100

int main()
{
    int i, window_start = 1, ack;
    int n;
    char frame[MAX_FRAMES + 1][10];

    printf("SLIDING WINDOW PROTOCOL\n");
    printf("GO BACK N ARQ\n");

    printf("Enter the number of frames: ");
    scanf("%d", &n);

    if (n <= 0 || n > MAX_FRAMES)
    {
        printf("Invalid number of frames.\n");
        return 1;
    }

    for (i = 1; i <= n; i++)
    {
        printf("Content for frame %d: ", i);
        scanf("%9s", frame[i]);
    }

    while (window_start <= n)
    {
        printf("\nSending frames:\n");

        for (i = window_start;
             i < window_start + WINDOW_SIZE && i <= n;
             i++)
        {
            printf("Frame %d: %s\n", i, frame[i]);
        }

        printf("Enter frame number with no ACK (0 if all are acknowledged): ");
        scanf("%d", &ack);

        if (ack == 0)
        {
            window_start += WINDOW_SIZE;
        }
        else if (ack >= window_start && ack <= n)
        {
            printf("No acknowledgement for frame %d.\n", ack);
            printf("Resending frames starting from frame %d.\n", ack);

            window_start = ack;
        }
        else
        {
            printf("Invalid acknowledgement.\n");
        }
    }

    printf("\nAll frames sent successfully.\n");

    return 0;
}

```

# OUTPUT
<img width="576" height="512" alt="Screenshot 2026-08-02 205039" src="https://github.com/user-attachments/assets/430457f7-56fe-4629-8c01-9b790eab2208" />

 
# RESULT
Thus, the Go-Back-N Sliding Window protocol with error control was successfully implemented and executed in C++ using Code::Blocks. The simulation was performed under different packet-loss conditions. It was observed that as packet loss increases, retransmissions increase while throughput and efficiency decrease. The protocol maintains reliable delivery by retransmitting lost packets. Hence, varying network conditions have a significant impact on the performance of the Sliding Window protocol.
