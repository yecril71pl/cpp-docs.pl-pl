---
title: Klasa CPropExchange | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPropExchange
- AFXCTL/CPropExchange
- AFXCTL/CPropExchange::ExchangeBlobProp
- AFXCTL/CPropExchange::ExchangeFontProp
- AFXCTL/CPropExchange::ExchangePersistentProp
- AFXCTL/CPropExchange::ExchangeProp
- AFXCTL/CPropExchange::ExchangeVersion
- AFXCTL/CPropExchange::GetVersion
- AFXCTL/CPropExchange::IsAsynchronous
- AFXCTL/CPropExchange::IsLoading
dev_langs:
- C++
helpviewer_keywords:
- CPropExchange [MFC], ExchangeBlobProp
- CPropExchange [MFC], ExchangeFontProp
- CPropExchange [MFC], ExchangePersistentProp
- CPropExchange [MFC], ExchangeProp
- CPropExchange [MFC], ExchangeVersion
- CPropExchange [MFC], GetVersion
- CPropExchange [MFC], IsAsynchronous
- CPropExchange [MFC], IsLoading
ms.assetid: ed872180-e770-4942-892a-92139d501fab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8b63de74a044a55362c2ebafc814fcf0136434d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216845"
---
# <a name="cpropexchange-class"></a>Klasa CPropExchange
Obsługuje trwałość wdrożenia formantów OLE.  
  
## <a name="syntax"></a>Składnia  
  
```  
class AFX_NOVTABLE CPropExchange  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|Zamienia właściwość duży obiekt binarny (BLOB).|  
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|Zamienia właściwość czcionki.|  
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|Zamienia właściwość między formantem plikiem.|  
|[CPropExchange::ExchangeProp](#exchangeprop)|Właściwości wymiany dowolnego typu wbudowanego.|  
|[CPropExchange::ExchangeVersion](#exchangeversion)|Zamienia numer wersji kontrolkę OLE.|  
|[CPropExchange::GetVersion](#getversion)|Pobiera numer wersji kontrolkę OLE.|  
|[CPropExchange::IsAsynchronous](#isasynchronous)|Określa, jeśli właściwość wymiany są wykonywane asynchronicznie.|  
|[CPropExchange::IsLoading](#isloading)|Wskazuje, czy właściwości są ładowane do formantu lub zapisany z niego.|  
  
## <a name="remarks"></a>Uwagi  
 `CPropExchange` nie ma klasy bazowej.  
  
 Ustanawia kontekst i kierunek exchange właściwości.  
  
 Utrwalanie jest wymiany informacji o stanie formantu, zwykle reprezentowany przez jej właściwości między nim a średniej lub.  
  
 Struktura konstruuje obiekt pochodną `CPropExchange` kiedy zostanie powiadomiony, że mają zostać załadowane z właściwości kontrolki OLE lub przechowywanych do trwałego magazynu.  
  
 Struktura przekazuje wskaźnik do tego `CPropExchange` obiektu do kontroli nad `DoPropExchange` funkcji. Jeśli Kreator jest używany do tworzenia plików początkowy dla formantu, formant `DoPropExchange` wywołaniach funkcji `COleControl::DoPropExchange`. Wersja klasy bazowej wymienia podstawowe właściwości formantu; Możesz zmodyfikować klasy pochodnej w wersji do programu exchange właściwości zostały dodane do formantu.  
  
 `CPropExchange` można serializować właściwości kontrolki lub zainicjować właściwości formantu w momencie ładowania lub tworzenia kontrolki. `ExchangeProp` i `ExchangeFontProp` funkcje elementów członkowskich `CPropExchange` są w stanie właściwości, aby zapisać i załadować je od innych nośników.  
  
 Aby uzyskać więcej informacji na temat korzystania z `CPropExchange`, zapoznaj się z artykułem [kontrolki ActiveX MFC: strony właściwości](../../mfc/mfc-activex-controls-property-pages.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CPropExchange`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxctl.h  
  
##  <a name="exchangeblobprop"></a>  CPropExchange::ExchangeBlobProp  
 Serializuje właściwość, która przechowuje dane dużych obiektów binarnych (BLOB).  
  
```  
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,  
    HGLOBAL* phBlob,  
    HGLOBAL hBlobDefault = NULL) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *phBlob*  
 Wskaźnik do zmiennej wskazuje do przechowywania właściwości (zmienna zwykle jest elementem członkowskim klasy).  
  
 *hBlobDefault*  
 Wartość domyślna dla właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytywany lub zapisywany do, odpowiednio, zmienna odwołuje się *phBlob*. Jeśli *hBlobDefault* jest określony, będzie służyć jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, serializacji formantu nie powiedzie się.  
  
 Funkcje `CArchivePropExchange::ExchangeBlobProp`, `CResetPropExchange::ExchangeBlobProp`, i `CPropsetPropExchange::ExchangeBlobProp` zastąpienie tego czystą funkcję wirtualną.  
  
##  <a name="exchangefontprop"></a>  CPropExchange::ExchangeFontProp  
 Zamienia właściwość czcionki, między nośnika magazynowania i kontroli.  
  
```  
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,  
    CFontHolder& font,  
    const FONTDESC* pFontDesc,  
    LPFONTDISP pFontDispAmbient) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *Czcionka*  
 Odwołanie do [CFontHolder](../../mfc/reference/cfontholder-class.md) obiekt, który zawiera właściwość czcionki.  
  
 *pFontDesc*  
 Wskaźnik do [FONTDESC](/windows/desktop/api/olectl/ns-olectl-tagfontdesc) struktury zawierającej wartości inicjowanie domyślnego stanu właściwość czcionki podczas *pFontDispAmbient* ma wartość NULL.  
  
 *pFontDispAmbient*  
 Wskaźnik do `IFontDisp` interfejsu czcionki do użycia dla inicjowanie domyślnego stanu właściwość czcionki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli właściwość czcionki jest ładowany z nośnika do formantu, cech czcionki są pobierane z nośnika i `CFontHolder` zawiera odwołanie do obiektu *czcionki* jest inicjowany z nich. Jeśli jest on przechowywany właściwość czcionki, właściwości w obiekcie czcionki są zapisywane do nośnika.  
  
 Funkcje `CArchivePropExchange::ExchangeFontProp`, `CResetPropExchange::ExchangeFontProp`, i `CPropsetPropExchange::ExchangeFontProp` zastąpienie tego czystą funkcję wirtualną.  
  
