# marom-k8s
בתוך תיקיית wordpress-k8s:

צריך להץחבר לecr

צור את ה‑Secrets:

kubectl apply -f secret.yaml


צור את מסד הנתונים (Service + StatefulSet):

kubectl apply -f db/service.yaml

kubectl apply -f db/statefulset.yaml


צור את WordPress (Service + Deployment):

kubectl apply -f wordpress/service.yaml

kubectl apply -f wordpress/deployment.yaml


צור את ה‑Ingress:

kubectl apply -f ingress/ingress.yaml


בדוק סטטוס:

kubectl get pods
kubectl get svc
kubectl get ingress

 גישה ל‑WordPress

השתמש ב‑Port Forward:

kubectl port-forward svc/wordpress 8080:80


וSSH Tunnel מאובטח:

ssh -i "<your-key>.pem" ec2-user@<EC2_PUBLIC_IP> -L 8080:localhost:80


הוסף 127.0.0.1 wordpress.local ל־hosts במחשב המקומי.

גש ל־http://wordpress.local:8080.


helm install marom-prom oci://ghcr.io/prometheus-community/charts/kube-prometheus-stack

kubectl port-forward svc/marom-prom-grafana 3000:80

ssh -i "<your-key>.pem" ec2-user@<EC2_PUBLIC_IP> -L 3000:localhost:80
