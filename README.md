Running with gitlab-runner 19.4.1 (3c39fceb)
  on dc_runner_80 KtJCK3d-w, system ID: s_37748334dac5
  UUID: 01a1239a-600e-7b48-a47a-a4c2a2c06502
Resolving secrets
Preparing the "docker" executor
00:00
Using Docker executor with image artifactory.jfrog.sbi:443/dso-base-image/java-maven-images/rhel-jdk-21-maven3.8.9:0.0.1 ...
Using helper image:  artifactory.jfrog.sbi:443/devsecops-docker-redhat-virtual/gitlab/gitlab-runner-helper:x86_64-v19.4.1  (overridden, default would be  registry.gitlab.com/gitlab-org/gitlab-runner/gitlab-runner-helper:x86_64-v19.4.1 )
Using effective pull policy of [if-not-present] for container artifactory.jfrog.sbi:443/devsecops-docker-redhat-virtual/gitlab/gitlab-runner-helper:x86_64-v19.4.1
Using locally found image version due to "if-not-present" pull policy
Using docker image sha256:25db4eaaff9ff231b010eca4e189065b821b637a443897e14e0271a9faf370bf for artifactory.jfrog.sbi:443/devsecops-docker-redhat-virtual/gitlab/gitlab-runner-helper:x86_64-v19.4.1 with digest artifactory.jfrog.sbi:443/devsecops-docker-redhat-virtual/gitlab/gitlab-runner-helper@sha256:25db4eaaff9ff231b010eca4e189065b821b637a443897e14e0271a9faf370bf ...
Using helper image:  artifactory.jfrog.sbi:443/devsecops-docker-redhat-virtual/gitlab/gitlab-runner-helper:x86_64-v19.4.1  (overridden, default would be  registry.gitlab.com/gitlab-org/gitlab-runner/gitlab-runner-helper:x86_64-v19.4.1 )
Using effective pull policy of [if-not-present] for container artifactory.jfrog.sbi:443/devsecops-docker-redhat-virtual/gitlab/gitlab-runner-helper:x86_64-v19.4.1
Using docker image sha256:25db4eaaff9ff231b010eca4e189065b821b637a443897e14e0271a9faf370bf for artifactory.jfrog.sbi:443/devsecops-docker-redhat-virtual/gitlab/gitlab-runner-helper:x86_64-v19.4.1 with digest artifactory.jfrog.sbi:443/devsecops-docker-redhat-virtual/gitlab/gitlab-runner-helper@sha256:25db4eaaff9ff231b010eca4e189065b821b637a443897e14e0271a9faf370bf ...
Using effective pull policy of [if-not-present] for container artifactory.jfrog.sbi:443/dso-base-image/java-maven-images/rhel-jdk-21-maven3.8.9:0.0.1
Using locally found image version due to "if-not-present" pull policy
Using docker image sha256:26834e2b7839f7d5d440948c8d561124b44bd5305be9669b455ccff74eade7ed for artifactory.jfrog.sbi:443/dso-base-image/java-maven-images/rhel-jdk-21-maven3.8.9:0.0.1 with digest artifactory.jfrog.sbi:443/dso-base-image/java-maven-images/rhel-jdk-21-maven3.8.9@sha256:26834e2b7839f7d5d440948c8d561124b44bd5305be9669b455ccff74eade7ed ...
Preparing environment
00:01
Using helper image:  artifactory.jfrog.sbi:443/devsecops-docker-redhat-virtual/gitlab/gitlab-runner-helper:x86_64-v19.4.1  (overridden, default would be  registry.gitlab.com/gitlab-org/gitlab-runner/gitlab-runner-helper:x86_64-v19.4.1 )
Using effective pull policy of [if-not-present] for container artifactory.jfrog.sbi:443/devsecops-docker-redhat-virtual/gitlab/gitlab-runner-helper:x86_64-v19.4.1
Using docker image sha256:25db4eaaff9ff231b010eca4e189065b821b637a443897e14e0271a9faf370bf for artifactory.jfrog.sbi:443/devsecops-docker-redhat-virtual/gitlab/gitlab-runner-helper:x86_64-v19.4.1 with digest artifactory.jfrog.sbi:443/devsecops-docker-redhat-virtual/gitlab/gitlab-runner-helper@sha256:25db4eaaff9ff231b010eca4e189065b821b637a443897e14e0271a9faf370bf ...
Using effective pull policy of [if-not-present] for container sha256:25db4eaaff9ff231b010eca4e189065b821b637a443897e14e0271a9faf370bf
Running on runner-ktjck3d-w-project-1758-concurrent-0 via PE3DSOPGRUNNERS6...
Getting source from Git repository
00:08
Gitaly correlation ID: 01M7WGMHZWERJVBXSXCDPXP5PZ
Fetching changes with git depth set to 20...
Initialized empty Git repository in /builds/cb-ops/fincore/fincorebackend/fincore_common_master_service/.git/
Created fresh repository.
Checking out 9cca399d as detached HEAD (ref is feature_security_config_state_master_upgrade)...
Skipping Git submodules setup
Downloading artifacts
00:03
Downloading artifacts for build_job (2278852)...
Downloading artifacts from coordinator... ok        correlation_id=01M7WGMW99RSKQF1J9XSQZMJCG id=2278852 status=200 token=eyJraWQiO
Executing "step_script" stage of the job script
00:27
Using effective pull policy of [if-not-present] for container artifactory.jfrog.sbi:443/dso-base-image/java-maven-images/rhel-jdk-21-maven3.8.9:0.0.1
Using docker image sha256:26834e2b7839f7d5d440948c8d561124b44bd5305be9669b455ccff74eade7ed for artifactory.jfrog.sbi:443/dso-base-image/java-maven-images/rhel-jdk-21-maven3.8.9:0.0.1 with digest artifactory.jfrog.sbi:443/dso-base-image/java-maven-images/rhel-jdk-21-maven3.8.9@sha256:26834e2b7839f7d5d440948c8d561124b44bd5305be9669b455ccff74eade7ed ...
$ jf config add \--url="$JF_URL" \--xray-url="$JF_XRAY_URL" \--user="$JF_USER" \--access-token="$JF_TOKEN" \--interactive=false
$ ls target
fincore_common_master_service-9cca399d-2278852.jar
$ jf scan target/*.jar --watches=CB-OPS --fail=true
12:59:41 [Info] JFrog Xray Indexer 3.150.38 is not cached locally. Downloading it now...
2026/11/20 12:59:43 maxprocs: Updating GOMAXPROCS=2: determined from CPU quota
12:59:43 [Info] The downloaded Xray Indexer version is 3.150.38
12:59:43 [Info] [Thread 2] Indexing file: target/fincore_common_master_service-9cca399d-2278852.jar
12:59:56 [Info] 2026/11/20 12:59:43 maxprocs: Updating GOMAXPROCS=2: determined from CPU quota
2026-11-20T12:59:51.193Z [jfxia] [WARN ] [] [maven_extractor:103           ] [UnnamedContext                  ] skipping adding org.slf4j:slf4j-api to :logback-classic: dependency again as already in list
2026-11-20T12:59:51.193Z [jfxia] [WARN ] [] [maven_extractor:103           ] [UnnamedContext                  ] skipping adding ch.qos.logback:logback-core to :logback-classic: dependency again as already in list
2026-11-20T12:59:51.228Z [jfxia] [WARN ] [] [maven_extractor:103           ] [UnnamedContext                  ] skipping adding ch.qos.logback:logback-core to :log4j-to-slf4j:2.25.5 dependency again as already in list
2026-11-20T12:59:56.264Z [jfxia] [WARN ] [] [maven_extractor:103           ] [UnnamedContext                  ] skipping adding ${project.groupId}:netty-transport to :netty-handler: dependency again as already in list
2026-11-20T12:59:56.341Z [jfxia] [WARN ] [] [maven_extractor:103           ] [UnnamedContext                  ] skipping adding ${project.groupId}:netty-transport to :netty-codec-base: dependency again as already in list
2026-11-20T12:59:56.470Z [jfxia] [WARN ] [] [maven_extractor:103           ] [UnnamedContext                  ] skipping adding ${project.groupId}:netty-transport to :netty-resolver-dns: dependency again as already in list
2026-11-20T12:59:56.475Z [jfxia] [WARN ] [] [maven_extractor:103           ] [UnnamedContext                  ] skipping adding ${project.groupId}:netty-transport to :netty-codec-dns: dependency again as already in list
2026-11-20T12:59:56.682Z [jfxia] [WARN ] [] [maven_extractor:103           ] [UnnamedContext                  ] skipping adding ch.qos.logback:logback-core to commons-logging:commons-logging:1.3.6 dependency again as already in list
12:59:57 [Info] Waiting for scan to complete on JFrog Xray...
Security Violations
+-----------------+------------+---------------------------+---------+---------------------------+-----------+-----------+-------+
| CVE             | SEVERITY   | DIRECT                    | DIRECT  | AFFECTED                  | AFFECTED  | FIXED     | TYPE  |
|                 |            | PACKAGE                   | PACKAGE | COMPONENT                 | COMPONENT | VERSIONS  |       |
|                 |            |                           | VERSION | NAME                      | VERSION   |           |       |
+-----------------+------------+---------------------------+---------+---------------------------+-----------+-----------+-------+
| CVE-2026-119078 | 💀Critical | commons-codec:commons-cod | 1.21.0  | commons-codec:commons-cod | 1.21.0    | [1.23.0]  | Maven |
|                 |            | ec                        |         | ec                        |           |           |       |
+-----------------+------------+---------------------------+---------+---------------------------+-----------+-----------+-------+
| CVE-2026-110879 | 💀Critical | tools.jackson.core:jackso | 3.1.7   | tools.jackson.core:jackso | 3.1.7     | [3.1.8]   | Maven |
|                 |            | n-databind                |         | n-databind                |           | [3.2.4]   |       |
+-----------------+------------+---------------------------+---------+---------------------------+-----------+-----------+-------+
| CVE-2026-110879 | 💀Critical | com.fasterxml.jackson.cor | 2.21.7  | com.fasterxml.jackson.cor | 2.21.7    | [2.18.12] | Maven |
|                 |            | e:jackson-databind        |         | e:jackson-databind        |           | [2.21.8]  |       |
|                 |            |                           |         |                           |           | [2.22.4]  |       |
+-----------------+------------+---------------------------+---------+---------------------------+-----------+-----------+-------+
| CVE-2026-49844  | 🎃Medium   | org.apache.logging.log4j: | 2.26.0  | org.apache.logging.log4j: | 2.26.0    | [2.25.5]  | Maven |
|                 |            | log4j-api                 |         | log4j-api                 |           | [2.26.1]  |       |
+-----------------+------------+---------------------------+---------+---------------------------+-----------+-----------+-------+
License Compliance Violations
+---------------------------------------------+
| No license compliance violations were found |
+---------------------------------------------+
Operational Risk Violations
+-------------------------------------------+
| No operational risk violations were found |
+-------------------------------------------+
13:00:02 [Info] Trace ID for JFrog Platform logs: d183bb7827a931da
13:00:02 [Error] One or more of the detected violations are configured to fail the build that including them
Cleaning up project directory and file based variables
00:00
ERROR: Job failed: exit code 3
