Model will experience drift over time if left unmanaged

Example:
1.  model training/finetuning
2. Model version control 
3. Deploy
4. Performance monitoring

Sagemaker model registry:
- manage model versions
- Track approval states
- Associate metadata - training data lineage
- Hyperparamter used, infra reqs
- Approval trail, intended use and limitations 

EventBridge can trigger an automated deployment

Performance monitoring:
1. Cloudwatch: Infra and ops metrics, error rates, latency, invocation, metrics, CPU/GPU utilization 
2. Sagemaker Model Monitor: Statistical quality of model inputs and outputs. Data quality, model quality, bias drift, feature attribution drift. Are predictions accurat
3. Sagemaker Clarify: Fairness and transparenc. Fairnes, bias, and feature attribution. All groups being treated fairly? Which features drive decisions?

Exam tips:
Sagemaker AI: Training and finetuning
Sagemaker Model registry: Version control
CodePipeline, CodeBuild, CloudFormation, Sagemaker Pipeline: deployment 
Cloudwatch, Sagemaker model monitor, Sagemaker clarify: monitor

