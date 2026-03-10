pipeline {
    agent any

    stages {
        stage('Deploy Pod') {
            steps {
                sh '''
                kubectl apply -f - <<EOF
apiVersion: v1
kind: Pod
metadata:
  name: hello-jenkins-pod-webapp-2
  namespace: github-pipeline
  labels:
    app: hello-jenkins
spec:
  containers:
  - name: hello-container
    image: nginx:alpine
    ports:
    - containerPort: 80
    resources:
      requests:
        memory: "32Mi"
        cpu: "50m"
      limits:
        memory: "64Mi"
        cpu: "100m"
EOF

                kubectl get pods -n github-pipeline -o wide
                '''
            }
        }
    }
}
