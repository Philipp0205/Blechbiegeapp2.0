```
graph LR
subgraph Broker
  T1
  T2[(...)]

end
  PUB[Publisher]:::pub --Messages--> T1[(Topic)] --Messages--> S1[Subscriber]:::sub & S2[Subscriber] & S3[Subscriber] 
  S2:::sub
  S3:::sub

classDef pub fill:#ebcb8b
classDef sub fill:#a3be8c
```