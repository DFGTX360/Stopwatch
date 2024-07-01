# Cronômetro Simples em C#

Este é um projeto de um cronômetro simples desenvolvido em C#. Ele permite que o usuário defina um tempo para contar em segundos ou minutos e exibe uma contagem regressiva até zero.

## Funcionalidades

- Contagem regressiva em segundos ou minutos
- Opção para sair do programa

## Como usar

1. Clone este repositório:
    ```bash
    git clone https://github.com/DFGTX360/Calculadora.c-.git
    ```
2. Abra o projeto em seu IDE de C# preferido (como Visual Studio ou Visual Studio Code).
3. Compile e execute o projeto.
4. Siga as instruções no console para definir o tempo desejado para a contagem regressiva.

## Estrutura do Código

O código está estruturado em métodos que permitem ao usuário escolher entre contar em segundos ou minutos e inicia a contagem regressiva a partir do tempo especificado.

### Método `Menu`

O método `Menu` exibe as opções disponíveis e lê a entrada do usuário. Ele permite que o usuário insira o tempo desejado no formato `Xs` para segundos ou `Xm` para minutos. Se o usuário digitar `0`, o programa é encerrado.

### Método `PreStart`

O método `PreStart` prepara o cronômetro para iniciar, exibindo uma sequência de mensagens "Ready", "Set" e "Go" antes de chamar o método `Start` para iniciar a contagem regressiva.

### Método `Start`

O método `Start` realiza a contagem regressiva a partir do tempo especificado em segundos ou minutos, atualizando o valor no console a cada segundo até que o tempo chegue a zero. Após a contagem, retorna ao menu principal.

## Exemplo de Uso

Ao executar o programa, o usuário verá as seguintes opções:


Após escolher uma opção válida (por exemplo, `5s` para contar 5 segundos), o programa iniciará a contagem regressiva até zero, exibindo cada segundo no console.

## Código

```csharp
using System;
using System.Threading;

internal class Program
{
    private static void Main(string[] args)
    {
        Menu();
    }

    static void Menu()
    {
        Console.Clear();
        Console.WriteLine("S = Segundos => 10s = 10 segundos");
        Console.WriteLine("M = Minutos => 1m = 1 minuto");
        Console.WriteLine("0 = Sair");
        Console.WriteLine("Quanto tempo deseja contar?");

        string data = Console.ReadLine().ToLower();
        char type = char.Parse(data.Substring(data.Length - 1, 1));
        int time = int.Parse(data.Substring(0, data.Length - 1));
        int multiplier = 1;

        if (type == 'm')
            multiplier = 60;

        if (time == 0)
            Environment.Exit(0);

        PreStart(time * multiplier);
    }

    static void PreStart(int time)
    {
        Console.Clear();
        Console.WriteLine("Ready..");
        Thread.Sleep(1000);
        Console.WriteLine("Set..");
        Thread.Sleep(1000);
        Console.WriteLine("Go...");
        Thread.Sleep(2500);

        Start(time);

    }

    static void Start(int time)
    {
        int currentTime = 0;
        while (currentTime != time)
        {
            Console.Clear();
            currentTime++;
            Console.WriteLine(currentTime);
            Thread.Sleep(1000);
        }
        Console.Clear();
        Console.WriteLine("Cronômetro finalizado");
        Thread.Sleep(2500);
        Menu();
    }
}


Certifique-se de salvar este conteúdo em um arquivo chamado `README.md` no diretório raiz do seu projeto antes de fazer o commit para o GitHub. Isso ajudará outros desenvolvedores a entenderem e utilizarem seu código de forma mais eficiente.



