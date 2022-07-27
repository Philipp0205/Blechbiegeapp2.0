
# 12 Factors 
- Store config in the environment
- An apps config is everything that is likely to vary between deploy (staging, production, dev environments)

What does a config include? 
- Resource handles to the database
- Credentials 
- Per-deploy values such a the canonical hostname for the deploy. 

Strict separation of config from code 
- No environment dependent config should be stored in the code. 
	- -> Does not scale
- Config varies substantially across deploys, code does not. 

# External config through a file 
*@Configuration* 
Spring creates a Spring bean in the application context.


### Review questions
- "WHY" is external configuration important in cloud-native software?
- Where did you see aspects of external configuration in the technologies we used? Provide examples