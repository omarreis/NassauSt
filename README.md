# NassauSt

Esse repositório contém arquivos e tutoriais de suporte ao app Nassau St.

## Sobre NassauSt
NassauSt é um app para acompanhamento do mercado financeiro e gestão de carteiras de ativos financeiros.
O App está disponivel para Android, iOS e Windows.

## Market data ( cotações ) 
As cotações do Google Finance, através do GoogleSheets, são usadas para calculo do valor atual dos ativos nas carteiras de Nassau.
Este serviço é grátis, porém na maioria dos ativos há um delay de 15 min.

A planilha abaixo contém a tabela de ativos "oficial":

    https://docs.google.com/spreadsheets/d/1rP386BJCjW2MDa9PzYYP5OPzgeO61lG-Vo_EM8GDHho/edit?usp=sharing
    

##  Uso de cotações do Nassau em planilhas Excel ( via DDE )
Nassau St (na versão para Windows, v2.1+ ) suporta atualização cotações via links DDE.

DDE é um protocolo de intercâmbio de dados entre aplicativos no Windows. Tradicionalmente é usado para alimentar planilhas Excel com cotações em tempo real. 

NassauSt permite acessar cotações dos mercados mundiais. São disponiveis ações brasileiras, ETFs, FIIs, BDRs, ADRs na B3, além de alguns ativos da NYSE e NASDAQ, indices mundiais, moedas e cryptos ( aprox 1500 ativos financeiros ).

**Exemplo de uso do DDE:**

1) No Windows abra simultaneamente os apps NassauSt e Excel.
2) Faça o download e abra a planilha de teste: 
      https://github.com/omarreis/NassauSt/blob/main/documentacaoNassauSt_DDESvr.xlsx
3) Autorize a atualização dos items da planilha.

Como Nassau atualiza as cotações a cada 5 min, as cotações na planilha são atualizadas com a mesma frequencia.

A planilha Excel de exemplo ilustra como estabelecer os link para atualização automática.

## Servidor DDE Nassau
Nassau permite dois tipos de links DDE ( tópicos ): valores individuais e range de valores.

1) Valores individuais do papel (tópico **VAL** )
 
   fórmula:   **=nassau|val!ativo.tipo**
   exemplos:  **=nassau|val!goog**    ou   **=nassau|val!IBOV.max**
   (formula case insensitive - no caso de omitir o tipo, o ultimo preço é retornado)			
   
   tipos em portugues: cod,preco,max,min,abe,vol,var,marketcap,hora,pl,lpa,min52,max52,fech,numero,nome,tipo,moeda,bolsa
   tipos em ingles: cod,price,high,low,priceopen,volume,changepct,marketcap,tradetime,pe,eps,low52,high52,closeyest,shares,name,type,curr,bolsa
   (as duas linguas podem ser usadas)
  
2) Range de valores do ativo (tópico **ALL** )				
 
   Retorna todos os campos do ativo em multiplas células horizontais (range )
   
   uso:  1) Selecione um range de celulas horizontal com até 19 colunas.
         2) digite fórmula:  **=nassau|all!ativo**
            exemplo: **=nassau|all!petr4**
         3) pressione **Ctrl-Shift Enter**

![image](https://user-images.githubusercontent.com/7995878/121692954-048ea480-ca9f-11eb-886c-27b7791116a9.png)

## Facebook
Novidades e dicas do app são publicadas esta página no FB: 

   https://www.facebook.com/Nassaust-101122458817195

## download do app NassauSt: 

* para Windows: https://www.tecepe.com.br/nassau/download   
* para iOS:     https://apps.apple.com/us/app/nassau-st/id1093819633
* para Android: https://play.google.com/store/apps/details?id=com.embarcadero.Nassau 

## Site web
* https://www.tecepe.com.br/nassau
