#!groovy​

node {
    stage 'Checkout'
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
            admin('petems')
            useGitHubHooks()
            permitAll()
        }
    }

    stage 'test'
    sh 'rake test'
}
