pipeline {
   agent any

   tools {
      // Install the Maven version configured as "M3" and add it to the path.
      maven "Default"
   }

   stages {
     stage ('Fastlane Builds') {
       steps {
         // fastlane build
       }
     }

     stage ('Run Fragmented') {
       steps {
         build job: 'Fragmented', parameters: [
            string(name: 'SIMULATORS', value: 'iPhone 8,iPhone 11 Pro Max'),
            string(name: 'Excluded_Tags', value: '@wip,@Test,@RealDevice'),
            string(name: 'Branch', value: 'origin/master')
            ]
        }
      }

         post {
            // If Maven was able to run the tests, even if some of the test
            // failed, record the test results and archive the jar file.
            success {
               // junit '**/target/surefire-reports/TEST-*.xml'
               // archiveArtifacts 'target/*.jar'
            }
         }
      }
   }
}
