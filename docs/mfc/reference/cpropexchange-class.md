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
ms.openlocfilehash: 5f234b3f06e22308a31e8e5694648fd5664b448a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cpropexchange-class"></a>Klasa CPropExchange
Obsługuje implementacji trwałości dla formantów OLE.  
  
## <a name="syntax"></a>Składnia  
  
```  
class AFX_NOVTABLE CPropExchange  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|Zamienia właściwość dużego obiektu binarnego (BLOB).|  
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|Zamienia właściwość czcionki.|  
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|Zamienia właściwość między formantem a plikiem.|  
|[CPropExchange::ExchangeProp](#exchangeprop)|Właściwości wymiany dowolnego typu wbudowanego.|  
|[CPropExchange::ExchangeVersion](#exchangeversion)|Zamienia numer wersji kontrolkę OLE.|  
|[CPropExchange::GetVersion](#getversion)|Pobiera numer wersji kontrolkę OLE.|  
|[CPropExchange::IsAsynchronous](#isasynchronous)|Określa, czy właściwość wymian są wykonywane asynchronicznie.|  
|[CPropExchange::IsLoading](#isloading)|Wskazuje, czy są właściwości do kontrolki zapisywany lub ładowany z niego.|  
  
## <a name="remarks"></a>Uwagi  
 `CPropExchange` nie ma klasy podstawowej.  
  
 Ustanawia kontekstu i kierunek exchange właściwości.  
  
 Trwałości jest wymiany informacji o stanie formantu, zazwyczaj reprezentowany przez jej właściwości między nim a średniej.  
  
 Platformę tworzy obiekt pochodzący od `CPropExchange` po zostaje powiadomiony, że mają zostać załadowane z właściwości formantów OLE lub przechowywane do trwałego magazynu.  
  
 Platformę przekazuje wskaźnik do to `CPropExchange` obiektu do formantu `DoPropExchange` funkcji. Jeśli Kreator jest używany do tworzenia plików starter formantu, formantu `DoPropExchange` wywołania funkcji `COleControl::DoPropExchange`. Wersja klasy podstawowej wymiany standardowych właściwości formantu; Możesz zmodyfikować klasy pochodnej w wersji exchange właściwości została dodana do formantu.  
  
 `CPropExchange` można serializować właściwości formantu lub zainicjować właściwości formantu w momencie ładowania lub tworzenia formantu. `ExchangeProp` i `ExchangeFontProp` funkcji Członkowskich `CPropExchange` mogą przechowywać właściwości, aby załadować je z innego nośnika.  
  
 Aby uzyskać więcej informacji na temat używania `CPropExchange`, zapoznaj się z artykułem [kontrolki ActiveX MFC: strony właściwości](../../mfc/mfc-activex-controls-property-pages.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CPropExchange`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxctl.h  
  
##  <a name="exchangeblobprop"></a>  CPropExchange::ExchangeBlobProp  
 Serializuje właściwość, która przechowuje dane dużego obiektu binarnego (BLOB).  
  
