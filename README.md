


Building Service: fincore_help_service
Tag: PRE-PROD-01
------------------------------------------------------------
[INFO] Scanning for projects...
[INFO] 
[INFO] Using the MultiThreadedBuilder implementation with a thread count of 12
[INFO] 
[INFO] ----------------------< com.fincore:HelpService >-----------------------
[INFO] Building HelpService 0.0.1-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
Downloading from central: https://repo.maven.apache.org/maven2/dev/langchain4j/langchain4j/1.0.0-alpha1/langchain4j-1.0.0-alpha1.jar
Downloading from central: https://repo.maven.apache.org/maven2/dev/langchain4j/langchain4j-core/1.0.0-alpha1/langchain4j-core-1.0.0-alpha1.jar
Downloading from central: https://repo.maven.apache.org/maven2/org/jspecify/jspecify/0.3.0/jspecify-0.3.0.jar
Downloading from central: https://repo.maven.apache.org/maven2/org/apache/opennlp/opennlp-tools/1.9.4/opennlp-tools-1.9.4.jar
Downloading from central: https://repo.maven.apache.org/maven2/dev/langchain4j/langchain4j-ollama/1.0.0-alpha1/langchain4j-ollama-1.0.0-alpha1.jar
Downloading from central: https://repo.maven.apache.org/maven2/com/squareup/retrofit2/retrofit/2.9.0/retrofit-2.9.0.jar
Downloading from central: https://repo.maven.apache.org/maven2/com/squareup/retrofit2/converter-jackson/2.9.0/converter-jackson-2.9.0.jar
Downloading from central: https://repo.maven.apache.org/maven2/org/jetbrains/kotlin/kotlin-stdlib-common/1.9.24/kotlin-stdlib-common-1.9.24.jar
Downloading from central: https://repo.maven.apache.org/maven2/dev/langchain4j/langchain4j-redis/1.0.0-alpha1/langchain4j-redis-1.0.0-alpha1.jar
Downloading from central: https://repo.maven.apache.org/maven2/redis/clients/jedis/5.0.2/jedis-5.0.2.jar
Downloading from central: https://repo.maven.apache.org/maven2/org/apache/commons/commons-pool2/2.12.0/commons-pool2-2.12.0.jar
Downloading from central: https://repo.maven.apache.org/maven2/org/json/json/20231013/json-20231013.jar
Downloading from snapshot-repo: https://s01.oss.sonatype.org/content/repositories/snapshots/dev/langchain4j/langchain4j-core/1.0.0-alpha1/langchain4j-core-1.0.0-alpha1.jar
Downloading from snapshot-repo: https://s01.oss.sonatype.org/content/repositories/snapshots/org/jspecify/jspecify/0.3.0/jspecify-0.3.0.jar
Downloading from snapshot-repo: https://s01.oss.sonatype.org/content/repositories/snapshots/org/apache/opennlp/opennlp-tools/1.9.4/opennlp-tools-1.9.4.jar
Downloading from snapshot-repo: https://s01.oss.sonatype.org/content/repositories/snapshots/com/squareup/retrofit2/retrofit/2.9.0/retrofit-2.9.0.jar
Downloading from snapshot-repo: https://s01.oss.sonatype.org/content/repositories/snapshots/com/squareup/retrofit2/converter-jackson/2.9.0/converter-jackson-2.9.0.jar
Downloading from snapshot-repo: https://s01.oss.sonatype.org/content/repositories/snapshots/org/jetbrains/kotlin/kotlin-stdlib-common/1.9.24/kotlin-stdlib-common-1.9.24.jar
Downloading from snapshot-repo: https://s01.oss.sonatype.org/content/repositories/snapshots/redis/clients/jedis/5.0.2/jedis-5.0.2.jar
Downloading from snapshot-repo: https://s01.oss.sonatype.org/content/repositories/snapshots/org/apache/commons/commons-pool2/2.12.0/commons-pool2-2.12.0.jar
Downloading from snapshot-repo: https://s01.oss.sonatype.org/content/repositories/snapshots/org/json/json/20231013/json-20231013.jar
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  4.842 s (Wall Clock)
[INFO] Finished at: 2026-06-05T18:45:14+05:30
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal on project HelpService: Could not resolve dependencies for project com.fincore:HelpService:jar:0.0.1-SNAPSHOT
[ERROR] dependency: dev.langchain4j:langchain4j:jar:1.0.0-alpha1 (compile)
[ERROR]         Could not transfer artifact dev.langchain4j:langchain4j:jar:1.0.0-alpha1 from/to central (https://repo.maven.apache.org/maven2): PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target                                                                                                                                                                     
[ERROR] dependency: dev.langchain4j:langchain4j-core:jar:1.0.0-alpha1 (compile)
[ERROR]         Could not transfer artifact dev.langchain4j:langchain4j-core:jar:1.0.0-alpha1 from/to central (https://repo.maven.apache.org/maven2): PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target                                                                                                                                                                
[ERROR]         Could not transfer artifact dev.langchain4j:langchain4j-core:jar:1.0.0-alpha1 from/to snapshot-repo (https://s01.oss.sonatype.org/content/repositories/snapshots): status code: 407, reason phrase: Proxy Authentication Required (407)                                                                                                                                                                                                                 
[ERROR] dependency: org.jspecify:jspecify:jar:0.3.0 (compile)
[ERROR]         Could not transfer artifact org.jspecify:jspecify:jar:0.3.0 from/to central (https://repo.maven.apache.org/maven2): PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target                                                                                                                                                                                  
[ERROR]         Could not transfer artifact org.jspecify:jspecify:jar:0.3.0 from/to snapshot-repo (https://s01.oss.sonatype.org/content/repositories/snapshots): status code: 407, reason phrase: Proxy Authentication Required (407)                                                                                                                                                                                                                                   
[ERROR] dependency: org.apache.opennlp:opennlp-tools:jar:1.9.4 (compile)
[ERROR]         Could not transfer artifact org.apache.opennlp:opennlp-tools:jar:1.9.4 from/to central (https://repo.maven.apache.org/maven2): PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target                                                                                                                                                                       
[ERROR]         Could not transfer artifact org.apache.opennlp:opennlp-tools:jar:1.9.4 from/to snapshot-repo (https://s01.oss.sonatype.org/content/repositories/snapshots): status code: 407, reason phrase: Proxy Authentication Required (407)                                                                                                                                                                                                                        
[ERROR] dependency: dev.langchain4j:langchain4j-ollama:jar:1.0.0-alpha1 (compile)
[ERROR]         Could not transfer artifact dev.langchain4j:langchain4j-ollama:jar:1.0.0-alpha1 from/to central (https://repo.maven.apache.org/maven2): PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target                                                                                                                                                              
[ERROR] dependency: com.squareup.retrofit2:retrofit:jar:2.9.0 (compile)
[ERROR]         Could not transfer artifact com.squareup.retrofit2:retrofit:jar:2.9.0 from/to central (https://repo.maven.apache.org/maven2): PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target                                                                                                                                                                        
[ERROR]         Could not transfer artifact com.squareup.retrofit2:retrofit:jar:2.9.0 from/to snapshot-repo (https://s01.oss.sonatype.org/content/repositories/snapshots): status code: 407, reason phrase: Proxy Authentication Required (407)                                                                                                                                                                                                                         
[ERROR] dependency: com.squareup.retrofit2:converter-jackson:jar:2.9.0 (compile)
[ERROR]         Could not transfer artifact com.squareup.retrofit2:converter-jackson:jar:2.9.0 from/to central (https://repo.maven.apache.org/maven2): PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target                                                                                                                                                               
[ERROR]         Could not transfer artifact com.squareup.retrofit2:converter-jackson:jar:2.9.0 from/to snapshot-repo (https://s01.oss.sonatype.org/content/repositories/snapshots): status code: 407, reason phrase: Proxy Authentication Required (407)                                                                                                                                                                                                                
[ERROR] dependency: org.jetbrains.kotlin:kotlin-stdlib-common:jar:1.9.24 (compile)
[ERROR]         Could not transfer artifact org.jetbrains.kotlin:kotlin-stdlib-common:jar:1.9.24 from/to central (https://repo.maven.apache.org/maven2): PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target                                                                                                                                                             
[ERROR]         Could not transfer artifact org.jetbrains.kotlin:kotlin-stdlib-common:jar:1.9.24 from/to snapshot-repo (https://s01.oss.sonatype.org/content/repositories/snapshots): status code: 407, reason phrase: Proxy Authentication Required (407)                                                                                                                                                                                                              
[ERROR] dependency: dev.langchain4j:langchain4j-redis:jar:1.0.0-alpha1 (compile)
[ERROR]         Could not transfer artifact dev.langchain4j:langchain4j-redis:jar:1.0.0-alpha1 from/to central (https://repo.maven.apache.org/maven2): PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target                                                                                                                                                               
[ERROR] dependency: redis.clients:jedis:jar:5.0.2 (compile)
[ERROR]         Could not transfer artifact redis.clients:jedis:jar:5.0.2 from/to central (https://repo.maven.apache.org/maven2): PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target                                                                                                                                                                                    
[ERROR]         Could not transfer artifact redis.clients:jedis:jar:5.0.2 from/to snapshot-repo (https://s01.oss.sonatype.org/content/repositories/snapshots): status code: 407, reason phrase: Proxy Authentication Required (407)
[ERROR] dependency: org.apache.commons:commons-pool2:jar:2.12.0 (compile)
[ERROR]         Could not transfer artifact org.apache.commons:commons-pool2:jar:2.12.0 from/to central (https://repo.maven.apache.org/maven2): PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target                                                                                                                                                                      
[ERROR]         Could not transfer artifact org.apache.commons:commons-pool2:jar:2.12.0 from/to snapshot-repo (https://s01.oss.sonatype.org/content/repositories/snapshots): status code: 407, reason phrase: Proxy Authentication Required (407)                                                                                                                                                                                                                       
[ERROR] dependency: org.json:json:jar:20231013 (compile)
[ERROR]         Could not transfer artifact org.json:json:jar:20231013 from/to central (https://repo.maven.apache.org/maven2): PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target                                                                                                                                                                                       
[ERROR]         Could not transfer artifact org.json:json:jar:20231013 from/to snapshot-repo (https://s01.oss.sonatype.org/content/repositories/snapshots): status code: 407, reason phrase: Proxy Authentication Required (407)
[ERROR] 
[ERROR] -> [Help 1]
[ERROR] 
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR] 
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/DependencyResolutionException
[ERROR] Command failed: mvn -T 1C clean install -U -DskipTests
============================================================
