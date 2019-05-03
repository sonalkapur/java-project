node('linux'){
    stage('Unit Tests'){
        git 'https://github.com/sonalkapur/java-project.git'
        sh 'ant -f test.xml -v'
        junit 'reports/result.xml'
    }
    stage('Build'){
        ant -f build.xml -v
    }
}
