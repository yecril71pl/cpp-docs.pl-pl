---
title: Stan trwały formantów OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: 42e70f9e48339eddb2a5af4fa288400cce01f490
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502040"
---
# <a name="persistence-of-ole-controls"></a>Stan trwały formantów OLE

Jedną z możliwości formantów OLE jest trwałość właściwości (lub Serializacja), która umożliwia kontrolce OLE odczytywanie lub zapisywanie wartości właściwości do i z pliku lub strumienia. Aplikacja kontenera może użyć serializacji do przechowywania wartości właściwości kontrolki nawet wtedy, gdy aplikacja niszczy formant. Wartości właściwości kontrolki OLE można następnie odczytać z pliku lub strumienia, gdy zostanie utworzone nowe wystąpienie kontrolki w późniejszym czasie.

### <a name="persistence-of-ole-controls"></a>Stan trwały formantów OLE

|||
|-|-|
|[PX_Blob](#px_blob)|Wymienia właściwość kontrolki, która przechowuje dane binarne obiektów binarnych (BLOB).|
|[PX_Bool](#px_bool)|Wymienia właściwość kontrolki typu **bool**.|
|[PX_Color](#px_color)|Wymienia Właściwość Color formantu.|
|[PX_Currency](#px_currency)|Wymienia właściwość kontrolki typu **cy**.|
|[PX_DataPath](#px_datapath)|Wymienia właściwość kontrolki typu `CDataPathProperty`.|
|[PX_Double](#px_double)|Wymienia właściwość kontrolki typu **Double**.|
|[PX_Font](#px_font)|Wymienia Właściwość Font formantu.|
|[PX_Float](#px_float)|Wymienia właściwość kontrolki typu **float**.|
|[PX_IUnknown](#px_iunknown)|Wymienia właściwość kontrolki niezdefiniowanego typu.|
|[PX_Long](#px_long)|Wymienia właściwość kontrolki typu **Long**.|
|[PX_Picture](#px_picture)|Wymienia Właściwość Picture dla kontrolki.|
|[PX_Short](#px_short)|Wymienia właściwość kontrolki typu **Short**.|
|[PX_ULong](#px_ulong)|Wymienia właściwość kontrolki typu **ULONG**.|
|[PX_UShort](#px_ushort)|Wymienia właściwość kontrolki typu **UShort**.|
|[PXstring](#px_string)|Wymienia właściwość kontrolki ciągu znaków.|
|[PX_VBXFontConvert](#px_vbxfontconvert)|Wymienia właściwości dotyczące czcionek formantu VBX we właściwości czcionki kontrolki OLE.|

Ponadto `AfxOleTypeMatchGuid` funkcja globalna jest przetestowana pod kątem dopasowania między TYPEDESC i danym identyfikatorem GUID.

##  <a name="px_blob"></a>PX_Blob

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby serializować lub zainicjować właściwość, która przechowuje dane binarne obiektów binarnych (BLOB).

```
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*hBlob*<br/>
Odwołanie do zmiennej, w której jest przechowywana Właściwość (zazwyczaj zmienna członkowska klasy).

*hBlobDefault*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Wartość właściwości zostanie odczytana lub zapisywana w zmiennej, do której odwołuje się *hBlob*, zgodnie z potrzebami. Ta zmienna powinna zostać zainicjowana do wartości null `PX_Blob` przed pierwszym wywołaniem po raz pierwszy (zazwyczaj można to zrobić w konstruktorze kontrolki). Jeśli *hBlobDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegoś powodu proces inicjalizacji lub serializacji kontrolki nie powiedzie się.

Uchwyty *hBlob* i *hBlobDefault* odnoszą się do bloku pamięci, który zawiera następujące elementy:

- Wartość DWORD, która zawiera długość (w bajtach) danych binarnych, które po nim następuje

- Blok pamięci zawierający rzeczywiste dane binarne.

Należy pamiętać `PX_Blob` , że program przydzieli pamięć przy użyciu interfejsu API [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) systemu Windows podczas ładowania właściwości typu obiektu BLOB. Użytkownik jest odpowiedzialny za zwolnienie tej pamięci. W związku z tym destruktor formantu powinien wywołać [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) w dowolnych uchwytach właściwości typu obiektu BLOB, aby zwolnić pamięć przydzieloną do formantu.

##  <a name="px_bool"></a>PX_Bool

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby serializować lub zainicjować właściwość typu bool.

```
BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue);

BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue,
    BOOL bDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*bValue*<br/>
Odwołanie do zmiennej, w której jest przechowywana Właściwość (zazwyczaj zmienna członkowska klasy).

*bDefault*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Wartość właściwości zostanie odczytana lub zapisywana w zmiennej, do której odwołuje się *bValue*, zgodnie z potrzebami. Jeśli *bDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegoś powodu proces serializacji kontrolki nie powiedzie się.

##  <a name="px_color"></a>PX_Color

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby serializować lub zainicjować właściwość typu OLE_COLOR.

```
BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue);

BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue,
    OLE_COLOR clrDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*clrValue*<br/>
Odwołanie do zmiennej, w której jest przechowywana Właściwość (zazwyczaj zmienna członkowska klasy).

*clrDefault*<br/>
Wartość domyślna właściwości, zgodnie z definicją dewelopera kontrolki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Wartość właściwości zostanie odczytana lub zapisywana w zmiennej, do której odwołuje się *clrValue*, zgodnie z potrzebami. Jeśli *clrDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegoś powodu proces serializacji kontrolki nie powiedzie się.

##  <a name="px_currency"></a>PX_Currency

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby serializować lub zainicjować właściwość typu **Currency**.

```
BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue);

BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue,
    CY cyDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*cyValue*<br/>
Odwołanie do zmiennej, w której jest przechowywana Właściwość (zazwyczaj zmienna członkowska klasy).

*cyDefault*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Wartość właściwości zostanie odczytana lub zapisywana w zmiennej, do której odwołuje się *cyValue*, zgodnie z potrzebami. Jeśli *cyDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegoś powodu proces serializacji kontrolki nie powiedzie się.

##  <a name="px_datapath"></a>PX_DataPath

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby serializować lub zainicjować właściwość ścieżki danych typu [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md).

```
BOOL PX_DataPath(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CDataPathProperty& dataPathProperty);

BOOL PX_DataPath(
    CPropExchange* pPX,
    CDataPathProperty& dataPathProperty);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*dataPathProperty*<br/>
Odwołanie do zmiennej, w której jest przechowywana Właściwość (zazwyczaj zmienna członkowska klasy).

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Właściwości ścieżki danych implementują właściwości kontrolki asynchronicznej. Wartość właściwości zostanie odczytana lub zapisywana w zmiennej, do której odwołuje się *dataPathProperty*, zgodnie z potrzebami.

##  <a name="px_double"></a>PX_Double

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby serializować lub zainicjować właściwość typu **Double**.

```
BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue);

BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue,
    double doubleDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*doubleValue*<br/>
Odwołanie do zmiennej, w której jest przechowywana Właściwość (zazwyczaj zmienna członkowska klasy).

*doubleDefault*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub zapisywana w zmiennej, do której odwołuje się *doubleValue*, zgodnie z potrzebami. Jeśli *doubleDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegoś powodu proces serializacji kontrolki nie powiedzie się.

##  <a name="px_font"></a>PX_Font

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby serializować lub zainicjować właściwość czcionki typu Font.

```
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*Font*<br/>
Odwołanie do `CFontHolder` obiektu, który zawiera właściwość Font.

*pFontDesc*<br/>
Wskaźnik do `FONTDESC` struktury zawierającej wartości do użycia podczas inicjowania stanu domyślnego właściwości czcionki w przypadku, gdy *pFontDispAmbient* ma wartość null.

*pFontDispAmbient*<br/>
Wskaźnik do `IFontDisp` interfejsu czcionki, który ma być używany podczas inicjowania domyślnego stanu właściwości czcionki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub zapisywana `font` `CFontHolder` jako odwołanie, w razie potrzeby. Jeśli *pFontDesc* i *pFontDispAmbient* są określone, są one używane do inicjowania wartości domyślnej właściwości, w razie potrzeby. Te wartości są używane, jeśli z jakiegoś powodu nie powiedzie się proces serializacji formantu. Zwykle przekazanie wartości null dla *pFontDesc* oraz wartości otoczenia zwróconej przez `COleControl::AmbientFont` *pFontDispAmbient*. Należy zauważyć, że obiekt czcionki zwracany `COleControl::AmbientFont` przez musi być uwalniany przez wywołanie `IFontDisp::Release` funkcji składowej.

##  <a name="px_float"></a>PX_Float

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby serializować lub zainicjować właściwość typu **zmiennoprzecinkowego**.

```
BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue);

BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue,
    float floatDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*floatValue*<br/>
Odwołanie do zmiennej, w której jest przechowywana Właściwość (zazwyczaj zmienna członkowska klasy).

*floatDefault*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub zapisywana w zmiennej, do której odwołuje się *floatValue*, zgodnie z potrzebami. Jeśli *floatDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegoś powodu proces serializacji kontrolki nie powiedzie się.

##  <a name="px_iunknown"></a>PX_IUnknown

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby serializować lub zainicjować właściwość reprezentowaną przez obiekt `IUnknown`z interfejsem pochodnym.

```
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*pUnk*<br/>
Odwołanie do zmiennej zawierającej interfejs obiektu, który reprezentuje wartość właściwości.

*IID*<br/>
Identyfikator interfejsu wskazujący, który interfejs obiektu właściwości jest używany przez formant.

*pUnkDefault*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub zapisywana w zmiennej, do której odwołuje się *punkt*, zgodnie z potrzebami. Jeśli *pUnkDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegoś powodu proces serializacji kontrolki nie powiedzie się.

##  <a name="px_long"></a>PX_Long

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby serializować lub zainicjować właściwość typu **Long**.

```
BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue);

BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue,
    long lDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*lValue*<br/>
Odwołanie do zmiennej, w której jest przechowywana Właściwość (zazwyczaj zmienna członkowska klasy).

*lDefault*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub zapisywana w zmiennej, do której odwołuje się *lvalue*, zgodnie z potrzebami. Jeśli *lDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegoś powodu proces serializacji kontrolki nie powiedzie się.

##  <a name="px_picture"></a>PX_Picture

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby serializować lub zainicjować właściwość obrazu formantu.

```
BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict);

BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict,
    CPictureHolder& pictDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*Optymalizuj*<br/>
Odwołanie do obiektu [CPictureHolder](../../mfc/reference/cpictureholder-class.md) , w którym jest przechowywana Właściwość (zazwyczaj jest to zmienna członkowska klasy).

*pictDefault*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub zapisywana w zmiennej, do której odwołuje się *PICT*, zgodnie z potrzebami. Jeśli *pictDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegoś powodu proces serializacji kontrolki nie powiedzie się.

##  <a name="px_short"></a>PX_Short

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby serializować lub zainicjować właściwość typu **Short**.

```
BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue);

BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue,
    short sDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*sValue*<br/>
Odwołanie do zmiennej, w której jest przechowywana Właściwość (zazwyczaj zmienna członkowska klasy).

*sDefault*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub zapisywana w zmiennej, do której odwołuje się *sValue*, zgodnie z potrzebami. Jeśli *sDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegoś powodu proces serializacji kontrolki nie powiedzie się.

##  <a name="px_ulong"></a>PX_ULong

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby serializować lub zainicjować właściwość typu **ULONG**.

```
BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue);

BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue,
    long ulDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*ulValue*<br/>
Odwołanie do zmiennej, w której jest przechowywana Właściwość (zazwyczaj zmienna członkowska klasy).

*ulDefault*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub zapisywana w zmiennej, do której odwołuje się *ulValue*, zgodnie z potrzebami. Jeśli *ulDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegoś powodu proces serializacji kontrolki nie powiedzie się.

##  <a name="px_ushort"></a>PX_UShort

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby serializować lub zainicjować właściwość typu unsigned **Short**.

```
BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue);

BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue,
    USHORT usDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*usValue*<br/>
Odwołanie do zmiennej, w której jest przechowywana Właściwość (zazwyczaj zmienna członkowska klasy).

*usDefault*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub zapisywana w zmiennej, do której odwołuje się *usValue*, zgodnie z potrzebami. Jeśli *usDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegoś powodu proces serializacji kontrolki nie powiedzie się.

##  <a name="px_string"></a>PXstring

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby serializować lub zainicjować właściwość ciągu znaków.

```
BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue);

BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue,
    CString strDefault);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*strValue*<br/>
Odwołanie do zmiennej, w której jest przechowywana Właściwość (zazwyczaj zmienna członkowska klasy).

*strDefault*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub zapisywana w zmiennej, do której odwołuje się *strValue*, zgodnie z potrzebami. Jeśli *strDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegoś powodu proces serializacji kontrolki nie powiedzie się.

##  <a name="px_vbxfontconvert"></a>  PX_VBXFontConvert

Wywołaj tę funkcję w funkcji `DoPropExchange` składowej kontrolki, aby zainicjować właściwość Font poprzez konwersję właściwości związanych z czcionką kontrolki VBX.

```
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>Parametry

*pPX*<br/>
Wskaźnik do obiektu [CPropExchange](../../mfc/reference/cpropexchange-class.md) (zwykle przekazywać jako parametr do `DoPropExchange`).

*Font*<br/>
Właściwość Font formantu OLE, który będzie zawierać skonwertowane właściwości powiązane z czcionką VBX.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być używana tylko przez kontrolkę OLE, która została zaprojektowana jako bezpośrednie zastąpienie formantu VBX. Gdy Visual Basic środowisko programistyczne konwertuje formularz zawierający formant VBX, aby użyć odpowiedniej zastępczej kontrolki OLE, wywoła `IDataObject::SetData` funkcję kontrolki, przekazując do zestawu właściwości, który zawiera dane właściwości kontrolki VBX. Ta operacja z kolei powoduje, że `DoPropExchange` funkcja kontrolki ma być wywoływana. `DoPropExchange`może wywołać `PX_VBXFontConvert` , aby skonwertować właściwości powiązane z czcionką formantu VBX (na przykład "FontName," "FontSize" itd.) do odpowiednich składników właściwości font formantu OLE.

`PX_VBXFontConvert`należy wywołać tylko wtedy, gdy kontrolka jest faktycznie konwertowana z aplikacji formularza VBX. Na przykład:

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>Zobacz także

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
