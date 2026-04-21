Remember there are L4 and L7 load balancers

L4: [[Network load balancer (NLB)]]
L7: [[Application load balancer (ALB)]]

# Network balancing algorithms:

1. Least connections
2. Least response time
3. Least bandwidth
4. Round robin (send requests to each server in order, eg 1,2,3,1,2....)
5. Weighted round robin (same but maybe some servers get 2)
6. IP hashing (so same client always gets to same node)