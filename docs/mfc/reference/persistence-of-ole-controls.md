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
ms.openlocfilehash: f07efa6ebbea70f83803238bf73e2d3e806ea457
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204572"
---
# <a name="persistence-of-ole-controls"></a>Stan trwały formantów OLE
Jeden możliwości formantów OLE jest właściwość trwałość (lub serializacji), co pozwala kontrolkę OLE do odczytu lub zapisu wartości właściwości, do i z pliku lub strumienia. Aplikacja kontenera można użyć serializacji do przechowywania wartości właściwości kontrolki, nawet po zakończeniu aplikacja ma zniszczone formantu. Wartości właściwości kontrolki OLE może następnie zostać odczytany z pliku lub strumienia, gdy nowe wystąpienie kontrolki jest tworzona w późniejszym czasie.  
  
### <a name="persistence-of-ole-controls"></a>Stan trwały formantów OLE  
  
|||  
|-|-|  
|[Px_blob —](#px_blob)|Zamienia właściwości kontrolki, która przechowuje dane dużych obiektów binarnych (BLOB).|  
|[Px_bool —](#px_bool)|Wymienia właściwość formantu typu **BOOL**.|  
|[Px_color —](#px_color)|Zamienia właściwość color, kontrolki.|  
|[Px_currency —](#px_currency)|Wymienia właściwość formantu typu **CY**.|  
|[Px_datapath —](#px_datapath)|Wymienia właściwość formantu typu `CDataPathProperty`.|  
|[Px_double —](#px_double)|Wymienia właściwość formantu typu **double**.|  
|[Px_font —](#px_font)|Zamienia właściwość czcionki formantu.|  
|[Px_float —](#px_float)|Wymienia właściwość formantu typu **float**.|  
|[Px_iunknown —](#px_iunknown)|Zamienia niezdefiniowanego typu właściwości formantu.|  
|[Px_long —](#px_long)|Wymienia właściwość formantu typu **długie**.|  
|[Px_picture —](#px_picture)|Zamienia właściwość obrazu formantu.|  
|[Px_short —](#px_short)|Wymienia właściwość formantu typu **krótki**.|  
|[Px_ulong —](#px_ulong)|Wymienia właściwość formantu typu **ULONG**.|  
|[Px_ushort —](#px_ushort)|Wymienia właściwość formantu typu **USHORT**.|  
|[PXstring](#px_string)|Zamienia właściwość formantu w postaci ciągu znaków.|  
|[Px_vbxfontconvert —](#px_vbxfontconvert)|Zamienia właściwości powiązanych z czcionki kontrolkę VBX do właściwości czcionki kontrolki OLE.|  
  
 Ponadto `AfxOleTypeMatchGuid` funkcja globalna znajduje się do testowania TYPEDESC zgodne z podanym identyfikatorem GUID.  
  
##  <a name="px_blob"></a>  Px_blob —  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcja elementu członkowskiego do serializacji lub zainicjuj właściwość, która przechowuje dane dużych obiektów binarnych (BLOB).  
  
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
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *hBlob*  
 Odwołanie do zmiennej, w której są przechowywane właściwości (zazwyczaj zmienną składową klasy).  
  
 *hBlobDefault*  
 Wartość domyślna dla właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości będzie odczytać lub zapisywane w zmiennej, odwołuje się *hBlob*, odpowiednio. Ta zmienna powinna zostać zainicjowana na wartość NULL, przed wywołaniem początkowo `PX_Blob` po raz pierwszy (zazwyczaj można to zrobić w Konstruktorze formantu). Jeśli *hBlobDefault* jest określony, będzie służyć jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, proces inicjowania lub serializacji formantu nie powiedzie się.  
  
 Uchwyty *hBlob* i *hBlobDefault* odnoszą się do bloku pamięci, która zawiera następujące czynności:  
  
-   DWORD, zawierającą długości w bajtach, danych binarnych, poniżej, a następnie natychmiast przez  
  
-   Blok pamięci zawierającej dane binarne.  
  
 Należy pamiętać, że `PX_Blob` spowoduje przydzielenie pamięci, przy użyciu Windows [działanie funkcji GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) interfejsu API, podczas ładowania właściwości typu obiektu BLOB. Odpowiedzialność za zwalniania tej pamięci. W związku z tym, należy wywołać destruktor kontroli nad [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree) dowolne właściwości typu obiektu BLOB uchwytów, aby zwolnić Konfigurowanie przydzielania pamięci na Twoją kontrolą.  
  
##  <a name="px_bool"></a>  Px_bool —  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcja elementu członkowskiego do serializacji lub zainicjuj właściwość typu wartość logiczna.  
  
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
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *bDane wartości*  
 Odwołanie do zmiennej, w której są przechowywane właściwości (zazwyczaj zmienną składową klasy).  
  
 *bPoziom domyślny*  
 Wartość domyślna dla właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości będzie odczytać lub zapisywane w zmiennej, odwołuje się *bDane wartości*, odpowiednio. Jeśli *bPoziom domyślny* jest określony, będzie służyć jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, procesem serializacji formantu nie powiedzie się.  
  
##  <a name="px_color"></a>  Px_color —  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcja elementu członkowskiego do serializacji lub zainicjuj właściwość typu OLE_COLOR.  
  
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
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *clrValue*  
 Odwołanie do zmiennej, w której są przechowywane właściwości (zazwyczaj zmienną składową klasy).  
  
 *clrDefault*  
 Wartość domyślna właściwości, zdefiniowaną przez dewelopera kontrolek.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości będzie odczytać lub zapisywane w zmiennej, odwołuje się *clrValue*, odpowiednio. Jeśli *clrDefault* jest określony, będzie służyć jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, procesem serializacji formantu nie powiedzie się.  
  
##  <a name="px_currency"></a>  Px_currency —  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcja elementu członkowskiego do serializacji lub zainicjuj właściwość typu **waluty**.  
  
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
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *cyValue*  
 Odwołanie do zmiennej, w której są przechowywane właściwości (zazwyczaj zmienną składową klasy).  
  
 *cyDefault*  
 Wartość domyślna dla właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości będzie odczytać lub zapisywane w zmiennej, odwołuje się *cyValue*, odpowiednio. Jeśli *cyDefault* jest określony, będzie służyć jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, procesem serializacji formantu nie powiedzie się.  
  
##  <a name="px_datapath"></a>  Px_datapath —  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcja elementu członkowskiego do serializacji lub zainicjować właściwości ścieżki danych typu [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md).  
  
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
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *dataPathProperty*  
 Odwołanie do zmiennej, w której są przechowywane właściwości (zazwyczaj zmienną składową klasy).  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Właściwości ścieżki danych implementuje właściwości kontrolki asynchronicznego. Wartość właściwości będzie odczytać lub zapisywane w zmiennej, odwołuje się *dataPathProperty*, odpowiednio.  
  
##  <a name="px_double"></a>  Px_double —  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcja elementu członkowskiego do serializacji lub zainicjuj właściwość typu **double**.  
  
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
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *doubleValue*  
 Odwołanie do zmiennej, w której są przechowywane właściwości (zazwyczaj zmienną składową klasy).  
  
 *doubleDefault*  
 Wartość domyślna dla właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytywany lub zapisywany do zmiennej, odwołuje się *doubleValue*, odpowiednio. Jeśli *doubleDefault* jest określony, będzie służyć jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, procesem serializacji formantu nie powiedzie się.  
  
##  <a name="px_font"></a>  Px_font —  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcja elementu członkowskiego do serializacji lub zainicjuj właściwość Typ czcionki.  
  
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
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *Czcionka*  
 Odwołanie do `CFontHolder` obiekt, który zawiera właściwość czcionki.  
  
 *pFontDesc*  
 Wskaźnik do `FONTDESC` struktura zawierająca wartości, które mają być używane w inicjowanie domyślnego stanu właściwość czcionki, w przypadku których *pFontDispAmbient* ma wartość NULL.  
  
 *pFontDispAmbient*  
 Wskaźnik do `IFontDisp` interfejsu czcionki do użycia w inicjowanie domyślnego stanu właściwość czcionki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytywany lub zapisywany do `font`, `CFontHolder` odwołanie, jeśli to możliwe. Jeśli *pFontDesc* i *pFontDispAmbient* są określone, są one używane do inicjowania właściwości wartość domyślna, gdy potrzebne. Te wartości są używane, jeśli z jakiegokolwiek powodu, procesem serializacji formantu nie powiedzie się. Zazwyczaj przekazać wartości NULL *pFontDesc* i otoczenia wartość zwrócona przez obiekt `COleControl::AmbientFont` dla *pFontDispAmbient*. Należy zauważyć, że obiekt czcionki zwracany przez `COleControl::AmbientFont` muszą zostać zwolnione przez wywołanie `IFontDisp::Release` funkcja elementu członkowskiego.  
  
##  <a name="px_float"></a>  Px_float —  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcja elementu członkowskiego do serializacji lub zainicjuj właściwość typu **float**.  
  
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
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *floatValue*  
 Odwołanie do zmiennej, w której są przechowywane właściwości (zazwyczaj zmienną składową klasy).  
  
 *floatDefault*  
 Wartość domyślna dla właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytywany lub zapisywany do zmiennej, odwołuje się *floatValue*, odpowiednio. Jeśli *floatDefault* jest określony, będzie służyć jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, procesem serializacji formantu nie powiedzie się.  
  
##  <a name="px_iunknown"></a>  Px_iunknown —  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcja elementu członkowskiego do serializacji lub zainicjować właściwość reprezentowana przez obiekt `IUnknown`-pochodnych interfejsu.  
  
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
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *pUnk*  
 Odwołanie do zmiennej zawierający interfejs obiekt reprezentujący wartość właściwości.  
  
 *IID*  
 Identyfikator interfejsu, wskazujący, który interfejs obiektu właściwość jest używana przez kontrolkę.  
  
 *pUnkDefault*  
 Wartość domyślna dla właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytywany lub zapisywany do zmiennej, odwołuje się *pUnk*, odpowiednio. Jeśli *pUnkDefault* jest określony, będzie służyć jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, procesem serializacji formantu nie powiedzie się.  
  
##  <a name="px_long"></a>  Px_long —  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcja elementu członkowskiego do serializacji lub zainicjuj właściwość typu **długie**.  
  
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
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *l-wartości*  
 Odwołanie do zmiennej, w której są przechowywane właściwości (zazwyczaj zmienną składową klasy).  
  
 *lDefault*  
 Wartość domyślna dla właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytywany lub zapisywany do zmiennej, odwołuje się *l-wartości*, odpowiednio. Jeśli *lDefault* jest określony, będzie służyć jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, procesem serializacji formantu nie powiedzie się.  
  
##  <a name="px_picture"></a>  Px_picture —  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcja elementu członkowskiego do serializacji lub zainicjować właściwość obraz kontrolki.  
  
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
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *PICT*  
 Odwołanie do [CPictureHolder](../../mfc/reference/cpictureholder-class.md) przechowywania właściwości obiektu (zazwyczaj zmienną składową klasy).  
  
 *pictDefault*  
 Wartość domyślna dla właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytywany lub zapisywany do zmiennej, odwołuje się *pict*, odpowiednio. Jeśli *pictDefault* jest określony, będzie służyć jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, procesem serializacji formantu nie powiedzie się.  
  
##  <a name="px_short"></a>  Px_short —  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcja elementu członkowskiego do serializacji lub zainicjuj właściwość typu **krótki**.  
  
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
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *sValue*  
 Odwołanie do zmiennej, w której są przechowywane właściwości (zazwyczaj zmienną składową klasy).  
  
 *sDefault*  
 Wartość domyślna dla właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytywany lub zapisywany do zmiennej, odwołuje się *sValue*, odpowiednio. Jeśli *sDefault* jest określony, będzie służyć jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, procesem serializacji formantu nie powiedzie się.  
  
##  <a name="px_ulong"></a>  Px_ulong —  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcja elementu członkowskiego do serializacji lub zainicjuj właściwość typu **ULONG**.  
  
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
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *ulValue*  
 Odwołanie do zmiennej, w której są przechowywane właściwości (zazwyczaj zmienną składową klasy).  
  
 *ulDefault*  
 Wartość domyślna dla właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytywany lub zapisywany do zmiennej, odwołuje się *ulValue*, odpowiednio. Jeśli *ulDefault* jest określony, będzie służyć jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, procesem serializacji formantu nie powiedzie się.  
  
##  <a name="px_ushort"></a>  Px_ushort —  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcja elementu członkowskiego do serializacji lub zainicjuj właściwość typu **typ unsigned short**.  
  
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
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *usValue*  
 Odwołanie do zmiennej, w której są przechowywane właściwości (zazwyczaj zmienną składową klasy).  
  
 *usDefault*  
 Wartość domyślna dla właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytywany lub zapisywany do zmiennej, odwołuje się *usValue*, odpowiednio. Jeśli *usDefault* jest określony, będzie służyć jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, procesem serializacji formantu nie powiedzie się.  
  
##  <a name="px_string"></a>  PXstring  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcja elementu członkowskiego do serializacji lub zainicjuj właściwość ciągu znaków.  
  
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
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *pszPropName*  
 Nazwa właściwości wymianie.  
  
 *strValue*  
 Odwołanie do zmiennej, w której są przechowywane właściwości (zazwyczaj zmienną składową klasy).  
  
 *strDefault*  
 Wartość domyślna dla właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest odczytywany lub zapisywany do zmiennej, odwołuje się *strValue*, odpowiednio. Jeśli *strDefault* jest określony, będzie służyć jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu, procesem serializacji formantu nie powiedzie się.  
  
##  <a name="px_vbxfontconvert"></a>  Px_vbxfontconvert —  
 Wywołaj tę funkcję, w ramach kontroli nad `DoPropExchange` funkcji elementu członkowskiego, aby zainicjować właściwość czcionki przez przekonwertowanie właściwości powiązanych z czcionki kontrolkę VBX.  
  
```  
 
BOOL  
PX_VBXFontConvert(
    CPropExchange* 
pPX  ,  
    CFontHolder& font);  
```  
  
### <a name="parameters"></a>Parametry  
 *pPX*  
 Wskaźnik do [CPropExchange](../../mfc/reference/cpropexchange-class.md) obiektu (zwykle jest przekazywany jako parametr do `DoPropExchange`).  
  
 *Czcionka*  
 Właściwość czcionki formantu OLE, który będzie zawierać przekonwertowanego właściwości powiązanych z czcionki VBX.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wymiany powiodła się. 0 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja powinna być używane tylko przez kontrolkę OLE, która została zaprojektowana jako bezpośrednio zastąpić kontrolki VBX. Gdy środowisko projektowe języka Visual Basic konwertuje formularza, w którym formant VBX, aby użyć odpowiedniego zastępczy formantu OLE, wywoła formantu `IDataObject::SetData` funkcję, przekazując ustawioną właściwość, która zawiera dane właściwości kontrolki VBX. Ta operacja powoduje z kolei formantu `DoPropExchange` funkcja do wywołania. `DoPropExchange` można wywołać `PX_VBXFontConvert` przekonwertować właściwości związane z czcionki formantu VBX (na przykład "FontName," "FontSize", i tak dalej) do odpowiadających składników właściwość czcionki kontrolkę OLE.  
  
 `PX_VBXFontConvert` tylko powinna być wywoływana, gdy kontrolka jest faktycznie przekształcany z poziomu aplikacji formularza VBX. Na przykład:  
  
 [!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]  
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
