Kubernetes Pod CrashLoopBackOff? Issue: 
Solution:
✅ How to check pod status and logs 

✅ Common reasons for CrashLoopBackOff OOMKilled, permission issues, missing configs, etc.

✅ Step-by-step fixes for each issue  

✅ Pro tips to prevent it in the future  

Step1: kubectl get pods -n <your namespacename>

Step2: kubectl describe pod <pod-name > -n <namespacename>

Step3: kubectl logs <pod-name> -n <namespacename> --previous

**Common issues for CrshLoopBackOff:**
Issue: Missing Configs/Secrets:
Error Example: Crash due to missing environment variable
Fix: Check if necessary ConfigMaps or Secrets are mounted properly.
Command: kubectl get configmap/secret -n <namespace>

Issue: Insufficient Resources
Error Example: OOMkilled in kubectl describe pod output
Fix: Increase Memory/CPU limits in the deployment YAML
Command: resources:
           limits:
              cpu: "2"
              memory: "2Gi

Issue: Application Bug or Wrong command:
Error Example: command not found or Exec format error.
Fix: Check your command and args in the deployment YAML
command :  command: ["/bin/sh", "-c"]
           args: ["echo Hello World"]
