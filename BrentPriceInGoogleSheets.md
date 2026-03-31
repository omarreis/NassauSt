# How to get brent oil prices into your Google spreadsheet

This file is in suppor of **Nassau St** financial app

## About NassauSt: 
NassauSt é um app para acompanhamento do mercado financeiro e gestão de carteiras de ativos financeiros.
Multi-plataforma disponivel para **Android iOS e Windows**.

## Google sheet trigger
In this sample we use a time triggered Trigger code to download
data from website **oilpriceapi.com**

You have to Sign Up with this website and get a secret **API key**
There is a free service tier if you do less than 10000 queries per month.

You have to have Edit rights on the sheet.
Thiss trigger updates the value of three cells:

      celulaPreco = "B8";     // brent price
      celulaHora  = "I8";     // query time
      celulaTeste = "J8";     // error message

On the sheet select from menu: 

> Extensions > App script

type code (JavaScript) 

    // TriggerUpdateBrent() code for sheet trigger 
    function TriggerUpdateBrent() {   
      var planilha = SpreadsheetApp.getActiveSpreadsheet();
      var aba = planilha.getSheetByName("Sheet1");
      var celulaPreco = "B8";     
      var celulaHora  = "I8";
      var celulaTeste = "J8";
      var preco = 0; 
      var precoAnt = aba.getRange(celulaPreco).getValue();
      // oil price website 
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


    
