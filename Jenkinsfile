pipeline {
  agent any
  stages {
    stage('pod install') {
      parallel {
        stage('pod install') {
          steps {
            dir(path: 'Example') {
              sh '''export LANG=en_US.UTF-8
rm -f Podfile.lock
rm -f pods/
/usr/local/bin/pod install'''
            }

          }
        }

        stage('log') {
          steps {
            echo 'pod install'
          }
        }

      }
    }

    stage('sleep') {
      steps {
        sleep 2
      }
    }

    stage('build') {
      parallel {
        stage('build') {
          steps {
            dir(path: 'Example') {
              xcodeBuild(target: 'LRSEntranceSourceLoader_Example', xcodeWorkspaceFile: 'LRSEntranceSourceLoader', xcodeSchema: 'LRSEntranceSourceLoader-Example', bundleIDInfoPlistPath: 'LRSEntranceSourceLoader/LRSEntranceSourceLoader-Info.plist', developmentTeamID: '3EZ8YQY6LK', developmentTeamName: 'Junc liu', ignoreTestResults: true, ipaExportMethod: 'development', buildIpa: true, cleanBeforeBuild: true, cleanResultBundlePath: true, cleanTestReports: true, generateArchive: true, provideApplicationVersion: true, copyProvisioningProfile: true, signingMethod: 'Automic', sdk: 'iphoneos')
            }

          }
        }

        stage('log') {
          steps {
            echo 'build'
          }
        }

      }
    }

    stage('sleep2') {
      steps {
        sleep 2
      }
    }

    stage('upload ipa') {
      steps {
        sh 'ls'
        dir(path: 'Example') {
          exportIpa(archiveDir: 'build', compileBitcode: true, developmentTeamID: '3EZ8YQY6LK', developmentTeamName: 'junc liu', signingMethod: 'Automic')
        }

      }
    }

  }
}