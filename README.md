# Kubernetes-Deploy-WithJenkinsCICD

# Pre-requisites:
    - Install Jenkins
    - Install GIT
    - Install Docker
    - Install Jenkins
    - EKS Cluster
# Install GIT:
    yum install git -y
# Install Docker:
    yum install docker -y
    service docker start
# Install Jenkins
    sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins.io/redhat-stable/jenkins.repo
    sudo rpm --import http://pkg.jenkins.io/redhat-stable/jenkins.io.key
    sudo yum install jenkins -y
    sudo service jenkins start
    
    You will get error for java part: install java and start the jenkins
    
![image](https://user-images.githubusercontent.com/54719289/117429679-30a68b00-af1f-11eb-9944-5a93e958f9c1.png)

    
# Add jenkins user docker group
    usermod -aG docker jenkins
# Provide sudo permissions for jenkins user
    vi /etc/sudoers
  ![image](https://user-images.githubusercontent.com/58024415/96357945-9a944a00-111f-11eb-8a33-e4d1980c4609.png)
# Restart jenkins
    service jenkins restart
# EKS Cluster Setup:
  [EKS Cluster Setup](https://github.com/Naresh240/eks-cluster-setup/blob/main/README.md)
# Add kubectl to default path
    cp ./kubectl /usr/bin
# Goto Jenkins and add plugins
    jenkins --> Manage Jenkins --> Available
    - CloudBees AWS Credentials
    - Kubernetes Credentials
    - Kubernetes Continuous Deploy


![image](https://user-images.githubusercontent.com/54719289/117446258-b6343600-af33-11eb-85a7-fa709814f1d9.png)

# Create Credentials
    - docker credentials
         (credentialsId: 'docker_credentials',  username: 'username', password: 'password')
    - kubernetes config credentials
         (credentialsId: 'kube_config', variable: 'KUBECONFIG')
         
     - aws configure credentials
         (accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws_configure', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')

![image](https://user-images.githubusercontent.com/54719289/117446636-41adc700-af34-11eb-90ed-37a7d3be02ea.png)
![image](https://user-images.githubusercontent.com/54719289/117446769-7ae63700-af34-11eb-8b2e-e03cf7d7c643.png)

![image](https://user-images.githubusercontent.com/54719289/117446793-85a0cc00-af34-11eb-8973-fa7742ba42e8.png)


# Add JenkinsFile Content inside pipeline section
  ![image](https://user-images.githubusercontent.com/58024415/96358243-ae8d7b00-1122-11eb-89ef-f68a7bee8273.png)
# Goto Web UI and Check output of application
   http://ad5ab72d8d77042768e8994647f637e1-1324271138.us-east-1.elb.amazonaws.com:8080/
   
  ![image](https://user-images.githubusercontent.com/58024415/96358112-2f4b7780-1121-11eb-9825-0a9ab99659c1.png)
