## Introdução
Como muitos sabem, nativamente o Pawn não possui programação modular, porém através de ALS podemos realizar as chamadas de "hooks" que são ganchos, tanto em Callbacks quanto em Funções.
## ALS (Advanced Library System)
Bom, até onde consegui pesquisar o ALS (Advanced Library System) basicamente determina que uma função já foi registrado/fisgado. Essa técnica até onde tenho conhecimento aproveita do pre-processamento do compilador através de suas diretivas que fazem que o processamento ocorra de forma especial gerando uma outra linha de processamento.
## Como funciona
O gancho é feito fazendo com que uma função chame outra função aparentemente com o mesmo nome, "encadeando" todas essas funções idênticas, de modo que chamar uma chama todas elas. Ao conectar funções, isso é fácil porque a cadeia chama a função anterior com o mesmo nome; no entanto, conectar retornos de chamada é complicado pelo fato de que a cadeia chama a próxima função com o mesmo nome - uma função que ainda não foi definida e pode nem existir.
## Macros
Um macro é uma sequência de instruções que é atribuída a um nome. Os macros são usados para automatizar tarefas repetitivas.
## Diretivas de pré-processamento
As diretivas são comandos especiais que são processados pelo compilador antes de compilar o código-fonte.

```cpp
#if // Testa o valor de uma constante (valor definido pela diretiva #define)

#else // Usada igual nas condicionais convencionais porém, para nesse caso, se o #if não seja satisfeito

#endif // Sinaliza o fim de uma condicional feita pelas diretivas

#defined // Indica se uma constante já foi definida (Constante definida pela diretiva '#define')

#undef // Serve para indefinir uma constante (Constante definida pela diretiva '#define')

#define // Define constantes durante a compilação
```

## Observações Úteis 
Existem algumas observações úteis que devem ser lembradas para qualquer problema futuro.
1. Ao declarar um ALS é extremamente necessário que ele esteja sendo chamado caso contrário ele pode, dar conflito e assim ele não carregará os outros módulo
2. Infelizmente o compilador não possui suporte para um limite de 31 caracteres em definições de variáveis e funções, caso aconteça esse aviso na hora de compilar utilize o seguinte código:
3. Vale ressaltar que quando definido um nome a um ALS esse nome é único a ele, ou seja, cada ALS deve conter um nome diferente.

```cpp
#pragma warning disable 230
```

## Wiki
Veja como utilizar ALS em diversas situações abaixo:
- [ALS com Callbacks](https://github.com/PawnTeam/ALS-HOOK-s/blob/main/ALS%20com%20Callbacks.md)
## Créditos/Referências
- https://sampforum.blast.hk/showthread.php?tid=574534
- https://portalsamp.com/showthread.php?tid=4226
