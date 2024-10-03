## Hello World com Spring Boot

- Abra o Eclipse.

- Vá para File > New > Spring Starter Project.

- Configure o projeto:

```
Name: HelloWorldSpring
Type: Maven
Java Version: 17
Packaging: Jar
Group: com.workshop
Artifact: helloworldspring
Package: com.workshop.helloworldspring
```

- Na próxima tela, selecione apenas a dependência "Spring Web".

- Clique em Finish para criar o projeto.

- No pacote `com.workshop.helloworldspring`, você verá a classe principal gerada automaticamente. Modifique-a assim:
```
package com.workshop.helloworldspring;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@SpringBootApplication
@RestController
public class HelloworldspringApplication {

    public static void main(String[] args) {
        SpringApplication.run(HelloworldspringApplication.class, args);
    }

    @GetMapping("/")
    public String hello() {
        return "Hello, Spring Boot!";
    }
}
```

- Hello World Spring Boot ProjectClick to open code

- Salve o arquivo e execute a aplicação clicando com o botão direito no projeto > Run As > Spring Boot App.

- Abra um navegador e acesse http://localhost:8080.

- Você deverá ver a mensagem "Hello, Spring Boot!".