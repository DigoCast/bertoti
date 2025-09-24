<h2>Strategy - Anti-Pattern</h2>

<p>O principal AntiPattern é o uso excessivo do padrão para lógicas simples e estáticas, onde um if-else seria mais legível e direto, adicionando complexidade desnecessária. Outras armadilhas incluem a criação de um "inferno de estratégias" com um número exagerado de classes minúsculas e difíceis de gerenciar, ou o desenvolvimento de estratégias que dependem excessivamente do estado interno do contexto, quebrando o encapsulamento e criando um forte acoplamento.</p>

<h4>Exemplo em codigo:</h4>

```java
public interface ValidacaoIdadeStrategy {
    boolean validar(int idade);
}

public class ValidacaoMaioridade implements ValidacaoIdadeStrategy {
    @Override
    public boolean validar(int idade) {
        return idade >= 18;
    }
}

public class UsuarioValidador {
    private ValidacaoIdadeStrategy strategy = new ValidacaoMaioridade(); 

    public boolean eValido(int idade) {
        return strategy.validar(idade);
    }
}
```

```java
public class Aplicacao {
    public static void main(String[] args) {
        UsuarioValidador validador = new UsuarioValidador();
        System.out.println("Usuário com 20 anos é válido? " + validador.eValido(20)); 
        System.out.println("Usuário com 17 anos é válido? " + validador.eValido(17)); 
    }
}
```