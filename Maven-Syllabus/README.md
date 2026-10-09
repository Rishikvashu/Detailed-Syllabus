# 📦 Maven for DevOps: Complete Syllabus

A module-by-module Maven roadmap, from first `pom.xml` to CI/CD pipelines and artifact repositories. Tick the boxes as you go (`- [ ]` → `- [x]`).

> **Rule:** build a real project for every module. Read the output of `mvn -X` and `help:effective-pom` until nothing feels like magic.

**Prerequisites:** basic Linux, basic Java (compile, run, packages, JARs), Git.

## 📌 How to Use This Roadmap

| Priority | Modules | Why |
|---|---|---|
| 🟢 **Core (start here)** | 01–07 | Asked in almost every DevOps interview |
| 🟡 **Next** | 08–11, 14 | Real project and team workflows |
| 🔴 **Advanced** | 12, 13, 15–17 | CI/CD, releases, supply-chain security |
| 🏁 **Finish with** | 18–20 | Troubleshooting, comparison, capstones |

## 📑 Table of Contents

1. [Build Tool Fundamentals](#01-build-tool-fundamentals)
2. [Installation & Setup](#02-installation--setup)
3. [Project Structure & POM](#03-project-structure--pom)
4. [Dependency Management](#04-dependency-management)
5. [Build Lifecycle](#05-build-lifecycle)
6. [Plugins & Goals](#06-plugins--goals)
7. [Command Line Essentials](#07-command-line-essentials)
8. [Repositories](#08-repositories)
9. [Properties, Profiles & Resource Filtering](#09-properties-profiles--resource-filtering)
10. [Multi-Module Projects](#10-multi-module-projects)
11. [Testing & Code Quality](#11-testing--code-quality)
12. [Packaging & Artifacts](#12-packaging--artifacts)
13. [Versioning & Releases](#13-versioning--releases)
14. [settings.xml Deep Dive](#14-settingsxml-deep-dive)
15. [Maven in CI/CD](#15-maven-in-cicd)
16. [Security & Supply Chain](#16-security--supply-chain)
17. [Custom Plugins & Archetypes](#17-custom-plugins--archetypes)
18. [Performance & Troubleshooting](#18-performance--troubleshooting)
19. [Maven vs Other Build Tools](#19-maven-vs-other-build-tools)
20. [Capstones & Interview Prep](#20-capstones--interview-prep)

---

## 01. Build Tool Fundamentals

### 1.1 Why Build Tools
- [ ] Manual `javac` / `jar` workflow and its problems
- [ ] Dependency hell, reproducible builds, standard layout
- [ ] Ant vs Maven vs Gradle (overview)

### 1.2 Maven Philosophy
- [ ] Convention over configuration
- [ ] Declarative builds (what, not how)
- [ ] Project Object Model (POM) concept
- [ ] Central repository and artifact coordinates

### 1.3 Java Basics You Need
- [ ] JDK vs JRE vs JVM
- [ ] Packages, classpath, JAR / WAR / EAR
- [ ] `javac`, `java`, `jar` commands
- [ ] Java versions and LTS releases

---

## 02. Installation & Setup

### 2.1 Install JDK
- [ ] OpenJDK / Temurin / Corretto, installing on Linux (apt, dnf, tarball)
- [ ] `JAVA_HOME`, `PATH`, `update-alternatives`, SDKMAN!
- [ ] Multiple JDKs and switching between them

### 2.2 Install Maven
- [ ] Binary tarball install (`/opt/maven`), package manager install
- [ ] `MAVEN_HOME`, `PATH`, `mvn -version`
- [ ] Maven directory layout (`bin`, `conf/settings.xml`, `lib`, `boot`)
- [ ] `~/.m2` folder (`repository`, `settings.xml`, `toolchains.xml`)

### 2.3 Maven Wrapper
- [ ] `mvnw` / `mvnw.cmd`, `.mvn/wrapper/maven-wrapper.properties`
- [ ] Generating the wrapper (`mvn wrapper:wrapper`)
- [ ] Why wrapper matters in CI (pinned Maven version)

### 2.3 IDE Integration
- [ ] IntelliJ / Eclipse / VS Code Maven support
- [ ] Importing, reloading, and running goals from the IDE

---

## 03. Project Structure & POM

### 3.1 Standard Directory Layout
- [ ] `src/main/java`, `src/main/resources`
- [ ] `src/test/java`, `src/test/resources`
- [ ] `src/main/webapp` (WAR projects)
- [ ] `target/` (classes, test-classes, artifacts, surefire-reports)

### 3.2 Creating a Project
- [ ] `mvn archetype:generate` (quickstart, webapp)
- [ ] Interactive vs batch mode
- [ ] Creating a POM by hand

### 3.3 POM Anatomy
- [ ] `modelVersion`, `groupId`, `artifactId`, `version`, `packaging`
- [ ] `name`, `description`, `url`, `licenses`, `developers`, `scm`
- [ ] `properties`, `dependencies`, `dependencyManagement`
- [ ] `build` (plugins, pluginManagement, resources, finalName)
- [ ] `profiles`, `repositories`, `pluginRepositories`, `distributionManagement`
- [ ] `modules`, `parent`

### 3.4 Coordinates (GAV)
- [ ] `groupId` naming (reverse domain), `artifactId`, `version`
- [ ] Classifier and type
- [ ] How coordinates map to repository paths

### 3.5 POM Inheritance
- [ ] Parent POM and `relativePath`
- [ ] Super POM (default values)
- [ ] Effective POM (`mvn help:effective-pom`)
- [ ] What is inherited and what is not
- [ ] Inheritance vs aggregation

---

## 04. Dependency Management

### 4.1 Declaring Dependencies
- [ ] `<dependency>` element, GAV, `type`, `classifier`
- [ ] Finding artifacts on Maven Central (search.maven.org, mvnrepository)
- [ ] Adding, updating, and removing dependencies

### 4.2 Scopes
- [ ] `compile` (default), `provided`, `runtime`, `test`
- [ ] `system` (and why to avoid it), `import` (BOMs)
- [ ] Scope effect on classpath at compile, test, and runtime

### 4.3 Transitive Dependencies
- [ ] How transitive resolution works
- [ ] Dependency mediation: nearest definition wins, first declaration wins
- [ ] Scope propagation table
- [ ] `<optional>true</optional>`
- [ ] `<exclusions>` and when to use them

### 4.4 Dependency Management Section
- [ ] `dependencyManagement` vs `dependencies`
- [ ] Centralizing versions in a parent POM
- [ ] BOMs (`<scope>import</scope>`, `<type>pom</type>`), e.g. Spring Boot BOM

### 4.5 Versions
- [ ] Fixed versions, version ranges (`[1.0,2.0)`) and risks
- [ ] `SNAPSHOT` vs release versions
- [ ] `LATEST` / `RELEASE` (deprecated, avoid)
- [ ] Version ordering and qualifiers (`-alpha`, `-RC1`, `.Final`)

### 4.6 Analyzing Dependencies
- [ ] `mvn dependency:tree` (`-Dverbose`, `-Dincludes`)
- [ ] `dependency:analyze` (used-undeclared, unused-declared)
- [ ] `dependency:resolve`, `dependency:copy-dependencies`, `dependency:go-offline`
- [ ] Detecting version conflicts and duplicate classes
- [ ] `maven-enforcer-plugin` (`dependencyConvergence`, `banDuplicatePomDependencyVersions`)

---

## 05. Build Lifecycle

### 5.1 Core Concepts
- [ ] Lifecycle → phases → goals → plugins
- [ ] Phases run in order, including all earlier phases
- [ ] Plugin goal bound to a phase via `<executions>`

### 5.2 Three Built-in Lifecycles
- [ ] **clean:** `pre-clean`, `clean`, `post-clean`
- [ ] **default:** the full build lifecycle (below)
- [ ] **site:** `site`, `site-deploy`

### 5.3 Default Lifecycle Phases
- [ ] `validate`
- [ ] `initialize`, `generate-sources`, `process-sources`
- [ ] `generate-resources`, `process-resources`
- [ ] `compile`, `process-classes`
- [ ] `generate-test-sources`, `process-test-resources`, `test-compile`
- [ ] `test`
- [ ] `prepare-package`, `package`
- [ ] `pre-integration-test`, `integration-test`, `post-integration-test`
- [ ] `verify`
- [ ] `install`
- [ ] `deploy`

### 5.4 Default Bindings per Packaging
- [ ] `jar`, `war`, `pom`, `ear` default plugin bindings
- [ ] Viewing bindings (`mvn help:describe -Dcmd=package`)

### 5.5 Commonly Used Combinations
- [ ] `mvn clean install`, `mvn clean package`, `mvn verify`
- [ ] `mvn clean deploy`
- [ ] Difference between `package`, `install`, and `deploy`

---

## 06. Plugins & Goals

### 6.1 Plugin Basics
- [ ] Plugin = collection of goals (mojos)
- [ ] Core plugins vs third-party plugins
- [ ] Invoking: `mvn plugin:goal` (e.g. `mvn compiler:compile`)
- [ ] Plugin coordinates and version pinning
- [ ] `pluginManagement` vs `plugins`
- [ ] `mvn help:describe -Dplugin=...`

### 6.2 Core Plugins
- [ ] `maven-clean-plugin`
- [ ] `maven-resources-plugin`
- [ ] `maven-compiler-plugin` (`source`, `target`, `release`, `-parameters`, annotation processors)
- [ ] `maven-surefire-plugin` (unit tests)
- [ ] `maven-failsafe-plugin` (integration tests)
- [ ] `maven-jar-plugin`, `maven-war-plugin`
- [ ] `maven-install-plugin`, `maven-deploy-plugin`
- [ ] `maven-site-plugin`

### 6.3 Packaging Plugins
- [ ] `maven-shade-plugin` (uber JAR, relocation, transformers)
- [ ] `maven-assembly-plugin` (descriptors, ZIP/TAR distributions)
- [ ] `spring-boot-maven-plugin` (repackage, `build-image`)
- [ ] `maven-dependency-plugin` (copy, unpack)
- [ ] `jib-maven-plugin` (container images without Docker)

### 6.3 Utility Plugins
- [ ] `maven-enforcer-plugin` (Java version, Maven version, banned dependencies)
- [ ] `versions-maven-plugin` (`display-dependency-updates`, `set`, `use-latest-releases`)
- [ ] `maven-help-plugin`
- [ ] `exec-maven-plugin`, `build-helper-maven-plugin`
- [ ] `git-commit-id-plugin` (embedding build info)
- [ ] `maven-antrun-plugin`

### 6.4 Binding Goals to Phases
- [ ] `<executions>`, `<id>`, `<phase>`, `<goals>`, `<configuration>`
- [ ] Plugin-level vs execution-level configuration
- [ ] Execution order within one phase

---

## 07. Command Line Essentials

### 7.1 Everyday Commands
- [ ] `mvn clean`, `compile`, `test`, `package`, `verify`, `install`, `deploy`
- [ ] `mvn -v` / `--version`
- [ ] `mvn validate`

### 7.2 Important Flags
- [ ] `-DskipTests` vs `-Dmaven.test.skip=true`
- [ ] `-o` (offline), `-U` (force update snapshots), `-q` (quiet)
- [ ] `-X` (debug), `-e` (errors), `-B` (batch mode), `-ntp` (no transfer progress)
- [ ] `-f <pom>`, `-P<profile>`, `-D<prop>=<value>`
- [ ] `-T 1C` (parallel builds)
- [ ] `-fae`, `-ff`, `-fn` (failure behavior)
- [ ] `-rf :module` (resume from)
- [ ] `-pl`, `-am`, `-amd` (selective builds)
- [ ] `-s <settings>`, `-gs <global settings>`

### 7.3 Running Tests Selectively
- [ ] `-Dtest=MyTest`, `-Dtest=MyTest#method`, `-Dtest='*IT'`
- [ ] `-DfailIfNoTests=false` / `-Dsurefire.failIfNoSpecifiedTests=false`
- [ ] Tags/groups (JUnit 5 `-Dgroups`)

### 7.4 Project Config Files
- [ ] `.mvn/maven.config`, `.mvn/jvm.config`, `.mvn/extensions.xml`
- [ ] `MAVEN_OPTS`, `MAVEN_ARGS`

### 7.5 Help & Inspection
- [ ] `help:effective-pom`, `help:effective-settings`
- [ ] `help:active-profiles`, `help:all-profiles`
- [ ] `help:evaluate -Dexpression=project.version -q -DforceStdout`

---

## 08. Repositories

### 8.1 Repository Types
- [ ] Local (`~/.m2/repository`)
- [ ] Central (Maven Central)
- [ ] Remote (company / third-party)
- [ ] Repository layout (groupId path, `maven-metadata.xml`, checksums)

### 8.2 Resolution Flow
- [ ] Local → remote lookup order
- [ ] Release vs snapshot repositories and update policies
- [ ] `_remote.repositories`, `*.lastUpdated` files, `-U`

### 8.3 Declaring Repositories
- [ ] `<repositories>` and `<pluginRepositories>` in the POM
- [ ] `<releases>` / `<snapshots>` policies (`updatePolicy`, `checksumPolicy`)
- [ ] Why POM repositories are discouraged (prefer mirrors)

### 8.4 Mirrors
- [ ] `<mirror>` in `settings.xml`, `mirrorOf` patterns (`*`, `central`, `external:*`)
- [ ] Routing all traffic through an internal proxy

### 8.5 Repository Managers
- [ ] Sonatype Nexus Repository (hosted, proxy, group)
- [ ] JFrog Artifactory
- [ ] AWS CodeArtifact, GitHub Packages, GitLab Package Registry
- [ ] Installing and configuring Nexus (Docker/EC2)
- [ ] Repository policies, cleanup, blob stores, backups

### 8.6 Publishing Artifacts
- [ ] `distributionManagement` (`repository`, `snapshotRepository`)
- [ ] `mvn deploy` and server credentials (`<server><id>`)
- [ ] `deploy:deploy-file`, `install:install-file` (third-party JARs)
- [ ] Publishing to Maven Central (Central Portal, GPG signing, sources & javadoc JARs)

---

## 09. Properties, Profiles & Resource Filtering

### 9.1 Properties
- [ ] User-defined `<properties>`
- [ ] Built-ins: `${project.*}`, `${settings.*}`, `${env.*}`, `${java.version}`
- [ ] System properties and `-D` overrides
- [ ] Common properties: `project.build.sourceEncoding`, `maven.compiler.release`

### 9.2 Profiles
- [ ] Defining profiles in `pom.xml`, `settings.xml`, `profiles.xml` (legacy)
- [ ] Activation: `activeByDefault`, `-P`, JDK, OS, property, file exists/missing
- [ ] Deactivating profiles (`-P !profile`)
- [ ] Typical profiles: dev / test / prod, skip-tests, release, sonar, docker
- [ ] Profile pitfalls (non-portable builds, `activeByDefault` quirks)

### 9.3 Resource Filtering
- [ ] `<resources>` and `<filtering>true`
- [ ] Replacing `${...}` in `application.properties`
- [ ] Filtering with profile-specific property files
- [ ] Binary file corruption pitfalls (`nonFilteredFileExtensions`)
- [ ] Spring Boot `@...@` delimiter

---

## 10. Multi-Module Projects

### 10.1 Concepts
- [ ] Aggregator (`<modules>`) vs parent (`<parent>`)
- [ ] Packaging type `pom`
- [ ] Typical layout (`parent`, `core`, `api`, `web`, `bom`)

### 10.2 Reactor
- [ ] Build order and dependency graph
- [ ] Reactor summary and failure handling
- [ ] `-pl`, `-am`, `-amd`, `-rf`, `-T`
- [ ] Inter-module dependencies and version alignment

### 10.3 Managing Versions Across Modules
- [ ] `dependencyManagement` in parent
- [ ] Shared `pluginManagement`
- [ ] BOM module for consumers
- [ ] CI-friendly versions (`${revision}`, `flatten-maven-plugin`)

### 10.4 Best Practices
- [ ] Keep parents lean, avoid circular dependencies
- [ ] Naming and structure conventions
- [ ] Company-wide parent POM design

---

## 11. Testing & Code Quality

### 11.1 Unit Testing
- [ ] JUnit 4 / JUnit 5 / TestNG with Surefire
- [ ] Naming conventions (`*Test`, `Test*`, `*Tests`)
- [ ] Test reports (`target/surefire-reports`)
- [ ] Parallel tests, `forkCount`, `reuseForks`, `argLine`
- [ ] `-DskipTests`, `-Dmaven.test.failure.ignore=true`

### 11.2 Integration Testing
- [ ] Failsafe plugin (`*IT`, `integration-test` + `verify` goals)
- [ ] Why integration tests run at `verify` (cleanup in `post-integration-test`)
- [ ] Testcontainers, embedded servers, docker-maven-plugin

### 11.3 Code Coverage
- [ ] JaCoCo (`prepare-agent`, `report`, `check` with thresholds)
- [ ] Aggregated coverage in multi-module builds

### 11.4 Static Analysis & Style
- [ ] Checkstyle, SpotBugs, PMD
- [ ] `maven-enforcer-plugin` rules
- [ ] SonarQube / SonarCloud analysis (`sonar:sonar`, quality gates)
- [ ] Formatters (`spotless-maven-plugin`)

### 11.5 Reporting
- [ ] `mvn site`, project reports (Javadoc, surefire-report, changes)
- [ ] Javadoc generation (`maven-javadoc-plugin`)

---

## 12. Packaging & Artifacts

### 12.1 Packaging Types
- [ ] `jar`, `war`, `ear`, `pom`, `maven-plugin`
- [ ] Executable JAR (`Main-Class` manifest, `maven-jar-plugin` config)

### 12.2 Fat / Uber JARs
- [ ] Shade plugin vs Assembly plugin vs Spring Boot repackage
- [ ] Resource transformers (`ServicesResourceTransformer`) and relocation

### 12.3 WAR Deployments
- [ ] `src/main/webapp`, `web.xml`, `failOnMissingWebXml`
- [ ] Deploying to Tomcat (manual, Tomcat Maven plugin, Cargo)

### 12.4 Additional Artifacts
- [ ] Sources JAR (`maven-source-plugin`), Javadoc JAR
- [ ] Test JAR (`test-jar` goal)
- [ ] Classifiers and attached artifacts (`build-helper:attach-artifact`)

### 12.5 Containerization
- [ ] Multi-stage Dockerfile with `mvn package`
- [ ] Layer caching (`dependency:go-offline`, copying `pom.xml` first)
- [ ] Jib, Spring Boot `build-image` (Buildpacks)
- [ ] Pushing images to ECR / Docker Hub from Maven

### 12.6 Reproducible Builds
- [ ] `project.build.outputTimestamp`
- [ ] Verifying identical output across machines

---

## 13. Versioning & Releases

### 13.1 Version Strategy
- [ ] Semantic Versioning (MAJOR.MINOR.PATCH)
- [ ] `-SNAPSHOT` lifecycle and meaning
- [ ] Release, snapshot, and hotfix flows

### 13.2 Maven Release Plugin
- [ ] `release:prepare` (tags, version bumps, SCM commits)
- [ ] `release:perform`, `release:rollback`, `release:clean`
- [ ] SCM configuration (`<scm>`, connection, developerConnection, tag)
- [ ] Common failures (dirty working tree, SNAPSHOT dependencies, credentials)

### 13.3 Versions Plugin
- [ ] `versions:set -DnewVersion=...`, `versions:commit`, `versions:revert`
- [ ] `versions:display-dependency-updates`, `display-plugin-updates`
- [ ] `versions:update-properties`

### 13.4 CI-Friendly Versioning
- [ ] `${revision}`, `${sha1}`, `${changelist}`
- [ ] `flatten-maven-plugin`
- [ ] Building versions from Git tags / pipeline variables

### 13.5 Dependency Updates
- [ ] Dependabot, Renovate
- [ ] Update policy and regression testing

---

## 14. settings.xml Deep Dive

### 14.1 Levels and Precedence
- [ ] Global (`${maven.home}/conf/settings.xml`) vs user (`~/.m2/settings.xml`)
- [ ] `-s` and `-gs` overrides, merge behavior

### 14.2 Key Elements
- [ ] `<localRepository>`, `<offline>`, `<interactiveMode>`
- [ ] `<servers>` (id, username, password, token)
- [ ] `<mirrors>`, `<proxies>`
- [ ] `<profiles>`, `<activeProfiles>`
- [ ] `<pluginGroups>`

### 14.3 Credentials Security
- [ ] Password encryption (`mvn --encrypt-master-password`, `settings-security.xml`)
- [ ] Environment-variable placeholders (`${env.NEXUS_PASSWORD}`)
- [ ] Never committing secrets, using CI secret stores

### 14.4 Toolchains
- [ ] `toolchains.xml` and `maven-toolchains-plugin`
- [ ] Building with a specific JDK regardless of `JAVA_HOME`

---

## 15. Maven in CI/CD

### 15.1 Jenkins
- [ ] Installing JDK and Maven (Global Tool Configuration)
- [ ] Freestyle job with Maven build step
- [ ] Declarative pipeline: `tool 'maven'`, `sh 'mvn -B clean verify'`
- [ ] `settings.xml` via Config File Provider plugin
- [ ] Credentials binding for Nexus/Artifactory
- [ ] Publishing JUnit and JaCoCo reports, archiving artifacts
- [ ] Shared libraries for standard Maven pipelines

### 15.2 GitHub Actions / GitLab CI
- [ ] `actions/setup-java` with Maven cache
- [ ] Matrix builds across JDK versions
- [ ] GitLab CI cache for `.m2/repository`

### 15.3 Pipeline Design
- [ ] Stages: build → test → quality gate → package → publish → deploy
- [ ] Batch mode and flags: `-B -ntp -Dstyle.color=never`
- [ ] Caching `~/.m2` (and risks of cache poisoning)
- [ ] Parallel builds and incremental module builds (`-pl -am`)
- [ ] Failing fast and test report publication

### 15.4 Quality Gates & Publishing
- [ ] SonarQube scan and quality-gate wait
- [ ] Deploy snapshots on `main`, releases on tags
- [ ] Promotion between repositories (snapshot → staging → release)

### 15.5 Docker-based CI Builds
- [ ] Official `maven` images, custom build images
- [ ] Multi-stage builds, BuildKit cache mounts for `~/.m2`
- [ ] Build agents on EC2 / Kubernetes (ephemeral pods)

### 15.6 Deployment Hooks
- [ ] Deploy WAR/JAR to EC2, Tomcat, Elastic Beanstalk
- [ ] Image build → push to ECR → deploy to ECS/EKS
- [ ] Artifact traceability (build number, Git SHA in manifest)

---

## 16. Security & Supply Chain

### 16.1 Dependency Vulnerabilities
- [ ] OWASP `dependency-check-maven`
- [ ] `mvn dependency:tree` for impact analysis
- [ ] Snyk, Trivy, GitHub Dependabot alerts
- [ ] Log4Shell-style incident response (find, pin, patch)

### 16.2 Software Bill of Materials
- [ ] CycloneDX Maven plugin (`makeAggregateBom`)
- [ ] SPDX, SBOM storage and consumption

### 16.3 Integrity & Signing
- [ ] Checksums (SHA-1/256, MD5) and `checksumPolicy`
- [ ] GPG signing (`maven-gpg-plugin`), key management
- [ ] Verifying artifact signatures

### 16.4 Safe Resolution
- [ ] Blocking HTTP repositories (Maven 3.8.1+ default)
- [ ] Enforcing an internal mirror for all traffic
- [ ] Dependency confusion / typosquatting risks
- [ ] Pinning plugin and dependency versions
- [ ] Enforcer rules (`requirePluginVersions`, `bannedDependencies`)

### 16.5 Secrets & Access
- [ ] Credentials in CI, least-privilege repository users
- [ ] Rotating tokens, avoiding secrets in `pom.xml`

---

## 17. Custom Plugins & Archetypes

### 17.1 Archetypes
- [ ] Creating an archetype from an existing project (`archetype:create-from-project`)
- [ ] Publishing and using a company archetype

### 17.2 Writing a Plugin
- [ ] `maven-plugin` packaging, `maven-plugin-plugin`
- [ ] Mojo class, `@Mojo`, `@Parameter`, `@Component`
- [ ] Default phase binding, descriptor generation
- [ ] Testing a plugin, publishing it

### 17.3 Extensions
- [ ] `.mvn/extensions.xml` (build cache, tools)
- [ ] Core extensions vs plugins (overview)

### 17.4 Maven 4 Overview
- [ ] Model version 4.1.0, build/consumer POM split
- [ ] Improvements to multi-module builds and CLI
- [ ] Migration considerations from Maven 3.x

---

## 18. Performance & Troubleshooting

### 18.1 Speeding Up Builds
- [ ] `-T 1C`, parallel Surefire, `-o` offline
- [ ] Skipping unneeded work (`-DskipTests`, `-Dmaven.javadoc.skip`)
- [ ] Maven Build Cache Extension
- [ ] Incremental builds (`-pl -am`), `mvnd` (Maven Daemon)
- [ ] Local/proxy repository caching, `MAVEN_OPTS` heap tuning

### 18.2 Common Errors and Fixes
- [ ] `JAVA_HOME is not defined correctly`
- [ ] `Could not resolve dependencies` / `Could not transfer artifact` (network, mirror, credentials)
- [ ] `Non-resolvable parent POM`
- [ ] `Unsupported class file major version` / `invalid target release`
- [ ] `No compiler is provided in this environment`
- [ ] `Failed to execute goal ... maven-surefire-plugin`, `OutOfMemoryError`
- [ ] `401 Unauthorized` / `403 Forbidden` on deploy, `409 Conflict` re-deploying a release
- [ ] `PKIX path building failed` (SSL certificates, truststore)
- [ ] `*.lastUpdated` stuck downloads, corrupted local repo
- [ ] `NoSuchMethodError` / `ClassNotFoundException` from version conflicts
- [ ] Wrong version of a plugin picked up, missing `pluginManagement`

### 18.3 Debugging Method
- [ ] `-X` and `-e` output reading
- [ ] `help:effective-pom` and `help:effective-settings`
- [ ] `dependency:tree -Dverbose`
- [ ] Reproducing with a clean local repo (`-Dmaven.repo.local=/tmp/repo`)
- [ ] `mvnDebug` for plugin debugging

---

## 19. Maven vs Other Build Tools

- [ ] **19.1 Maven vs Gradle:** XML vs Groovy/Kotlin DSL, incremental builds, build cache, flexibility vs convention
- [ ] **19.2 Maven vs Ant (+Ivy):** declarative vs imperative
- [ ] **19.3 Maven vs Bazel:** monorepos, hermetic builds
- [ ] **19.4 Non-Java builds:** npm / pip / Go modules as Maven analogues
- [ ] **19.5 Choosing a tool:** team skills, ecosystem, build time, tooling support
- [ ] **19.6 Migrating:** Maven → Gradle and Ant → Maven (overview)

---

## 20. Capstones & Interview Prep

### 20.1 Hands-on Projects
- [ ] Build a multi-module Spring Boot app (parent, `core`, `api`, `web`) with a BOM
- [ ] Install Nexus on EC2, proxy Maven Central, publish SNAPSHOT and release artifacts
- [ ] Jenkins pipeline: checkout → build → test → JaCoCo → SonarQube → deploy to Nexus
- [ ] Multi-stage Dockerfile and Jib image pushed to ECR
- [ ] Full release flow: `release:prepare` / `release:perform` with Git tag
- [ ] Break-and-fix: 10 deliberate Maven failures (conflict, bad settings, missing parent) and diagnose each
- [ ] Add OWASP dependency-check and SBOM generation to the pipeline

### 20.2 Interview Topics
- [ ] "Explain the Maven build lifecycle and the difference between `package`, `install`, and `deploy`."
- [ ] "What is a POM? What is the Super POM and effective POM?"
- [ ] "Explain dependency scopes and transitive dependency resolution."
- [ ] "`dependencyManagement` vs `dependencies`; parent vs aggregator."
- [ ] "SNAPSHOT vs release versions."
- [ ] "How do you resolve a dependency version conflict?"
- [ ] "How do you speed up a slow Maven build in CI?"
- [ ] "How do you handle credentials for Nexus in Jenkins?"
- [ ] "Surefire vs Failsafe; why does `verify` exist?"
- [ ] "A build works locally but fails in CI. What do you check?"
- [ ] "What is a mirror? Why use a repository manager?"

### 20.3 Quick Reference Cheat Sheet
- [ ] Write your own one-page cheat sheet of the 25 commands and flags you use most

---

## 🚀 What's Next

After Maven, continue with: **Jenkins pipelines → Docker → SonarQube & Nexus → Kubernetes deployments**.