```  
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,  
    HGLOBAL* phBlob,  
    HGLOBAL hBlobDefault = NULL) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `phBlob`  
 Wskaźnik do zmiennej wskazuje do przechowywania właściwości (zmienna jest zwykle elementu członkowskiego klasy).  
  
 `hBlobDefault`  
 Wartość domyślna właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytu lub zapisu do, odpowiednio, zmienna odwołuje się `phBlob`. Jeśli `hBlobDefault` jest określony, będzie on używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, serializacji formantu nie powiedzie się.  
  
 Funkcje **CArchivePropExchange::ExchangeBlobProp**, **CResetPropExchange::ExchangeBlobProp**, i **CPropsetPropExchange::ExchangeBlobProp** zastąpienia czystej funkcji wirtualnej.  
  
##  <a name="exchangefontprop"></a>  CPropExchange::ExchangeFontProp  
 Zamienia właściwość czcionki między nośnika magazynowania i formantu.  
  
```  
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,  
    CFontHolder& font,  
    const FONTDESC* pFontDesc,  
    LPFONTDISP pFontDispAmbient) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `font`  
 Odwołanie do [CFontHolder](../../mfc/reference/cfontholder-class.md) obiekt, który zawiera właściwość czcionki.  
  
 `pFontDesc`  
 Wskaźnik do [FONTDESC](http://msdn.microsoft.com/library/windows/desktop/ms692782) struktury zawierającej wartości inicjowanie domyślnego stanu właściwość czcionki podczas `pFontDispAmbient` jest **NULL**.  
  
 `pFontDispAmbient`  
 Wskaźnik do **IFontDisp** interfejsu czcionki do użycia dla inicjowanie domyślnego stanu właściwość czcionki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli właściwość czcionki jest ładowany z nośnika do kontrolki, ustawienia czcionek są pobierane z nośnika i `CFontHolder` zawiera odwołanie do obiektu `font` jest inicjowany z nich. Jeśli właściwość czcionki są przechowywane, właściwości w obiekcie czcionki są zapisywane na nośniku.  
  
 Funkcje **CArchivePropExchange::ExchangeFontProp**, **CResetPropExchange::ExchangeFontProp**, i **CPropsetPropExchange::ExchangeFontProp** zastąpienia czystej funkcji wirtualnej.  
  
##  <a name="exchangepersistentprop"></a>  CPropExchange::ExchangePersistentProp  
 Zamienia właściwość między formantem a plikiem.  
  
```  
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,  
    LPUNKNOWN* ppUnk,  
    REFIID iid,  
    LPUNKNOWN pUnkDefault) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `ppUnk`  
 Wskaźnik do zmiennej zawierający wskaźnik z właściwością **IUnknown** interfejsu (Ta zmienna jest zwykle elementu członkowskiego klasy).  
  
 `iid`  
 Identyfikator interfejsu interfejsu we właściwości, który będzie używany przez formant.  
  
 `pUnkDefault`  
 Wartość domyślna właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli właściwość jest ładowany z pliku do formantu, właściwość jest tworzony i inicjowany z pliku. Jeśli właściwość jest magazynowana, jego wartość jest zapisywany do pliku.  
  
 Funkcje **CArchivePropExchange::ExchangePersistentProp**, **CResetPropExchange::ExchangePersistentProp**, i **CPropsetPropExchange::ExchangePersistentProp** zastąpienie tego czystej funkcji wirtualnej.  
  
##  <a name="exchangeprop"></a>  CPropExchange::ExchangeProp  
 Zamienia właściwość między nośnika magazynowania i formantu.  
  
```  
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,  
    VARTYPE vtProp,  
    void* pvProp,  
    const void* pvDefault = NULL) = 0 ;  
```  
  
### <a name="parameters"></a>Parametry  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `vtProp`  
 Symbol określenie typu właściwości są wymieniane. Możliwe wartości to:  
  
|Symbol|Typ właściwości|  
|------------|-------------------|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_BOOL`|**BOOL**|  
|`VT_BSTR`|`CString`|  
|`VT_CY`|**CY**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
  
 `pvProp`  
 Wskaźnik do wartości właściwości.  
  
 *pvDefault*  
 Wskaźnik do wartości domyślnej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli właściwość jest ładowany z nośnika do formantu, wartość właściwości jest pobierana z nośnika i przechowywane w wskazywanego przez obiekt `pvProp`. Jeśli właściwość są przechowywane na nośniku, wartość obiektu wskazywana przez `pvProp` jest zapisywany na nośniku.  
  
 Funkcje **CArchivePropExchange::ExchangeProp**, **CResetPropExchange::ExchangeProp**, i **CPropsetPropExchange::ExchangeProp** zastąpienie tym czysty funkcję wirtualną.  
  
##  <a name="exchangeversion"></a>  CPropExchange::ExchangeVersion  
 Wywoływane przez platformę, by obsłużyć trwałości numeru wersji.  
  
```  
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,  
    DWORD dwVersionDefault,  
    BOOL bConvert);
```  
  
### <a name="parameters"></a>Parametry  
 *dwVersionLoaded*  
 Odwołanie do zmiennej przechowywania numer wersji ładowanych danych trwałych.  
  
 `dwVersionDefault`  
 Bieżący numer wersji formantu.  
  
 `bConvert`  
 Wskazuje, czy do konwersji danych trwałych do bieżącej wersji lub zachowania jej w tej samej wersji, która została załadowana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończyło się pomyślnie; w przeciwnym razie 0.  
  
##  <a name="getversion"></a>  CPropExchange::GetVersion  
 Wywołanie tej funkcji można pobrać numeru wersji formantu.  
  
```  
DWORD GetVersion();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Numer wersji formantu.  
  
##  <a name="isasynchronous"></a>  CPropExchange::IsAsynchronous  
 Określa, czy właściwość wymian są wykonywane asynchronicznie.  
  
```  
BOOL IsAsynchronous();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość TRUE, jeśli właściwości są wymieniane asynchronicznie, w przeciwnym razie wartość FALSE.  
  
##  <a name="isloading"></a>  CPropExchange::IsLoading  
 Wywołanie tej funkcji w celu ustalenia, czy są właściwości do kontrolki zapisywany lub ładowany z niego.  
  
```  
BOOL IsLoading();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli właściwości są ładowane; w przeciwnym razie 0.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [COleControl::DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)



