pipeline {
  agent any

  environment {
    INVENTORY = 'inventory'
    PRIVATE_KEY = 'ansible-key'
  }

	triggers {
			pollSCM '* * * * *'
	}

  stages {
    stage('Run Ansible Playbook for Dev and QA') {
      steps {
        sshagent([PRIVATE_KEY]) {
          sh '''
					  cd /home/ubuntu/ansible-setup
            ansible-playbook -i ${INVENTORY} playbook.yml
          '''
        }
      }
    }
  }
}
