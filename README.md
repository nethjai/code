node('docker-slave')
{   
    def mn = [:]

for (int i = 0; i < 15; i++) {
  def index = i
  mn["new${i}"] = {
    build job: 'job', parameters: [
      string(name:'sample', value: "${index}")]
  }
}
parallel mn
}
