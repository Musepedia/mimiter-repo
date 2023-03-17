# mimiter-repo
本仓库包含多个Java项目之间共用的包，通过Nexus部署在测试服务器上

## Notes
`groupId`统一填写`com.mimiter`

## Usage
修改`~/.m2/settings.xml`，添加Nexus后台的username和password

```xml
<settings>
    <servers>
        <server>
            <id>nexus</id>
            <username>[USERNAME]</username>
            <password>[PASSWORD]</password>
        </server>
    </servers>
</settings>
```

### 下载
向`pom.xml`中添加

```xml
<project>
    <repositories>
        <repository>
            <id>nexus</id>
            <url>http://81.68.95.37:8081/repository/maven-releases/</url>
        </repository>
    </repositories>
</project>
```
随后，添加相应的dependency即可从私有maven服务器上下载相应的包了。

### 部署
向`pom.xml`中添加

```xml
<project>
    <distributionManagement>
        <repository>
            <id>nexus</id>
            <url>http://81.68.95.37:8081/repository/maven-releases/</url>
        </repository>
    </distributionManagement>
</project>
```

随后，运行`mvn deploy`即可~~（默认情况下，请通过Github Actions部署，不需要手动部署）~~。