<h2>Strategy - Pattern</h2>

<p>O padrão Strategy é potencializado ao ser combinado com outros padrões, como o Factory, que encapsula a lógica de qual estratégia escolher, desacoplando o código cliente. Ele também pode atuar em conjunto com o State para gerenciar mudanças de comportamento controladas internamente pelo objeto, ou com o Flyweight para compartilhar instâncias de estratégias sem estado, otimizando o uso de memória. Essas sinergias criam sistemas mais flexíveis e de fácil manutenção.</p>

<h4>Exemplo em codigo:</h4>

```java
public interface FreteStrategy {
    /**
     * Calcula o custo do frete para um determinado peso.
     * @param pesoEmKg O peso do pedido.
     * @return O valor do frete em reais.
     */
    double calcular(double pesoEmKg);
}

```

```java
public class FreteNormal implements FreteStrategy {
    @Override
    public double calcular(double pesoEmKg) {
        return pesoEmKg * 1.25;
    }
}

public class FreteExpresso implements FreteStrategy {
    @Override
    public double calcular(double pesoEmKg) {
        return pesoEmKg * 2.50;
    }
}

public class FreteRetiradaLocal implements FreteStrategy {
    @Override
    public double calcular(double pesoEmKg) {
        return 0.0;
    }
}
```

```java

public class Pedido {
    private double peso;
    private FreteStrategy estrategiaDeFrete; 

    public Pedido(double peso) {
        this.peso = peso;
    }

    /**
     * Permite que o cliente (ou a lógica de negócio) defina a estratégia em tempo de execução.
     * @param estrategiaDeFrete A estratégia de cálculo de frete a ser usada.
     */
    public void setEstrategiaDeFrete(FreteStrategy estrategiaDeFrete) {
        this.estrategiaDeFrete = estrategiaDeFrete;
    }

    /**
     * Delega o cálculo do frete para o objeto Strategy.
     * @return O custo do frete calculado.
     */
    public double calcularFrete() {
        if (estrategiaDeFrete == null) {
            throw new IllegalStateException("A estratégia de frete não foi definida!");
        }
        return estrategiaDeFrete.calcular(this.peso);
    }
}

```

```java
public class LojaVirtual {
    public static void main(String[] args) {
        Pedido pedido = new Pedido(5.0);

        // Cenário 1: O cliente escolhe Frete Normal
        pedido.setEstrategiaDeFrete(new FreteNormal());
        System.out.printf("Custo do Frete Normal: R$ %.2f%n", pedido.calcularFrete()); // Saída: R$ 6,25

        // Cenário 2: O cliente escolhe Frete Expresso
        pedido.setEstrategiaDeFrete(new FreteExpresso());
        System.out.printf("Custo do Frete Expresso: R$ %.2f%n", pedido.calcularFrete()); // Saída: R$ 12,50

        // Cenário 3: O cliente decide retirar na loja
        pedido.setEstrategiaDeFrete(new FreteRetiradaLocal());
        System.out.printf("Custo para Retirada Local: R$ %.2f%n", pedido.calcularFrete()); // Saída: R$ 0,00
    }
}
```
