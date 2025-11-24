<h2>MVC (Model-View-Controller)</h2>

<p>O MVC é um padrão arquitetural que visa a separação de responsabilidades (Separation of Concerns) em uma aplicação. Ele divide o sistema em três componentes principais para garantir que as alterações na lógica de negócio (Model) ou na interface do usuário (View) não afetem diretamente o código de controle (Controller), promovendo baixo acoplamento e flexibilidade.</p>

---

<h3> Estrutura e Funções no Contexto de Padrões </h3>

| Componente | Responsabilidade Principal | Padrões Envolvidos |
| :--- | :--- | :--- |
| "Model" | "Dados e Lógica de Negócio. Notifica a View quando os dados mudam." | "Observer (Sujeito)" |
| "View" | "Interface do Usuário. Observa o Model para se atualizar automaticamente." | "Observer (Observador)" |
| "Controller" | "Processamento de Entrada. Define a estratégia de manipulação do Model." | "Strategy" |

---

<h3> Unindo Observer e Strategy no MVC </h3>
<p>O poder do MVC reside na maneira como ele aplica padrões comportamentais:

- Model e View (Observer): A View se inscreve no Model. Quando o Controller altera o Model, este notifica todas as Views registradas. A View, então, busca os novos dados no Model e se atualiza. O Model não precisa saber quem são as Views concretas.

- Controller (Strategy): O Controller encapsula a estratégia de como a entrada do usuário será convertida em uma ação do Model (Ex: salvar, deletar, formatar). Diferentes controladores (estratégias) podem ser usados para diferentes interações, sem alterar o Model ou a View.</p>
  

<h3>Exemplo em codigo:</h3>

```java
import java.util.ArrayList;
import java.util.List;

// Interface Observer
interface ViewObserver {
    void update();
}

// Model (O Sujeito/Observable)
class ContadorModel {
    private int valor = 0;
    private List<ViewObserver> observers = new ArrayList<>();

    public void addObserver(ViewObserver o) {
        observers.add(o);
    }

    public int getValor() {
        return valor;
    }

    public void incrementar() {
        this.valor++;
        notificar(); 
    }

    private void notificar() {
        for (ViewObserver o : observers) {
            o.update();
        }
    }
}

// View (O Observador concreto)
class ConsoleView implements ViewObserver {
    private ContadorModel model;

    public ConsoleView(ContadorModel model) {
        this.model = model;
        this.model.addObserver(this);
    }

    @Override
    public void update() {
        System.out.println("[VIEW] O contador atualizado é: " + model.getValor());
    }
}
```

```java
// Controller (Responsável por processar a entrada)
class IncrementoController {
    private ContadorModel model;

    public IncrementoController(ContadorModel model) {
        this.model = model;
    }

    public void receberComando(String comando) {
        if ("INCREMENTAR".equals(comando)) {
            System.out.println("[CONTROLLER] Comando recebido. Alterando Model...");
            model.incrementar();
        }
    }
}
```
Exemplo Aplicacao:

```java
public class AplicacaoMVC {
    public static void main(String[] args) {
        // 1. Cria o Model
        ContadorModel model = new ContadorModel();
        
        // 2. Cria a View e a registra no Model
        ConsoleView view = new ConsoleView(model); 
        
        // 3. Cria o Controller e injeta o Model
        IncrementoController controller = new IncrementoController(model); 

        // -- Início da Interação --
        
        // Ação 1 do Usuário
        controller.receberComando("INCREMENTAR");
        
        // Ação 2 do Usuário
        controller.receberComando("INCREMENTAR");
        
        // Ação 3 (ignorada)
        controller.receberComando("OUTRO");
    }
}

// saida esperada: 
[CONTROLLER] Comando recebido. Alterando Model...
[VIEW] O contador atualizado é: 1
[CONTROLLER] Comando recebido. Alterando Model...
[VIEW] O contador atualizado é: 2
```
