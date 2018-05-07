---
title: Stan trwały formantów OLE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e84e26bae83bd131b53d10e4561ddb60854a8a5e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="persistence-of-ole-controls"></a>Stan trwały formantów OLE
Jeden możliwości formantów OLE jest właściwość trwałości (lub serializacji), co pozwala kontrolkę OLE do odczytu lub zapisu wartości właściwości do i z pliku lub strumienia. Aplikacji kontenera można użyć serializacji do przechowywania wartości właściwości formantu, nawet po aplikacji został zniszczony formantu. Wartości właściwości formantu OLE następnie można odczytać z pliku lub strumienia, gdy nowe wystąpienie kontrolki jest tworzona w późniejszym czasie.  
  
### <a name="persistence-of-ole-controls"></a>Stan trwały formantów OLE  
  
|||  
|-|-|  
|[Px_blob —](#px_blob)|Zamienia właściwość formantu, która przechowuje dane dużego obiektu binarnego (BLOB).|  
|[Px_bool —](#px_bool)|Zamienia właściwość formantu typu **BOOL**.|  
|[Px_color —](#px_color)|Zamienia właściwość kolor formantu.|  
|[Px_currency —](#px_currency)|Zamienia właściwość formantu typu **CY**.|  
|[Px_datapath —](#px_datapath)|Zamienia właściwość formantu typu `CDataPathProperty`.|  
|[Px_double —](#px_double)|Zamienia właściwość formantu typu **podwójne**.|  
|[Px_font —](#px_font)|Zamienia właściwość czcionki formantu.|  
|[Px_float —](#px_float)|Zamienia właściwość formantu typu **float**.|  
|[Px_iunknown —](#px_iunknown)|Zamienia właściwości formantu niezdefiniowanego typu.|  
|[Px_long —](#px_long)|Zamienia właściwość formantu typu **długi**.|  
|[Px_picture —](#px_picture)|Zamienia właściwość obraz formantu.|  
|[Px_short —](#px_short)|Zamienia właściwość formantu typu **krótki**.|  
|[Px_ulong —](#px_ulong)|Zamienia właściwość formantu typu **ULONG**.|  
|[Px_ushort —](#px_ushort)|Zamienia właściwość formantu typu **USHORT**.|  
|[PXstring](#px_string)|Zamienia właściwości formantu ciąg znaków.|  
|[Px_vbxfontconvert —](#px_vbxfontconvert)|Zamienia właściwości powiązanych z czcionki formantu VBX do właściwość czcionki formantu OLE.|  
  
 Ponadto `AfxOleTypeMatchGuid` globalne funkcja służy do testowania dopasowanie między `TYPEDESC` i danym identyfikatorem GUID.  
  
##  <a name="px_blob"></a>  Px_blob —  
 Wywołanie tej funkcji w ramach formantu `DoPropExchange` funkcji członkowskiej do serializacji lub zainicjować właściwość, która przechowuje dane dużego obiektu binarnego (BLOB).  
  
```  
 
BOOL  
PX_Blob(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    HGLOBAL& 
hBlob  ,  
    HGLOBAL 
hBlobDefault  
= NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `hBlob`  
 Odwołanie do zmiennej, w którym przechowywana jest właściwość (zazwyczaj zmiennej członkowskiej klasy).  
  
 `hBlobDefault`  
 Wartość domyślna właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości będzie można z zapisu lub odczytu zmienna odwołuje się `hBlob`, gdzie to właściwe. Ta zmienna powinien być inicjowany do **NULL** przed wywołaniem początkowo `PX_Blob` po raz pierwszy (zazwyczaj można to zrobić w Konstruktorze formantu). Jeśli `hBlobDefault` jest określony, będzie on używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, proces inicjowania lub serializacji formantu nie powiedzie się.  
  
 Uchwyty `hBlob` i `hBlobDefault` odwoływać się do bloku pamięci, która zawiera następujące:  
  
-   A `DWORD` zawierającą w bajtach długość danych binarnych, poniżej, a następnie natychmiast przez  
  
-   Blok pamięci zawierający dane binarne.  
  
 Należy pamiętać, że `PX_Blob` spowoduje przydzielenie pamięci przy użyciu systemu Windows [działanie funkcji GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) interfejsu API, podczas ładowania właściwości typu obiektu BLOB. Jest odpowiedzialny za zwolnienie tej pamięci. W związku z tym powinny wywoływać destruktor formantu [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579) na żadnej właściwości typu obiektu BLOB dojścia do zwolnienia Konfigurowanie wszystkie pamięci przydzielona do formantu.  
  
##  <a name="px_bool"></a>  Px_bool —  
 Wywołanie tej funkcji w ramach formantu `DoPropExchange` funkcji członkowskiej do serializacji lub zainicjować właściwość typu **BOOL**.  
  
```  
 
BOOL  
PX_Bool(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    BOOL& bValue);

BOOL  
PX_Bool(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    BOOL& 
bValue  ,  
    BOOL bDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `bValue`  
 Odwołanie do zmiennej, w którym przechowywana jest właściwość (zazwyczaj zmiennej członkowskiej klasy).  
  
 `bDefault`  
 Wartość domyślna właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości będzie można z zapisu lub odczytu zmienna odwołuje się `bValue`, gdzie to właściwe. Jeśli `bDefault` jest określony, będzie on używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, niepowodzenia procesu serializacji formantu.  
  
##  <a name="px_color"></a>  Px_color —  
 Wywołanie tej funkcji w ramach formantu `DoPropExchange` funkcji członkowskiej do serializacji lub zainicjować właściwość typu **OLE_COLOR**.  
  
```  
 
BOOL PX_Color(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    OLE_COLOR& clrValue);

BOOL PX_Color(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    OLE_COLOR& 
clrValue  ,  
    OLE_COLOR 
clrDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `clrValue`  
 Odwołanie do zmiennej, w którym przechowywana jest właściwość (zazwyczaj zmiennej członkowskiej klasy).  
  
 `clrDefault`  
 Wartość domyślna właściwości, zdefiniowaną przez dewelopera kontrolek.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości będzie można z zapisu lub odczytu zmienna odwołuje się `clrValue`, gdzie to właściwe. Jeśli `clrDefault` jest określony, będzie on używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, niepowodzenia procesu serializacji formantu.  
  
##  <a name="px_currency"></a>  Px_currency —  
 Wywołanie tej funkcji w ramach formantu `DoPropExchange` funkcji członkowskiej do serializacji lub zainicjować właściwość typu **waluty**.  
  
```  
 
BOOL  
PX_Currency(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CY& cyValue);

BOOL  
PX_Currency(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CY& 
cyValue  ,  
    CY cyDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `cyValue`  
 Odwołanie do zmiennej, w którym przechowywana jest właściwość (zazwyczaj zmiennej członkowskiej klasy).  
  
 `cyDefault`  
 Wartość domyślna właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości będzie można z zapisu lub odczytu zmienna odwołuje się `cyValue`, gdzie to właściwe. Jeśli `cyDefault` jest określony, będzie on używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, niepowodzenia procesu serializacji formantu.  
  
##  <a name="px_datapath"></a>  Px_datapath —  
 Wywołanie tej funkcji w ramach formantu `DoPropExchange` funkcji członkowskiej do serializacji lub zainicjować właściwość ścieżki danych typu [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md).  
  
```  
 
BOOL  
PX_DataPath(
    CPropExchange* 
pPX,  
    LPCTSTR 
pszPropName,  
    CDataPathProperty& dataPathProperty);

BOOL  
PX_DataPath(
    CPropExchange* 
pPX,  
    CDataPathProperty& dataPathProperty);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `dataPathProperty`  
 Odwołanie do zmiennej, w którym przechowywana jest właściwość (zazwyczaj zmiennej członkowskiej klasy).  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Właściwości ścieżki danych implementuje właściwości asynchronicznej formantu. Wartość właściwości będzie można z zapisu lub odczytu zmienna odwołuje się `dataPathProperty`, gdzie to właściwe.  
  
##  <a name="px_double"></a>  Px_double —  
 Wywołanie tej funkcji w ramach formantu `DoPropExchange` funkcji członkowskiej do serializacji lub zainicjować właściwość typu **podwójne**.  
  
```  
 
BOOL  
PX_Double(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    double& doubleValue);

BOOL  
PX_Double(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    double& 
doubleValue  ,  
    double doubleDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `doubleValue`  
 Odwołanie do zmiennej, w którym przechowywana jest właściwość (zazwyczaj zmiennej członkowskiej klasy).  
  
 `doubleDefault`  
 Wartość domyślna właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytu lub zapisu odwołuje się zmiennej `doubleValue`, gdzie to właściwe. Jeśli `doubleDefault` jest określony, będzie on używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, niepowodzenia procesu serializacji formantu.  
  
##  <a name="px_font"></a>  Px_font —  
 Wywołanie tej funkcji w ramach formantu `DoPropExchange` funkcji członkowskiej do serializacji lub zainicjować właściwość czcionki typu.  
  
```  
 
BOOL  
PX_Font(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CFontHolder& 
font  ,  
    const 
FONTDESC  
FAR* 
pFontDesc  
= 
NULL,  
    LPFONTDISP 
pFontDispAmbient  
= NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `font`  
 Odwołanie do `CFontHolder` obiekt, który zawiera właściwość czcionki.  
  
 `pFontDesc`  
 Wskaźnik do **FONTDESC** struktura zawierająca wartości do użycia w inicjowanie domyślnego stanu właściwość czcionki, w przypadku których `pFontDispAmbient` jest **NULL**.  
  
 `pFontDispAmbient`  
 Wskaźnik do **IFontDisp** interfejsu czcionki do użycia w inicjowanie domyślnego stanu właściwość czcionki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytu lub zapisu do `font`, `CFontHolder` odwołać, jeśli to możliwe. Jeśli `pFontDesc` i `pFontDispAmbient` są określone, są one używane do inicjowania wartość domyślna właściwości, gdy jest wymagane. Te wartości są używane, jeśli z jakiegokolwiek powodu, niepowodzenia procesu serializacji formantu. Zazwyczaj należy przekazać **NULL** dla `pFontDesc` i otoczenia wartość zwrócona przez `COleControl::AmbientFont` dla `pFontDispAmbient`. Należy pamiętać, że obiekt czcionki zwracany przez `COleControl::AmbientFont` musi zostać zwolniona przez wywołanie do **IFontDisp::Release** funkcję elementu członkowskiego.  
  
##  <a name="px_float"></a>  Px_float —  
 Wywołanie tej funkcji w ramach formantu `DoPropExchange` funkcji członkowskiej do serializacji lub zainicjować właściwość typu **float**.  
  
```  
 
BOOL  
PX_Float(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    float& floatValue);

BOOL  
PX_Float(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    float& 
floatValue  ,  
    float floatDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `floatValue`  
 Odwołanie do zmiennej, w którym przechowywana jest właściwość (zazwyczaj zmiennej członkowskiej klasy).  
  
 `floatDefault`  
 Wartość domyślna właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytu lub zapisu odwołuje się zmiennej `floatValue`, gdzie to właściwe. Jeśli `floatDefault` jest określony, będzie on używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, niepowodzenia procesu serializacji formantu.  
  
##  <a name="px_iunknown"></a>  Px_iunknown —  
 Wywołanie tej funkcji w ramach formantu `DoPropExchange` funkcji członkowskiej do serializacji lub zainicjować reprezentowanego przez obiekt o właściwości **IUnknown**-interfejsu pochodnego.  
  
```  
 
BOOL  
PX_IUnknown(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    LPUNKNOWN& 
pUnk  ,  
    REFIID 
iid  ,  
    LPUNKNOWN 
pUnkDefault  
= NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 *pUnk*  
 Odwołanie do zmiennej z interfejsem obiekt reprezentujący wartość właściwości.  
  
 `iid`  
 Identyfikator interfejsu wskazujący, który interfejs obiektu właściwości jest używany przez formant.  
  
 `pUnkDefault`  
 Wartość domyślna właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytu lub zapisu odwołuje się zmiennej *pUnk*odpowiednio. Jeśli `pUnkDefault` jest określony, będzie on używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, niepowodzenia procesu serializacji formantu.  
  
##  <a name="px_long"></a>  Px_long —  
 Wywołanie tej funkcji w ramach formantu `DoPropExchange` funkcji członkowskiej do serializacji lub zainicjować właściwość typu **długi**.  
  
```  
 
BOOL  
PX_Long(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    long& lValue);

BOOL  
PX_Long(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    long& 
lValue  ,  
    long lDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `lValue`  
 Odwołanie do zmiennej, w którym przechowywana jest właściwość (zazwyczaj zmiennej członkowskiej klasy).  
  
 `lDefault`  
 Wartość domyślna właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytu lub zapisu odwołuje się zmiennej `lValue`, gdzie to właściwe. Jeśli `lDefault` jest określony, będzie on używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, niepowodzenia procesu serializacji formantu.  
  
##  <a name="px_picture"></a>  Px_picture —  
 Wywołanie tej funkcji w ramach formantu `DoPropExchange` funkcji członkowskiej do serializacji lub zainicjować właściwość obraz formantu.  
  
```  
 
BOOL  
PX_Picture(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CPictureHolder& pict);

BOOL  
PX_Picture(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CPictureHolder& 
pict  ,  
    CPictureHolder& pictDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `pict`  
 Odwołanie do [CPictureHolder](../../mfc/reference/cpictureholder-class.md) obiektu, w którym przechowywana jest właściwość (zazwyczaj zmiennej członkowskiej klasy).  
  
 `pictDefault`  
 Wartość domyślna właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytu lub zapisu odwołuje się zmiennej `pict`, gdzie to właściwe. Jeśli `pictDefault` jest określony, będzie on używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, niepowodzenia procesu serializacji formantu.  
  
##  <a name="px_short"></a>  Px_short —  
 Wywołanie tej funkcji w ramach formantu `DoPropExchange` funkcji członkowskiej do serializacji lub zainicjować właściwość typu **krótki**.  
  
```  
 
BOOL  
PX_Short(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    short& sValue);

BOOL  
PX_Short(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    short& 
sValue  ,  
    short sDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `sValue`  
 Odwołanie do zmiennej, w którym przechowywana jest właściwość (zazwyczaj zmiennej członkowskiej klasy).  
  
 `sDefault`  
 Wartość domyślna właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytu lub zapisu odwołuje się zmiennej `sValue`, gdzie to właściwe. Jeśli `sDefault` jest określony, będzie on używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, niepowodzenia procesu serializacji formantu.  
  
##  <a name="px_ulong"></a>  Px_ulong —  
 Wywołanie tej funkcji w ramach formantu `DoPropExchange` funkcji członkowskiej do serializacji lub zainicjować właściwość typu **ULONG**.  
  
```  
 
BOOL  
PX_ULong(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    ULONG& ulValue);

BOOL  
PX_ULong(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    ULONG& 
ulValue  ,  
    long ulDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `ulValue`  
 Odwołanie do zmiennej, w którym przechowywana jest właściwość (zazwyczaj zmiennej członkowskiej klasy).  
  
 `ulDefault`  
 Wartość domyślna właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytu lub zapisu odwołuje się zmiennej `ulValue`, gdzie to właściwe. Jeśli `ulDefault` jest określony, będzie on używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, niepowodzenia procesu serializacji formantu.  
  
##  <a name="px_ushort"></a>  Px_ushort —  
 Wywołanie tej funkcji w ramach formantu `DoPropExchange` funkcji członkowskiej do serializacji lub zainicjować właściwość typu `unsigned` **krótki**.  
  
```  
 
BOOL  
PX_UShort(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    USHORT& usValue);

BOOL  
PX_UShort(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    USHORT& 
usValue  ,  
    USHORT usDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 *usValue*  
 Odwołanie do zmiennej, w którym przechowywana jest właściwość (zazwyczaj zmiennej członkowskiej klasy).  
  
 *usDefault*  
 Wartość domyślna właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytu lub zapisu odwołuje się zmiennej *usValue*, gdzie to właściwe. Jeśli *usDefault* jest określony, będzie on używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, niepowodzenia procesu serializacji formantu.  
  
##  <a name="px_string"></a>  PXstring  
 Wywołanie tej funkcji w ramach formantu **DoPropExchange** funkcji członkowskiej do serializacji lub zainicjować właściwości ciągu znaków.  
  
```  
 
BOOL  
PXstring(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CString& strValue);

BOOL  
PXstring(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CString& 
strValue  ,  
    CString strDefault);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `pszPropName`  
 Nazwa właściwości są wymieniane.  
  
 `strValue`  
 Odwołanie do zmiennej, w którym przechowywana jest właściwość (zazwyczaj zmiennej członkowskiej klasy).  
  
 `strDefault`  
 Wartość domyślna właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytu lub zapisu odwołuje się zmiennej `strValue`, gdzie to właściwe. Jeśli `strDefault` jest określony, będzie on używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, niepowodzenia procesu serializacji formantu.  
  
##  <a name="px_vbxfontconvert"></a>  Px_vbxfontconvert —  
 Wywołanie tej funkcji w ramach formantu `DoPropExchange` funkcji członkowskiej zainicjować właściwość czcionki konwertując właściwości powiązanych z czcionki formantu VBX.  
  
```  
 
BOOL  
PX_VBXFontConvert(
    CPropExchange* 
pPX  ,  
    CFontHolder& font);  
```  
  
### <a name="parameters"></a>Parametry  
 `pPX`  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywana jako parametr `DoPropExchange`).  
  
 `font`  
 Właściwość czcionki formantu OLE, który będzie zawierać właściwości związanych z czcionki VBX przekonwertowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wymiany zakończyło się pomyślnie; 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja ta powinna być używana tylko przez formant OLE, który został zaprojektowany jako bezpośredniej wymiany kontrolki VBX. Gdy środowiska projektowania Visual Basic konwertuje formularz zawierający formantu VBX odpowiednie zastąpienia kontrolkę OLE, wywoła formantu **IDataObject::SetData** funkcji, przekazywanie we właściwości zestawu zawiera dane właściwości formantu VBX. Ta operacja powoduje z kolei formantu `DoPropExchange` funkcji do wywołania. `DoPropExchange` można wywołać `PX_VBXFontConvert` przekonwertować właściwości związanych z czcionki formantu VBX (na przykład "FontName," "FontSize," itd.) w odpowiadających składników właściwość czcionki formantu OLE.  
  
 `PX_VBXFontConvert` tylko powinna być wywoływana, gdy formant jest rzeczywiście przekształcany z aplikacji formularza VBX. Na przykład:  
  
 [!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]  
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
