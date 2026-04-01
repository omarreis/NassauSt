# How to get brent oil prices into your Google spreadsheet

This file is in support of **Nassau St** financial app

## About NassauSt: 
NassauSt é um app para acompanhamento do mercado financeiro e gestão de carteiras de ativos financeiros.
Multi-plataforma disponivel para **Android iOS e Windows**.

## Google sheet trigger
In this sample we use a time activated Trigger to download data from website **oilpriceapi.com**

## Sign up and get APIKey

You have to Sign Up with this website **oilpriceapi.com** and get a secret **API key**
There is a free service tier if you do less than 10000 queries per month.
In the case in this sample, we will be doing updates every 30 minutes.
So it is about 1440 updates per month. 

## Set the code
You have to have Edit rights on the spreadsheet.
This sample updates the value of three cells of a spreadsheet named **Sheet1**:

      celulaPreco = "B8";     // brent price cell
      celulaHora  = "I8";     // query time cell
      celulaTeste = "J8";     // error message cell

Change cell locations and spread sheet name as needed.
On the speadsheet, select from menu: 

> Extensions > App script

This will open the Google Javascript editor. 

type code (JavaScript):

    // TriggerUpdateBrent() code for time trigger (each 30 minutes)
    function TriggerUpdateBrent() {   
      var planilha = SpreadsheetApp.getActiveSpreadsheet();
      var aba = planilha.getSheetByName("Sheet1");
      var celulaPreco = "B8";     
      var celulaHora  = "I8";
      var celulaTeste = "J8";
      var preco = 0; 
      var precoAnt = aba.getRange(celulaPreco).getValue();
      // oil price api website 
      var apik = PropertiesService.getScriptProperties().getProperty('OILPRICES_AK');
      var url = 'https://api.oilpriceapi.com/v1/prices/latest';
      var options = {
        'method': 'GET',
        'headers': { 'Authorization': 'Token ' + apik }
      };
      try {
        var response = UrlFetchApp.fetch(url, options);
        var data = JSON.parse(response.getContentText());
        preco = data.data.price;
      } catch (error) {
        //nothing
        preco = 0;
      }
      if ( (preco != 0) && (preco != "#NA") && (preco != "#ERROR") ) {
        aba.getRange(celulaPreco).setValue(preco);      
        aba.getRange(celulaHora).setValue(new Date());
        aba.getRange(celulaTeste).setValue("ok");
      } else {
        // aba.getRange(celulaHora).setValue("preco zero");
        aba.getRange(celulaHora).setValue(new Date());
        aba.getRange(celulaTeste).setValue("erro");
      }
    }

This code downloads Brent prices from the website via https, parses the data and sets the spreadsheet cells.  
To make this work you have to set the APIKey available as a script property.
This hides the secret key from people seing the Javascript code and also from "Read-Only sheet users" (in case you share the sheet with others).
Script properties are not visible to read-only users.

In the script editor, select menu option  **Extensions > Apps Script**
Select **Project Settings > Script Properties**. 
Click **Edit script properties**.
Click **Add Script Property**:

name: OILPRICES_AK 
set APIKey value as received from Oil prices api website. Click Save.

Remember to confirm your account registration by responding confirmation email.

## Create Trigger
Select from script menu **Triggers**  
Click *Create Trigger* button

    Set Event type = Time-based
    Minute interval = 30 minutes
    select function *TriggerUpdateBrent*
    Click the *Save* button

Security detail: It is also possible to obtain the oil price from inside a Function 
called in a cell formula. 

In this mode however, for security reasons, the function can only affect the cell that called it.
Calling the code from a Trigger allows setting multiple cells ( price,time,status ) at once.

## Test the script

The script must be run at least once manually. This will register IT with service security.
Go to the editor, select **TriggerUpdateBrent** and click **Run**

The Execution log should show the script start and script finish. Or else there is some error.

Now go back to the Sheet1 spreadsheet. The brent prices should be on the cells.

**Nassau St** app shows the price with ticker **BRENT**

--xx--

Omar: 31/03/26 creation




    
