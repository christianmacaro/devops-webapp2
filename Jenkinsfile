//START-OF-SCRIPT
//comment1
timeout(time: 60, unit: 'SECONDS'){
   node{
      properties([
         pipelineTriggers([pollSCM('H/1 * * * 1-5')])
      ])
      
      def GRADLE_HOME = tool name: 'gradle-4.10.2', type: 'hudson.plugins.gradle.GradleInstallation'
      sh "${GRADLE_HOME}/bin/gradle tasks"

      stage('Clone'){
         git url: 'https://github.com/christianmacaro/devops-webapp1.git'
      }
    
      stage('Build'){
         sh "${GRADLE_HOME}/bin/gradle build --info"
      }
    
      stage('Archive'){
         archiveArtifacts 'build/libs/*.war'
      }      
   }
}
//END-OF-SCRIPT
