Para começar utilizarmos o ALS com Callbacks é necessário alguns passos.

1. Crie uma pasta chamada: **"modules"** e dentro dessa pasta adicione um arquivo chamado: **"ALS.inc"** 
2. Após isso, dentro do arquivo principal que se encontra em: **"gamemodes/main.pwn".** Adicione o código abaixo para incluir o arquivo que possui o método de ALS, assim ele será executado quando compilado o arquivo principal.

```cpp
#include "../modules/ALS.inc" 
```
## Código 
Após seguir os passos acima, vamos ao código. Dentro do arquivo: **ALS.inc** adicione o código abaixo:

```cpp
public OnPlayerConnect(playerid) {
   print("ALS in Callbacks, teste");
   #if defined HOOK_OnPlayerConnect
       return HOOK_OnPlayerConnect(playerid); 
   #else 
       return 1;
   #endif
}

#if defined _ALS_OnPlayerConnect 
  #undef OnPlayerConnect 
#else
  #define _ALS_OnPlayerConnect 
#endif
#define OnPlayerConnect HOOK_OnPlayerConnect 
#if defined HOOK_OnPlayerConnect 
  forward HOOK_OnPlayerConnect(playerid); 
#endif 
```

Oque esse código realiza?
1. **Declaração da callback `OnPlayerConnect(playerid)`:** Define uma função que é executada quando um jogador se conecta.
   
2. **Impressão da mensagem de teste:** Utiliza a função `print()` para exibir a mensagem "ALS in Callbacks, teste" no console.

3. **Verificação condicional com `#if defined HOOK_OnPlayerConnect`:** Verifica se a constante `HOOK_OnPlayerConnect` está definida.

4. **Retorno da função `HOOK_OnPlayerConnect(players)`:** Se a constante `HOOK_OnPlayerConnect` estiver definida, retorna a chamada da função `HOOK_OnPlayerConnect` passando o parâmetro `playerid`.

5. **Retorno padrão:** Caso a constante `HOOK_OnPlayerConnect` não esteja definida, retorna o valor 1.

6. **Verificação condicional com `#if defined _ALS_OnPlayerConnect`:** Verifica se a constante `_ALS_OnPlayerConnect` está definida.

7. **Undefine da função `OnPlayerConnect`:** Caso a constante `_ALS_OnPlayerConnect` esteja definida, remove a definição da função `OnPlayerConnect`.

8. **Definição da constante `_ALS_OnPlayerConnect`:** Caso a constante `_ALS_OnPlayerConnect` não esteja definida, define-a.

8. **Definição da constante `OnPlayerConnect`:** Define a constante `OnPlayerConnect` como sendo igual à função `HOOK_OnPlayerConnect`.

10. **Verificação condicional com `#if defined HOOK_OnPlayerConnect`:** Verifica se a constante `HOOK_OnPlayerConnect` está definida.

11. **Declaração antecipada da função `HOOK_OnPlayerConnect(playerid)`:** Se a constante `HOOK_OnPlayerConnect` estiver definida, declara antecipadamente a função `HOOK_OnPlayerConnect` que recebe o parâmetro `playerid`.
## Estrutura de Pastas
(https://github.com/PawnTeam/ALS-HOOK-s/blob/main/structure.png)
