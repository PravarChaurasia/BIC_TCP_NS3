# BIC_TCP_NS3
BIC comparison on Linux and ns3, modificaiton to overlap the graph in both Linux Kernel and ns3-dce

1) As Ns-3-dce does not have the correct and same  implementation of PRR Recovery as Linux we need to update the ns-3-dev. After updating ns-3-dev we need to build it again. 
2) We updated the ns-3-dev using the link https://gitlab.com/apoorvabhargava/ns-3-dev.git
3) In NS3 Implementation, Function GetSsThrash uses the value of m_beta which is Beta for multiplicative decrease. This m_beta has a hardcoded value of 0.8 in NS3 implementation, But in Linux m_beta is calculated with the scale Factor(1024). We updated the value of m_beta in the GetSsThrash function to 0.899 in one if condition and to 0.799 in the other as per the linux's implementation.
4) In NS3 Implementation value of smoothing factor is 5 but in linux it is 20. We changed NS3's smoothing factor to 20.
5) After changing according to Point 3 and 4, We are able to generate the Graph (CwndA_Improvement.Png).

