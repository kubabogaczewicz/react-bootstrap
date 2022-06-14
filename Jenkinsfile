library 'smartlogic-common@v2'

this.utils = smartlogic.api('Utils')

smartlogic([
  docker: 'node:16',
  builder: smartlogic.yarnBuilder(),
  buildWrapper: {
    sh "chown -R root ./"
    it()
  },
  archive: {archive()}
])

def archive() {
  utils.copyDirToWorkspaceIfExists("/root/.npm/_logs/", "npm_logs")
  List artifactsToArchive = ['**/*.log', "**/*.log.*"]
  archiveArtifacts(artifacts: artifactsToArchive.join(","), allowEmptyArchive: true)
}
