We see three critical differences between programming and software engineering: time, scale, and the trade-offs at play. On a software engineering project, engineers need to be more concerned with the passage of time and the eventual need for change. In a software engineering organization, we need to be more concerned about scale and efficiency, both for the software we produce as well as for the organization that is producing it. Finally, as software engineers, we are asked to make more complex decisions with higher-stakes outcomes, often based on imprecise estimates of time and growth.

Comentário:
De acordo com o texto os aspectos mais importantes para um engenheiro de software é a capacidade de organização, ou seja utilizar o tempo ao seu favor e a rapida adaptação de acordo com a situação que se encontra, buscando sempre a melhor entrega de resultados.

Within Google, we sometimes say, “Software engineering is programming integrated over time.” Programming is certainly a significant part of software engineering: after all, programming is how you generate new software in the first place. If you accept this distinction, it also becomes clear that we might need to delineate between programming tasks (development) and software engineering tasks (development, modification, maintenance). The addition of time adds an important new dimension to programming. Cubes aren’t squares, distance isn’t velocity. Software engineering isn’t programming.

Comentário:
Aqui ele diz que de acordo com algumas fontes a engenharia de software é programação com alguns complementos, porem para ele, a programação é uma parte importante mas não é programação, engloba muito mias coisas como por exemplo o desenvolvimento a modificação e a manutenção do software. 

trade-offS:
1-exemplo de trade-off Python x Java - facilidade e sintaxe - Na linguagem de programação Python, temos uma sintaxe simples e clara, o que acelera o desenvolvimento. No entanto, por ser uma linguagem de alto nível, a comunicação com o hardware é mais complexa, tornando o Python menos adequado para projetos grandes e complexos em comparação com linguagens de nível mais baixo. Por outro lado, o Java, que é uma linguagem de nível mais baixo, tem uma sintaxe mais verbosa, fornecendo mais estrutura, uma maior portabilidade e maior velocidade.

2-exemplo de trade-off Linux x Windowns - No sistema operacional Windows, há uma grande quantidade de recursos de segurança para usuários comuns. No entanto, Windows pode ser menos prático e mais difícil de manter em ambientes de servidores. Por outro lado, o Linux, embora possa ser mais desafiador para usuários comuns, se destaca na aplicação em servidores e projetos maiores, sendo geralmente mais leve e prático.

3-

entrar @alexxubyte pegar arquitetura real e discutir os trade-off da arquitetura (requisitos nao funcionais!), explicar por que é assim.
![netflix architecture](https://github.com/user-attachments/assets/31ede896-6722-400d-92ee-b6de7cd2761e)

Trade-off -- Complexidade x 

4- UML x Java relação

Código Album<br>

    import java.util.List;
    import java.util.LinkedList;

    public class Album {
        private List<Musica> musicas = new LinkedList<Musica>();
        public void adicionarMusica(Musica musica) {
            musicas.add(musica);
        }
        public List<Musica> buscarMusicaPorNome(String nome) {
            List<Musica> encontrados = new LinkedList<>();
            for (Musica musica : musicas) {
                if (nome.equals(musica.getNome())) {
                    encontrados.add(musica);
                }
            }
            return encontrados;
        }
    }

Codigo Musica<br>

    public class Musica {
        private String nome;
        private String duracao;
        public String getNome() {
            return nome;
        }
        public void setNome(String nome) {
            nome = nome;
        }
        public String getDuracao() {
            return duracao;
        }
        public void setDuracao(String duracao) {
            duracao = duracao;
        }
    }

![image](https://github.com/user-attachments/assets/2370a14e-7807-4aa4-aa47-0543eb5ded65)


