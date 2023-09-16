pipeline{
agent any
stages{
stage('checkout'){
steps{
checkout scm
}
}
stage('build and test'){
steps{
dir('/home/anusha/sampleproject'){
sh'mkdir -p build'
sh 'cp sample.html build/'
sh 'cp sample.css build/'
}
}
}
stage('deploy to s3'){
steps{
withCredentials([[$class:'AmazonWebServicesCredentialsBinding',credentialsId:'realawskey','accessKeyVariable:'AKIAW7IDMJGT46GFZLWC',secretkeyVariable:'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']]){
sh'aws s3 sync ./build/ s3://mystaticawsbucket/'
}
}
}
}
}
