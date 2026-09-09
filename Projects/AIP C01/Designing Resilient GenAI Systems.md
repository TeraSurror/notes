1. Circuit Breaker Pattern with Step Function
	1. Retry with exponential backoff
	2. Fallback model when all fails
	3. No custom retry logic is needed in application code
2. Fallback to a cached response from Elasticache to deliver graceful degradation instead of returning an error to the user
3. Cross region Inference - Automatically checks to determine which region has availability and capacity to fulfill the request and **routes to the optimal region**

[[Cross-region Model Deployment Deployment Strategies]]