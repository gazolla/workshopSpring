## Retornando HTML com Thymeleaf

- Crie um novo projeto Spring Boot seguindo os passos 1-3 do Projeto 1.
```
Nome: ThymeleafDemo
```
- Na tela de seleção de dependências, escolha: "Spring Web" e "Thymeleaf".
- Clique em Finish para criar o projeto.
- No pacote `com.workshop.thymeleafdemo`, crie uma nova classe chamada `HelloController`:

```
package com.workshop.thymeleafdemo;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class HelloController {

    @GetMapping("/")
    public String hello(Model model) {
        model.addAttribute("message", "Hello from Thymeleaf!");
        return "hello"; // This refers to hello.html in templates folder
    }
}
```

- Crie uma pasta chamada templates dentro de src/main/resources se ela não existir.
- Dentro da pasta templates, crie um novo arquivo chamado hello.html:

```
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Hello Thymeleaf</title>
</head>
<body>
    <h1 th:text="${message}"></h1>
</body>
</html> 
```

- Execute a aplicação e acesse http://localhost:8080.