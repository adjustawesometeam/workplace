#!/usr/bin/env groovy
def remote = [:]
    remote.host = '192.168.200.68'
    remote.name = 'node'
    remote.allowAnyHosts = true
    node() {
        remote.user = 'root'
        remote.password = 'YsBBB4zgzn9Fjoe'
        withCredentials([usernamePassword(credentialsId: 'kitrumvm', passwordVariable: 'YsBBB4zgzn9Fjoe', usernameVariable: 'root')]){
    stage('Install services'){
	sshCommand remote: remote, command: 'sudo dnf update -y'
    sshCommand remote: remote, command: 'sudo dnf install -y docker-ce docker-ce-cli containerd.io'
    sshCommand remote: remote, command: 'sudo systemctl start docker'
    sshCommand remote: remote, command: 'sudo systemctl enable docker'
    sshCommand remote: remote, command: 'sudo docker --version'
    sshCommand remote: remote, command: 'sudo curl -L "https://github.com/docker/compose/releases/download/1.27.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose'
    sshCommand remote: remote, command: 'sudo chmod +x /usr/local/bin/docker-compose'
    sshCommand remote: remote, command: 'sudo docker-compose --version'
    }
    stage('Git clone and start services'){
    sshCommand remote: remote, command: 'rm -rf ~/workspace'   
    sshCommand remote: remote, command: 'git clone https://github.com/adjustawesometeam/workplace.git'
    sshCommand remote: remote, command: 'cd workplace && ls -a  && sudo docker-compose up -d'
    }
}
    }
