node("cd") {
    def serviceName = "books-ms"
    def registryIpPort = "192.168.200:5000"

    checkout scm
    def flow = load "/data/scripts/workflow-util.groovy"
    flow.buildTests(serviceName, registryIpPort)
    flow.runTests(serviceName, "tests", "")
}
