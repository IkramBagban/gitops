## Cheatsheet

### Ingress 
- Add the `ingress-nginx` chart

```jsx
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
helm install nginx-ingress ingress-nginx/ingress-nginx --namespace ingress-nginx --create-namespace
```

- Check if you have pods running in the

```jsx
 kubectl get pods -n ingress-nginx
```
---
### Sealed Secret
1. **Add the Sealed Secrets Helm Chart Repo** (if haven't added it yet):
    
    ```bash
    helm repo add sealed-secrets https://bitnami-labs.github.io/sealed-secrets
    helm repo update
    ```
    
2. **Install the Sealed Secrets Controller** using Helm:
    
    ```bash
    helm install sealed-secrets sealed-secrets/sealed-secrets --namespace kube-system
    ```
    
    This installs the Sealed Secrets controller in the `kube-system` namespace.
3. **kubeseal command to encrypt the secret:**
```sh
cat secret.yaml | kubeseal --controller-namespace kube-system --controller-name sealed-secrets-controller --format yaml > sealed-secret.yaml
```

4. **Verify**
   ```sh
   kubectl get secret db-secret -n kube-system
   ```

