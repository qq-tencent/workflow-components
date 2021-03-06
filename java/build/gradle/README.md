## 组件名称：Java Build Gradle

使用 gradle 进行 java 项目构建, 可选地将构建产物上传到指定的二进制仓库.

### 组件参数
#### 入参
- `GIT_CLONE_URL` 必填，源代码地址，如为私有仓库需要授权; 如需使用系统关联的git仓库, 可以从系统提供的全局环境变量中获取: `${_WORKFLOW_GIT_CLONE_URL}`
- `GIT_REF` 非必填，源代码目标提交号或者分支名, 默认为master
- `GRADLE_TASK` 非必填，任务名, 默认任务是 jar
- `ENTRY_FILE` 非必填，构建文件, 默认是build.gradle
- `HUB_REPO` 非必填，构建产物目标二进制仓库, 组件在构建完成后将尝试自动上传构建产物到此仓库, 如果此值为空将不会自动上传
- `HUB_USER` 非必填，上传构建产物对应仓库的用户名, 如果想使用当前主账号, 可以直接设置`_WORKFLOW_FLAG_HUB_TOKEN: true`, 执行引擎将自动注入当前用户名和token
- `HUB_TOKEN` 非必填，上传构建产物对应仓库的用户密码或者token, 同上, 如果设置了`_WORKFLOW_FLAG_HUB_TOKEN: true`, 此入参可以省略
- `ARTIFACT_PATH` 非必填，上传构建产物对应的仓库目录, 默认是仓库根目录
- `ARTIFACT_TAG` 非必填，上传构建产物对应的tag, 默认是latest

#### 出参

- `ARTIFACT` 构建产物结果列表
- `ARTIFACT_URL` 成功上传的构建产物url

### Tag列表及其Dockerfile链接

* 4.9.0-jdk8, latest: [Dockerfile](https://github.com/tencentyun/workflow-components/blob/30478088fd0e6c9578688d0ef3ea02b8cece9fff/java/build/gradle/Dockerfile)

### 源码地址

Java Gradle Build: <https://github.com/tencentyun/workflow-components/tree/master/java/build/gradle>

### 构建:

`docker build -t hub.tencentyun.com/tencenthub/java_build_gradle:latest .`
