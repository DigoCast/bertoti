# Pattern (Observer):
O padrão Observer é um padrão de projeto comportamental que define uma relação de dependência um-para-muitos entre objetos, de forma que quando o estado de um objeto (sujeito) muda, todos os seus dependentes (observadores) são notificados automaticamente. Ele é usado para desacoplar o objeto que gera a mudança daqueles que precisam reagir a ela, permitindo que novos observadores sejam adicionados ou removidos sem alterar o código do sujeito. Esse padrão é comum em sistemas baseados em eventos, interfaces gráficas e notificações, pois facilita a comunicação entre componentes sem criar dependências diretas.

## Exemplo pratico em java:

```java
import java.util.ArrayList;
import java.util.List;

// Interface Observer
interface Observer {
    void update(String mensagem);
}

// Interface Subject
interface Subject {
    void adicionar(Observer o);
    void remover(Observer o);
    void notificar(String mensagem);
}

// Classe concreta do Subject
class Canal implements Subject {
    private List<Observer> inscritos = new ArrayList<>();

    @Override
    public void adicionar(Observer o) {
        inscritos.add(o);
    }

    @Override
    public void remover(Observer o) {
        inscritos.remove(o);
    }

    @Override
    public void notificar(String mensagem) {
        for (Observer o : inscritos) {
            o.update(mensagem);
        }
    }
}

// Classe concreta do Observer
class Usuario implements Observer {
    private String nome;

    public Usuario(String nome) {
        this.nome = nome;
    }

    @Override
    public void update(String mensagem) {
        System.out.println(nome + " recebeu notificação: " + mensagem);
    }
}

// Demonstração do padrão
public class ExemploPattern {
    public static void main(String[] args) {
        Canal canal = new Canal();

        Usuario u1 = new Usuario("Diego");
        Usuario u2 = new Usuario("Marcos");

        canal.adicionar(u1);
        canal.adicionar(u2);

        canal.notificar("Novo vídeo disponível!");
    }
}

```
O sujeito (Canal) não sabe nada sobre os observadores além da interface Observer. Os observadores podem ser adicionados ou removidos livremente, mantendo baixo acoplamento e alta flexibilidade.