##  <a name="exchangepersistentprop"></a>  CPropExchange::ExchangePersistentProp  
 Zamienia właściwość między formantem i pliku.  
  
```  
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,  
    LPUNKNOWN* ppUnk,  
    REFIID iid,  
    LPUNKNOWN pUnkDefault) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *ppUnk*  
 Wskaźnik do zmiennej wskaźnika z właściwością zawierającą `IUnknown` interfejsu (Ta zmienna jest zazwyczaj członkiem klasy).  
  
 *IID*  
 Identyfikator interfejsu interfejsu na właściwość, która kontrolka będzie używać.  
  
 *pUnkDefault*  
 Wartość domyślna dla właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli właściwość jest ładowany z pliku do kontrolki, właściwość jest utworzony i zainicjowany z pliku. Jeśli właściwość jest magazynowana, jego wartość jest zapisywana do pliku.  
  
 Funkcje `CArchivePropExchange::ExchangePersistentProp`, `CResetPropExchange::ExchangePersistentProp`, i `CPropsetPropExchange::ExchangePersistentProp` zastąpienie tego czystą funkcję wirtualną.  
  
##  <a name="exchangeprop"></a>  CPropExchange::ExchangeProp  
 Zamienia właściwość między nośnika magazynowania i kontroli.  
  
```  
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,  
    VARTYPE vtProp,  
    void* pvProp,  
    const void* pvDefault = NULL) = 0 ;  
```  
  
### <a name="parameters"></a>Parametry  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *vtProp*  
 Symbol, określając typ właściwości wymianie. Możliwe wartości to:  
  
|Symbol|Typ właściwości|  
|------------|-------------------|  
|VT_I2|**short**|  
|VT_I4|**long**|  
|VT_BOOL|**BOOL**|  
|VT_BSTR|`CString`|  
|VT_CY|**CY**|  
|VT_R4|**float**|  
|VT_R8|**double**|  
  
 *pvProp*  
 Wskaźnik do wartości właściwości.  
  
 *pvDefault*  
 Wskaźnik do wartości domyślnej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli właściwość jest ładowany z nośnika do formantu, wartość właściwości jest pobierana z nośnika i przechowywane w obiekt wskazywany przez *pvProp*. Jeśli właściwość jest przechowywana na nośniku, wartość obiektu wskazywanego przez *pvProp* jest zapisywany na nośniku.  
  
 Funkcje `CArchivePropExchange::ExchangeProp`, `CResetPropExchange::ExchangeProp`, i `CPropsetPropExchange::ExchangeProp` zastąpienie tego czystą funkcję wirtualną.  
  
##  <a name="exchangeversion"></a>  CPropExchange::ExchangeVersion  
 Metoda wywoływana przez platformę, by obsłużyć trwałości numeru wersji.  
  
```  
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,  
    DWORD dwVersionDefault,  
    BOOL bConvert);
```  
  
### <a name="parameters"></a>Parametry  
 *dwVersionLoaded*  
 Odwołanie do zmiennej, na którym będzie przechowywany numer wersji trwałe dane, które są ładowane.  
  
 *dwVersionDefault*  
 Bieżący numer wersji kontroli.  
  
 *bConvert*  
 Wskazuje, czy można przekonwertować danych trwałych do bieżącej wersji lub zachować te dane w tej samej wersji, który został załadowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0.  
  
##  <a name="getversion"></a>  CPropExchange::GetVersion  
 Wywołaj tę funkcję, aby pobrać numer wersji kontroli.  
  
```  
DWORD GetVersion();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Numer wersji kontroli.  
  
##  <a name="isasynchronous"></a>  CPropExchange::IsAsynchronous  
 Określa, jeśli właściwość wymiany są wykonywane asynchronicznie.  
  
```  
BOOL IsAsynchronous();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość TRUE, jeśli właściwości są wymieniane asynchronicznie, w przeciwnym razie wartość FALSE.  
  
##  <a name="isloading"></a>  CPropExchange::IsLoading  
 Wywołaj tę funkcję, aby ustalić, czy właściwości są ładowane do formantu lub zapisany z niego.  
  
```  
BOOL IsLoading();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli właściwości są ładowane; w przeciwnym razie 0.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [COleControl::DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)



