# BIC_TCP_NS3

Project Title: Validate the ns-3 implementation of BIC TCP using ns-3 DCE

Brief: 

Binary Increase Congestion control (BIC) is a precursor to CUBIC and is targeted for
Long Fat Networks. It uses a binary search algorithm to find the optimal value of congestion
window (​ cwnd ​ ). In this project, the aim is to validate ns-3 BIC implementation by comparing
the results obtained from it to those obtained by simulating Linux BIC.

Recommended Reading:

● Direct Code Execution (Link: https://www.nsnam.org/overview/projects/direct-code-execution/​ )

● Linux kernel code (Link: ​ https://elixir.bootlin.com/linux/v4.4/source/net/ipv4/tcp_bic.c​ )

● BIC Paper (Link: ​ https://ieeexplore.ieee.org/abstract/document/1354672/​ )


Overview of Work Done:
(See Wiki For More Details)

1) As Ns-3-dce does not have the correct and same  implementation of PRR Recovery as Linux we need to update the ns-3-dev. After updating ns-3-dev we need to build it again. 
2) We updated the ns-3-dev using the link https://gitlab.com/apoorvabhargava/ns-3-dev.git
3) In NS3 Implementation, Function GetSsThrash uses the value of m_beta which is Beta for multiplicative decrease. This m_beta has a hardcoded value of 0.8 in NS3 implementation, But in Linux m_beta is calculated with the scale Factor(1024). We updated the value of m_beta in the GetSsThrash function to 0.899 in one if condition and to 0.799 in the other as per the linux's implementation.
4) In NS3 Implementation value of smoothing factor is 5 but in linux it is 20. We changed NS3's smoothing factor to 20.
5) After changing according to Point 3 and 4, We are able to generate the Graph (CwndA_improvement_1.Png).
6) We changed --delAckCount to 2 in the command line parameters both in linux and NS3 and were able to generate the Graph(CwndA_delAckCount=2.png)
