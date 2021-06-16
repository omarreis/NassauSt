# NassauSt

Esse repositório contém arquivos e tutoriais de suporte ao app **Nassau St**.

## Sobre NassauSt
NassauSt é um app para acompanhamento do mercado financeiro e gestão de carteiras de ativos financeiros.
Está disponivel para **Android iOS e Windows**.

## Homepage
* https://www.tecepe.com.br/nassau

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

## Posições em Carteira

Para cada conta é mantida uma lista de posições em carteira e inclui estátisticas de rentabilidade da posição:
* Codigo e especificação do papel
* Quantidade possuida
* Preço médio de aquiosição
* Valor de aquisição ( inclui despesas )
* Participação na carteira
* Cotação atual
* Valor atual
* Variação percentual
* Lucro/prejuízo da posição
* Prazo médio da posição
* Taxa de retorno anualizada 

![image](https://user-images.githubusercontent.com/7995878/121906058-212a1700-cd01-11eb-9f79-58170250a64b.png)

## Banco de dados em texto

Nassau ST utiliza banco de dados em formato texto. Isso permite interagir com outros programas ( ex planilhas ). 
O formato do banco de dados de operações é texto separado por ';'.
Cada linha contem um objeto que pode ser tipo conta, cabeçalho de nota, execução em bolsa ou lançamento (saque-deposito)

**Conta:** 
    formato: **c;Nome;Instituicao;NumDaConta;AporteInicial;NumDeCotas**
    
    c;Jose Carlos;AçõesDoZeca;001-1;300000;300000

**Nota:** 
    formato: **n;data;TotalCompras;TotalVendas;Despesas;IRRF**

    n;08/01/2020;272400;0;50;0

**Execuções:** 
  formato: **e;data/hora;C/V;Papel;Qde;Valor;PreçoMédio**
    
    e;08/01/2020 00:00;C;WEGE3;2000;76000;38
    
Uma nota completa fica:

    n;24/03/2020;0;61000;20;5
    e;24/03/2020 00:00;V;WEGE3;1000;36000;36
    e;24/03/2020 00:00;V;HGLG11;100;12000;120
    e;24/03/2020 00:00;V;PETR4;1000;13000;13
    
Nassau ST permite copiar ou colar uma lista de objetos, para permitir interação com outros sistemas (p.e. Excel) usando o clipboard do dispositivo. 

                Nassau St   <------------> Planilhas Excel, e-mail, 
               
Na formatação em texto, observar: 
  1) Usar '.' como separador decimal  
  2) Não usar separador de milhar (Numeros reais devem ter o formato '1234.56') 
  3) Data no formato 'dd/mm/aaaa'

Para inserir objetos no app, na página de portfolio:

1) Clique **Menu** 
2) Com as operações já no clipboard do dispositivo, aperte **Cola objetos**. Note que as operações são inseridas na conta selecionada no momento. Certifique-se de selecionar a conta correta antes de colar.

Para copiar dados do programa, se o banco de dados estiver em texto não encriptado, na página do portfolio, clique o botão DB, selecione o texto desejado e clique **Copy** ( **Ctrl-C** no Windows ).

## Facebook

Novidades e dicas do app são publicadas nesta página no FB: 

   https://www.facebook.com/Nassaust-101122458817195
   
## Github

Repositório com dicas, planilhas de teste e outros arquivos de suporte ao app.

   https://github.com/omarreis/NassauSt

## download ou update do app NassauSt: 

versão atual: 2.1.2 jun/21

* para Windows: https://www.tecepe.com.br/nassau/download   
* para iOS:     https://apps.apple.com/us/app/nassau-st/id1093819633
* para Android: https://play.google.com/store/apps/details?id=com.embarcadero.Nassau 



