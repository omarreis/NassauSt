# NassauSt

Esse repositório contem arquivos e tutoriais de suporte ao app Nassau St.

## Sobre NassauSt
NassauSt é um app para acompanhamento do mercado financeiro e gestão de carteiras de ativos financeiros.
O App está disponivel para Android, iOS e Windows.
* NassauSt usa market data do Google Docs (ou GoogleFinance), a maioria com delay de 15 min.

##  Uso de cotações do Nassau em planilhas Excel ( DDE )
NassauSt (na versão para Windows, versao 2.1+ ) suporta atualização cotações via links DDE.

DDE é um protocolo de intercambio de dados enmtre aplicativos no Windows. Tradicionalmente é usado para alimentar planilhas Excel com cotações em tempo real.
NassauSt permite acessar cotações dos mercados mundiais, com ênfase Bovespa (As cotações são do Google Finance, a maioria om delay de 15 min).
São disponiveis ações, ETFs, FIIs, BDRs, ADRs na B3, além de alguns ativos da NYSE e NASDAQ ( aprox 1500 ativos financeiros ).

1) No Windows abra simultaneamente os apps NassauSt e Excel.
2) Faça o download e abra a planilha de teste: 
      https://github.com/omarreis/NassauSt/blob/main/documentacaoNassauSt_DDESvr.xlsx
3) Autorize a atualização dos items da planilha.

Como Nassau atualiza as cotações a cada 5 min, as cotações na planilha são atualizadas com a mesma frequencia.

A planilha Excel de exemplo ilustra como estabelecer os link para atualização automática.

## Servidor DDE Nassau
Nassau permite dois tipos de links DDE ( tópicos )

1) Valores individuais do papel ( **VAL** )  												
    
   sintaxe:   =nassau|val!ativo[.tipo]      
   exemplos:  =nassau|val!goog    ou   =nassau|val!IBOV.max   
   ( formula case insensitive - no caso de omitir o tipo, o ultimo preço é retornado ) 												
   
   tipos em portugues: cod,preco,max,min,abe,vol,var,marketcap,hora,pl,lpa,min52,max52,fech,numero,nome,tipo,moeda,bolsa									
   tipos em ingles: cod,price,high,low,priceopen,volume,changepct,marketcap,tradetime,pe,eps,low52,high52,closeyest,shares,name,type,curr,bolsa						      (as duas linguas podem ser usadas)												
   
2) Trem de valores do ativo ( ALL ) 												
    retorna todos os campos do ativo em lista separada por tabs												
    sintaxe:  1) Selecione um range de celulas horizontal com até 19 colunas												
              2) digite fórmula:  **=nassau|all!ativo**               
                 exemplo: **=nassau|all!petr4**
              4) pressione **Ctrl-Shift Enter**


## Facebook
Novidades e dicas do app são publicadas esta página no FB: 

   https://www.facebook.com/Nassaust-101122458817195

## download do app NassauSt: 

* para Windows: https://www.tecepe.com.br/nassau/download   
* para iOS:     https://apps.apple.com/us/app/nassau-st/id1093819633
* para Android: https://play.google.com/store/apps/details?id=com.embarcadero.Nassau 

## Site web
* https://www.tecepe.com.br/nassau

