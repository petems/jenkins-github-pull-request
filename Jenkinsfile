job('jenkins-github-pr') {
  concurrentBuild()

  parameters {
    stringParam('sha1')
  }

  scm {
    git {
      remote {
        github('petems/jenkins-github-pull-request')
        refspec('+refs/pull/*:refs/remotes/origin/pr/*')
      }
      branch('${sha1}')
    }
  }

  triggers {
    githubPullRequest {
      useGitHubHooks()
      userWhitelist(['petems'])
      triggerPhrase('test this please|please test this')
      extensions {
        commitStatus {
          context('jenkins-github-tests')
          triggeredStatus('Tests triggered')
          startedStatus('Tests started')
          completedStatus('SUCCESS', 'Success')
          completedStatus('FAILURE', 'Failure')
          completedStatus('PENDING', 'Pending')
          completedStatus('ERROR', 'Error')
        }
      }
    }
  }

  steps {
    shell('echo Hello')
  }

}

job('jenkins-master') {
  concurrentBuild()

  scm {
    git {
      remote {
        github('petems/jenkins-github-pull-request')
      }
      branch('master')
    }
  }

  triggers {
    githubPush()
    gitHubPushTrigger()
    cron('@daily')
    pollSCM{scmpoll_spec('')}
  }

  steps {
    shell('echo Hello')
  }
}
