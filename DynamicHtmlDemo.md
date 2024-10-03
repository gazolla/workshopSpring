## DynamicHtmlDemo

- Crie um novo projeto Spring Boot:

```
Name: DynamicHtmlDemo
Dependencies: Spring Web
```

- No pacote principal `com.workshop.dynamichtmldemo`, crie uma nova classe chamada `DynamicHtmlController`:

```
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.ResponseBody;

import java.time.LocalDateTime;
import java.util.Random;

@Controller
public class DynamicHtmlController {

    @GetMapping("/dynamic")
    @ResponseBody
    public String generateDynamicHtml() {
        LocalDateTime now = LocalDateTime.now();
        String randomColor = generateRandomColor();

        StringBuilder html = new StringBuilder();
        html.append("<!DOCTYPE html>")
            .append("<html lang='en'>")
            .append("<head>")
            .append("    <meta charset='UTF-8'>")
            .append("    <meta name='viewport' content='width=device-width, initial-scale=1.0'>")
            .append("    <title>Dynamic HTML Page</title>")
            .append("    <style>")
            .append("        body { font-family: Arial, sans-serif; text-align: center; padding-top: 50px; }")
            .append("        .dynamic-content { color: ").append(randomColor).append("; }")
            .append("    </style>")
            .append("</head>")
            .append("<body>")
            .append("    <h1>Welcome to Dynamic HTML Generation</h1>")
            .append("    <p>This page was generated on: <span class='dynamic-content'>").append(now).append("</span></p>")
            .append("    <p>Random Color: <span class='dynamic-content'>").append(randomColor).append("</span></p>")
            .append("</body>")
            .append("</html>");

        return html.toString();
    }

    private String generateRandomColor() {
        Random random = new Random();
        return String.format("#%06x", random.nextInt(0xFFFFFF + 1));
    }
}
```


#### Explicação do código:

- Usamos a anotação @ResponseBody para indicar que o retorno do método deve ser usado diretamente como o corpo da resposta HTTP, em vez de ser interpretado como um nome de view.
- Geramos dinamicamente a data e hora atual e uma cor aleatória.
- Construímos o HTML usando um StringBuilder, incorporando os valores dinâmicos diretamente na string.
- O método generateRandomColor() cria uma cor hexadecimal aleatória.


#### Execute a aplicação:

- Clique com o botão direito no projeto > Run As > Spring Boot App


- Acesse http://localhost:8080/dynamic no seu navegador.

- Cada vez que você atualizar a página, verá uma nova hora e uma nova cor aleatória.
- Este exemplo demonstra como podemos gerar HTML dinamicamente sem usar um mecanismo de template. - É uma técnica útil para páginas simples ou para situações onde você precisa de controle total sobre o HTML gerado.
- Pontos para discussão durante o workshop:

#### Vantagens deste método:

Controle total sobre o HTML gerado
Não requer arquivos de template adicionais
Pode ser útil para gerar emails HTML ou outros conteúdos dinâmicos


#### Desvantagens:

Pode se tornar difícil de manter para páginas HTML mais complexas
Mistura lógica de apresentação com lógica de negócios
Não aproveita as vantagens de um mecanismo de template (como cache, reutilização de fragmentos, etc.)


