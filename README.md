# NassauSt

Esse repositório contém arquivos e tutoriais de suporte ao app **Nassau St**.

## Sobre NassauSt
NassauSt é um app para acompanhamento do mercado financeiro e gestão de carteiras de ativos financeiros.
Está disponivel para **Android iOS e Windows**.

## Market data ( cotações ) 
As cotações do **Google Finance**, através do GoogleSheets, são usadas em cálculos nas carteiras de Nassau St.
Este serviço do Google é grátis, porém na maioria dos ativos há um **delay de 15 min**. 
Se voce precisa de cotações em tempo real, consulte a enfoque ( www.enfoque.com.br )

A planilha abaixo contém a tabela de ativos "oficial" de Nassau St:

    https://docs.google.com/spreadsheets/d/1rP386BJCjW2MDa9PzYYP5OPzgeO61lG-Vo_EM8GDHho/edit?usp=sharing
  
* certifique-se de conhecer os Termos de serviço do Google: 

    https://policies.google.com/terms?hl=pt-BR
    
##  Uso de cotações do Nassau em planilhas Excel ( via DDE )
Nassau St (na versão para Windows, v2.1+ ) suporta atualização de cotações via links DDE ( tecnicamente o app é um servidor dde ).

DDE é um protocolo de intercâmbio de dados entre aplicativos no Windows. Tradicionalmente é usado para alimentar planilhas Excel com cotações em tempo real. 

NassauSt permite acessar cotações dos mercados mundiais. São disponiveis ações brasileiras, ETFs, FIIs, BDRs, ADRs na B3, além de alguns ativos da NYSE e NASDAQ, indices mundiais, moedas e cryptos ( aprox 1500 ativos financeiros ).

**Exemplo de uso do DDE:**

1) No Windows abra simultaneamente os apps NassauSt e Excel.
2) Faça o download e abra a planilha de teste: 
      https://github.com/omarreis/NassauSt/blob/main/documentacaoNassauSt_DDESvr.xlsx
3) Autorize a atualização dos items da planilha.

Como Nassau atualiza as cotações a cada 5 min, as cotações na planilha são atualizadas com a mesma frequencia.

A planilha Excel de exemplo ilustra como estabelecer o link para atualização automática da planilha.

## Links de cotações
Nassau permite dois tipos de links DDE ( tópicos DDE ): valores **individuais** e **range** de valores.

**1-** Valores individuais do papel (tópico **VAL**)
 
* fórmula:   **=nassau|val!ativo.tipo**
* exemplos:  **=nassau|val!goog**    ou   **=nassau|val!IBOV.max**

A formula é case insensitive. 
   
* tipos em portugues: cod preco max min abe vol var marketcap hora pl lpa min52 max52 fech numero nome tipo moeda bolsa.
* tipos em ingles: cod price high low priceopen volume changepct marketcap tradetime pe eps low52 high52 closeyest shares name type curr bolsa.
 
As duas linguas podem ser usadas.

No caso de omitir o tipo o ultimo preço é retornado. ex: **=nassau|val!petr4**
 
**2-** Range de valores do ativo (tópico **ALL** )
Retorna todos os campos do ativo em multiplas células horizontais (range )
   
uso:
* Selecione um range de celulas horizontal com até 19 colunas       
* Digite fórmula:  **=nassau|all!ativo**  (exemplo: **=nassau|all!petr4**)
* pressione **Ctrl-Shift Enter**

![image](https://user-images.githubusercontent.com/7995878/121692954-048ea480-ca9f-11eb-886c-27b7791116a9.png)

## Facebook
Novidades e dicas do app são publicadas nesta página no FB: 

   https://www.facebook.com/Nassaust-101122458817195

## download do app NassauSt: 

versão atual: 2.1.2 jun/21

* para Windows: https://www.tecepe.com.br/nassau/download   
* para iOS:     https://apps.apple.com/us/app/nassau-st/id1093819633
* para Android: https://play.google.com/store/apps/details?id=com.embarcadero.Nassau 

## Site web
* https://www.tecepe.com.br/nassau


