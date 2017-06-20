node {
  if (GITHUB_PR_NUMBER != null) {
    checkout(changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: "*/pull/${GITHUB_PR_NUMBER}/head"]],
      userRemoteConfigs: [[name: "origin-pull",
      refspec: "+refs/pull/${GITHUB_PR_NUMBER}/merge:refs/remotes/origin-pull/pull/${GITHUB_PR_NUMBER}/merge",
      url: 'git://github.com/petems/jenkins-github-pull-request.git']]])
  } else {
    git url: "git://github.com/petems/jenkins-github-pull-request.git", branch: "master"
  }
  sh "ls"
}
