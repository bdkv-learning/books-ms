node("cd") {
    def serviceName = "books-ms"
    def registryIpPort = "192.168.60.200:5000"
    def prodIp = "192.168.60.201"
    def proxyIp = "192.168.60.201"
    def proxyNode = "prod"

     def flow = load "/data/scripts/workflow-util.groovy"

    checkout scm
    flow.provision("prod2.yml")
    //flow.buildTests(serviceName, registryIpPort)
    //flow.runTests(serviceName, "tests", "")
    //flow.buildService(serviceName, registryIpPort)

    def currentColor = flow.getCurrentColor(serviceName, prodIp)
    def nextColor = flow.getNextColor(currentColor)

    flow.deployBG(serviceName, prodIp, nextColor)
    //flow.runBGPreIntegrationTests(serviceName, prodIp, nextColor)
    flow.updateBGProxy(serviceName, proxyNode, nextColor)
    //flow.runBGPostIntegrationTests(serviceName, prodIp, proxyIp, proxyNode, currentColor, nextColor)
}
