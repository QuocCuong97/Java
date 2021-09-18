# Maven Apache
## **1) Giới thiệu** <img src=https://i.imgur.com/HTwRbDU.png align=right width=20%>
- Trang chủ : https://maven.apache.org/
- Phiên bản mới nhất : `3.8.2`
- **Maven** là công cụ quản lý và thiết lập tự động 1 dự án phần mềm. Chủ yếu dùng cho các lập trình viên **Java**, nhưng nó cũng có thể được dùng để xây dựng và quản lý các dự án dùng C#, Ruby, Scala hay ngôn ngữ khác.
- **Maven** phục vụ mục đích tương tự như **Apache Ant**, nhưng nó dựa trên khái niệm khác và cách hoạt động khác.
- **Maven** hỗ trợ việc tự động hóa các quá trình tạo dự án ban đầu, thực hiện biên dịch, kiểm thử, đóng gói và triển khai sản phẩm.
- Được phát triển bằng ngôn ngữ Java cho phép Maven chạy trên nhiều nền tảng khác nhau: Windows, Linux và Mac OS...
## **2) Cách hoạt động của Maven**
- **Maven** dùng khái niệm **Project Object Model (POM)** để mô tả việc build project, các thành phần phụ thuộc và các module. Nó định nghĩa trước các target cho việc khai báo task, trình biên dịch, đóng gói và thứ tự hoạt động để mọi việc diến ra tốt nhất.
- Trong mỗi project **Maven** tạo ra một file `.pom`, trong file này định nghĩa ra những task như task khi chạy test, task khi build và khi chạy **Maven** sẽ dựa vào những định nghĩa này để thao tác với project.
- **VD :**
    ```xml
    <!-- .pom -->
    <project>
      <!-- model version is always 4.0.0 for Maven 2.x POMs -->
      <modelVersion>4.0.0</modelVersion>

      <!-- project coordinates, i.e. a group of values which
        uniquely identify this project -->

      <groupId>com.mycompany.app</groupId>
      <artifactId>my-app</artifactId>
      <version>1.0</version>

      <!-- library dependencies -->

      <dependencies>
        <dependency>

        <!-- coordinates of the required library -->

        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>3.8.1</version>

        <!-- this dependency is only used for running and compiling tests -->

        <scope>test</scope>

        </dependency>
      </dependencies>
    </project>
    ```
## **3) Tại sao cần Maven ?**
- Khi một project do nhiều nhóm phát triển ví dụ có 2 team cùng tham gia dự án, 2 team đó ở 2 quốc gia khác nhau vì thế chúng ta luôn cần có một sự liên lạc để thông nhất trong việc lập trình vì thế phải có một cái chuẩn nào đó để tất cả mọi người cùng tuân theo, như trong việc sử dụng những thư viện nào, version của thư viện tất cả những thứ như vậy đều được Maven quản lý.
- Đối với những hệ thống lớn, phức tạp sử dụng nhiều thư viện lại đòi hỏi phải release liên tục cho nên công việc đóng gói (build & deploy), quản lý, nâng cấp và bào trì chúng rất mất thời gian, và lúc đó ta có Maven.
## **4) Cài đặt Maven**
### **4.1) Cài đặt trên Linux**
- Cài đặt trên **CentOS/RHEL 7** :
    ```
    # yum install maven -y
    ```
- Cài đặt trên **Ubuntu** :
    ```
    $ sudo apt install maven -y
    ```
- Kiểm tra phiên bản **Maven** đã cài đặt :
    ```
    # mvn --version
    ```
    <img src=https://i.imgur.com/U9PRwK9.png>
### **4.2) Cài đặt trên Windows**
## **5) Khởi tạo một Maven Project**
- Tạo Project:
    ```
    mvn archetype:generate -DgroupId=com.mycompany.app
        -DartifactId=my-app
        -DarchetypeArtifactId=maven-archetype-quickstart
        -DinteractiveMode=false
    ```
    - Trong đó :
        - `groupId` : thường đặt theo tên của tổ chức hoặc nhóm tạo ra dự án
        - `artifactId` : thường lấy theo tên viết tắt của dự án.
        - `archetypeArtifactId` : là loại dự án sẽ được tạo, Maven cung cấp nhiều kiểu mẫu có sẵn cho người dùng lựa chọn khi khởi tạo.
