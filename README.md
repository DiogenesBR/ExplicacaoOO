# Explicação Orientação de Objeto

```csharp
// Declaração da classe 'Gato'
public class Gato 
{
    // Propriedades (também chamadas de campos ou variáveis de instância)

    // Propriedade 'Nome'. Pode armazenar uma string representando o nome do gato
    public string Nome { get; set; }

    // Propriedade 'Idade'. Pode armazenar um inteiro representando a idade do gato
    public int Idade { get; set; }

    // Propriedade 'Cor'. Pode armazenar uma string representando a cor do gato
    public string Cor { get; set; }

    // Construtor
    // Este é um método especial que é chamado quando um novo objeto da classe 'Gato' é criado.
    // Ele geralmente é usado para inicializar as propriedades do objeto.
    public Gato(string nome, int idade, string cor) 
    {
        Nome = nome;
        Idade = idade;
        Cor = cor;
    }

    // Métodos (também chamados de funções ou ações)

    // Este método permite ao gato 'falar' 
    public void Miar() 
    {
        Console.WriteLine($"{Nome} diz: Miau!");
    }

    // Este método permite ao gato 'comer'. A quantidade de comida é passada como um parâmetro.
    public void Comer(int quantidadeDeComida) 
    {
        Console.WriteLine($"{Nome} comeu {quantidadeDeComida} gramas de comida.");
    }
}

class Program 
{
    static void Main(string[] args) 
    {
        // Criando um novo objeto da classe 'Gato'. O objeto é uma instância da classe.
        Gato meuGato = new Gato("Bolinha", 2, "preto");

        // Usando a propriedade 'Nome' do objeto 'meuGato'
        Console.WriteLine(meuGato.Nome); // Isso imprimirá "Bolinha"

        // Chamando o método 'Miar' do objeto 'meuGato'
        meuGato.Miar(); // Isso imprimirá "Bolinha diz: Miau!"

        // Chamando o método 'Comer' do objeto 'meuGato'
        meuGato.Comer(50); // Isso imprimirá "Bolinha comeu 50 gramas de comida."
    }
}
```

## Modificadores de acesso
```csharp
public class Gato 
{
    // Propriedades
    public string Nome { get; set; }
    public int Idade { get; set; }
    public string Cor { get; set; }

    // Propriedade 'Humor'.
    // Nós vamos torná-la privada, o que significa que só pode ser acessada dentro desta classe.
    // Isso faz sentido, porque só o próprio gato realmente sabe como está se sentindo!
    private string Humor { get; set; }

    // Construtor
    public Gato(string nome, int idade, string cor, string humor) 
    {
        Nome = nome;
        Idade = idade;
        Cor = cor;
        Humor = humor; // Agora inicializamos o humor do gato quando criamos um novo Gato
    }

    // Métodos
    public void Miar() 
    {
        // Agora o 'Miar' do gato pode variar de acordo com o seu humor!
        if (Humor == "feliz")
        {
            Console.WriteLine($"{Nome} diz: Miau! Estou feliz!");
        }
        else if (Humor == "irritado")
        {
            Console.WriteLine($"{Nome} diz: MIAU! Estou irritado!");
        }
        else
        {
            Console.WriteLine($"{Nome} diz: Miau!");
        }
    }

    public void Comer(int quantidadeDeComida) 
    {
        Console.WriteLine($"{Nome} comeu {quantidadeDeComida} gramas de comida.");
        // Comer geralmente melhora o humor do gato
        Humor = "feliz";
    }

    // Embora a propriedade 'Humor' seja privada, podemos criar um método público para permitir
    // que outras partes do código saibam se o gato está feliz
    public bool EstaFeliz() 
    {
        return Humor == "feliz";
    }
}

class Program 
{
    static void Main(string[] args) 
    {
        Gato meuGato = new Gato("Bolinha", 2, "preto", "irritado");
        Console.WriteLine(meuGato.Nome); 
        meuGato.Miar(); // Vai imprimir "Bolinha diz: MIAU! Estou irritado!"

        meuGato.Comer(50); // Isso vai mudar o humor do gato para "feliz"
        meuGato.Miar(); // Vai imprimir "Bolinha diz: Miau! Estou feliz!"

        Console.WriteLine(meuGato.EstaFeliz() ? "Bolinha está feliz!" : "Bolinha não está feliz.");
    }
}
```
