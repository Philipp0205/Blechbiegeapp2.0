[[BPT-07-SOA.pdf]]

# Motivation 
Problem 
- Inter-Application-Spaghetti

Solution
- SOA

# SOA Idea
- Structuring AL by Services into logical layers based on the factual business view.
- Service providers offer functionality over well defined interfaces and standardised technologies
	- Service consumers use these Services 
	- Service registered in a repo

![[SOAIdea.png]]

# Advantages 
- Better structure of the overall AL 
- Increased reuse of Services and their functionality 

//
- Faster and more flexible reconfiguration of business processes 
- Decrease of operational costs of IT
- Secure and reliable service levels 

# Terminology 
## *Service* 
Functionality offered by a software component.

## *Architecture* 
![[Pasted image 20220204161814.png]]

Paradigm 
1. Structure the company's business (business architecture) 
2. Derive architecture of the IT application system landscape (AL) 
3. Structure AL based on modeling the services offered ans used by applications 

## *Business Service* 
- Functionality with immediate business utility
- Clearly defined usage 
- Clearly defined reactions and effects 
- In context of contractual liabilities and utility
- Over organizational border

## *Application service*
- Support business services
- Follow contract on input/output 
- Uncouple business services logically from apps 
- Offered by components in an AL 
- Built after the ideal of the business services

- Structuring AL by Services into logical layers based on factual business view
- Service providers offer functionality over interfaces and standardised technologies 

# SOA and Web Services
- Web Services offer a fitting technical basis for implementing SOA
	- Related standards: SOAP, WSDL, 
- But SOA concept is technology independent

# SOA Requirements - app services
- Re-Use
- Fulfill requirements 
- Clearly defined functionality 
- Well defined interfaces 
- Well defined relationships

Key success factor: Good Service Cut 

# Approaches to build SOA
## Top-Down approach
From business process to service. 

1. Systematic Process analysis 
2. Modularisation & Iterative Refinement
3. Identification of identical/similar process modules 
4. Development of Business Services

## Bottom-Up Approach (Harvesting)
1. Existing application systems 
2. Identification of candidates for basic and high level application services
3. Aggregation to business services

# Does IT need to align to Business? 
Both is true and false at the same time: SOA offers an optimal approach to uncouple both aspects. 

# Challenges 
No SOA out of the box 
- Products/implementations must be combined for individual solutions 
- Services must be structures consistently and in alignment of ?
- Products partly relatively new 
- Best-Practices may provide help


Implementing a direct transformation from business process to service 
- Top-Down vs. Bottom Up
- Holistic vision rarely implemented 

Organisational adjustments 
- Implementing, operating and funding services 
- Quality assurance and service release process 

Management and business comittment
- SOA in itself offers very few short-term utility 
- Mid- to long-term amortisation 
- Quick-Wins must be created explicitly 

# Conclusion
- Without long-term technical considation, SOA increases operating costs 
- The tasks and challenges of IT system integration are well understood 
- Using Web Services for large Scale SOA is inevitable today 
- Technologies and products in the SOA area are not all similar  
- Using a SOA platform in itself does not guarantee a good architecture

When clearly adhered, the SOA paradigm to current knowledge is the best approach to master today AL! 