## **6) Cấu trúc file POM XML**
- `<groupId>`, `<artifactId>`, `<version>` : bộ ba thông tin để mô tả tên, version của project.
    ```xml
    <groupId>com.framgia.maven</groupId> (namespace)
    <artifactId>helloworld</artifactId> (tên project)
    <version>1.0</version> (vesion)
    ```
- `<packaging>` : Định nghĩa định dạng khi đóng gói thành phần, có thể là `.jar`, `.war`, `.ear`… 
    ```xml
    <packaging>jar</packaging>  (đóng gói thành .jar )
    ```
- `<dependency>` : nơi khai báo các thư viện sử dụng trong dự án
    ```xml
    <dependencies>
      <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>3.8.1</version>
        <scope>test</scope>
      </dependency>
    </dependencies>
    ```
- `<plugins>` : định nghĩa những Plugin sử dụng trong project trong dự án:
    ```xml
    <build>
      <plugins>
        <plugin>
          <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <configuration>
              <archive>
                <manifest>
                <addClasspath>true</addClasspath>
                <classpathPrefix>lib/</classpathPrefix>
                <mainClass>com.framgia.app.App</mainClass>
                </manifest>
              </archive>
            <source>1.5</source>
            <target>1.5</target>
            </configuration>
          <version>2.3.2</version>
        </plugin>
      </plugins>
    </build>
    ```
## **7) Dependency Trong Maven**
- Dependency chính là cách import thư viện vào project thông qua Maven
- Cơ chế import thư viện thông qua maven.
    - Ví dụ để import thư viện redis, bình thường ta sẽ dowload file redis.jar về rồi buildpath trong eclipse, nhưng với thẻ dependency, Maven sẽ tự động dowload thư viện đó về thư mục ~/.m2 trên máy local và buildpath vào project.
    - http://mvnrepository.com/artifact/redis.clients/jedis.
    - Thư mục ~/.m2/repository Sẽ chứa tất cả các thư viện mà Maven dowload về từ server center.
- Các Dependency sẽ tự động được buildpath trong Eclipse.
    ```xml
    <dependency>
      <groupId>redis.clients</groupId>
      <artifactId>jedis</artifactId>
      <version>2.7.2</version>
    </dependency>
    ```
## **8) Các lệnh cơ bản trong Maven**
- Build project với maven:
    ```
    mvn package
    ```
- Deploy to Tomcat:
    ```
    mvn tomcat:deploy
    ```
- Tạo file .project để có thể import vào eclipse:
    ```
    mvn eclipse:eclipse
    ```
- Chạy unit test :
    ```
    mvn test
    ```
- Clean project :
    ```
    mvn clean
    ```
## **9) Demo Project**
- **B1 :** Khởi tạo một project :
    ```
    mvn archetype:generate -DgroupId=com.mycompany.app
        -DartifactId=my-app
        -DarchetypeArtifactId=maven-archetype-quickstart
        -DinteractiveMode=false
    ```
    - Nội dung file `Main.java` :
        ```java
        package com.mycompany.app;

        /**
         * Hello world!
        *
        */
        public class App
        {
            public static void main( String[] args )
            {
                System.out.println( "Hello World!" );
            }
        }
        ```
- **B2 :** Thay đổi `.pom`, add thêm plugin để build project:
    ```xml
    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
      <modelVersion>4.0.0</modelVersion>
      <groupId>com.mycompany.app</groupId>
      <artifactId>my-app</artifactId>
      <packaging>jar</packaging>
      <version>1.0</version>
      <name>my-app</name>
      <url>http://maven.apache.org</url>
      <dependencies>
        <dependency>
          <groupId>junit</groupId>
          <artifactId>junit</artifactId>
          <version>3.8.1</version>
          <scope>test</scope>
        </dependency>
      </dependencies>

      <build>
        <plugins>
          <plugin>
          <!-- Build an executable JAR -->
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-jar-plugin</artifactId>
            <version>2.4</version>
            <configuration>
              <archive>
                <manifest>
                  <addClasspath>true</addClasspath>
                  <classpathPrefix>lib/</classpathPrefix>
                  <mainClass>com.mycompany.app.App</mainClass>
                </manifest>
              </archive>
            </configuration>
          </plugin>
        </plugins>
      </build>
    </project>
    ```
- **B3 :** Build project :
    ```
    mvn package
    ```
- **B4 :** Run project :
    ```
    java -jar [file_dot_jar]
    ```
    