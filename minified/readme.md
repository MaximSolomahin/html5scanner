# О проекте
Данная версия сканера, базируется на html5-qrcode. Исходники можно посмотреть по ссылке https://github.com/mebjas/html5-qrcode

Доработки для PMI: 
  1. Увеличение масштаба сканирования.
  2. Добавление инвертирования.
  3. Добавление увеличение масштаба инвертированной картинки.
Данное решение помогло при сканировании Datamatrix с пачек стиков и блоков

#Как использовать: 
1. Скачать html5-qrcode.min.js
2. Подключить минификатор в свой JS файл

   ![image](https://github.com/MaximSolomahin/html5scanner/assets/80065451/2ab06cdb-21cf-4ae2-9ca3-1a75719f931e)
   
3.  (Опционально) Выбрать формат кодов, которые необходимо будет сканировать.

Пример:

    /*
       enum Html5QrcodeSupportedFormats {
          QR_CODE = 0,
          AZTEC,
          CODABAR,
          CODE_39,
          CODE_93,
          CODE_128,
          DATA_MATRIX,
          MAXICODE,
          ITF,
          EAN_13,
          EAN_8,
          PDF_417,
          RSS_14,
          RSS_EXPANDED,
          UPC_A,
          UPC_E,
          UPC_EAN_EXTENSION,
        }
    */
    
    	const formatsToSupport = [
    		Html5QrcodeSupportedFormats.QR_CODE,
    		Html5QrcodeSupportedFormats.DATA_MATRIX,
    		Html5QrcodeSupportedFormats.CODE_128,
    		Html5QrcodeSupportedFormats.EAN_13,
    		Html5QrcodeSupportedFormats.CODE_39,
    		Html5QrcodeSupportedFormats.EAN_8,
    	];
     

4. Создать экземпляр класса. 
     Пример:

     let html5QrcodeScanner = new Html5QrcodeScanner(
    		"reader",
    		{
    			fps: 30,
    			qrbox: {width: 250, height: 250},
    			experimentalFeatures: {
    				useBarCodeDetectorIfSupported: true
    			},
    			rememberLastUsedCamera: true,
    			showTorchButtonIfSupported: true,
    			showZoomSliderIfSupported: true,
    			//formatsToSupport: formatsToSupport
    		},
    		/* verbose=  Turn on it when will you want to show time for read 100 pictures and watch camera examples*/ true);
    	html5QrcodeScanner.render(onScanSuccess, onScanFailure);

5. Определить 2 callback функции:
     Пример: 

   function onScanSuccess(decodedText, decodedResult) {
        // handle the scanned code as you like, for example:
        console.log(`Code matched = ${decodedText}`, decodedResult);
   }
    
   function onScanFailure(error) {
    		// handle scan failure, usually better to ignore and keep scanning.
    		// for example:
    		//console.warn(`Code scan error = ${error}`);
   }

 Реализацию можно посмотреть в файле: html5scanner/minified/testScanner.html

