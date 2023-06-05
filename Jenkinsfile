node("cd") {
    def serviceName = "books-ms"
    def prodIp = "192.168.56.200"
    def proxyIp = "192.168.56.200"
    def registryIpPort = "192.168.60.200:5000"

    checkout scm
    def flow = load "/data/scripts/workflow-util.groovy"
    flow.provision("prod2.yml")
    flow.buildTests(serviceName, registryIpPort)
    flow.runTests(serviceName, "tests", "")
    flow.buildService(serviceName, registryIpPort)
    flow.deploy(serviceName, prodIp)
    flow.updateProxy(serviceName, "prod")
    flow.runTests(serviceName, "integ", "-e DOMAIN=http://${proxyIp}")
}
