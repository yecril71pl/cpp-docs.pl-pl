---
title: Stan trwały formantów OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: 88707da503b1d1cdc809827dc4d1bac0ccad9b5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373011"
---
# <a name="persistence-of-ole-controls"></a>Stan trwały formantów OLE

Jedną z możliwości formantów OLE jest trwałość właściwości (lub serializacji), która umożliwia formantowi OLE odczytywanie lub zapisywanie wartości właściwości do i z pliku lub strumienia. Aplikacja kontenera można użyć serializacji do przechowywania wartości właściwości formantu, nawet po aplikacji zniszczył formantu. Wartości właściwości formantu OLE można następnie odczytać z pliku lub strumienia, gdy nowe wystąpienie formantu jest tworzony w późniejszym czasie.

### <a name="persistence-of-ole-controls"></a>Stan trwały formantów OLE

|||
|-|-|
|[PX_Blob](#px_blob)|Wymienia właściwość formantu, która przechowuje dane dużego obiektu binarnego (BLOB).|
|[PX_Bool](#px_bool)|Wymienia właściwość kontrolną typu **BOOL**.|
|[PX_Color](#px_color)|Wymienia właściwość koloru formantu.|
|[PX_Currency](#px_currency)|Wymienia właściwość kontrolną typu **CY**.|
|[PX_DataPath](#px_datapath)|Wymienia właściwość kontrolną typu `CDataPathProperty`.|
|[PX_Double](#px_double)|Wymienia właściwość kontrolną typu **double**.|
|[PX_Font](#px_font)|Wymienia właściwość czcionki formantu.|
|[PX_Float](#px_float)|Wymienia właściwość sterującą typu **float**.|
|[PX_IUnknown](#px_iunknown)|Wymienia właściwość formantu typu niezdefiniowanego.|
|[PX_Long](#px_long)|Wymienia właściwość kontrolną typu **long**.|
|[PX_Picture](#px_picture)|Wymienia właściwość obrazu formantu.|
|[PX_Short](#px_short)|Wymienia właściwość kontrolną typu **krótki**.|
|[PX_ULong](#px_ulong)|Wymienia właściwość kontrolną typu **ULONG**.|
|[PX_UShort](#px_ushort)|Wymienia właściwość kontrolną typu **USHORT**.|
|[PXstring (właśc.](#px_string)|Wymienia właściwość formantu ciągu znaków.|
|[PX_VBXFontConvert](#px_vbxfontconvert)|Wymienia właściwości związane z czcionką formantu VBX na właściwość czcionki sterującej OLE.|

Ponadto funkcja `AfxOleTypeMatchGuid` globalna jest dostarczana do testowania dopasowania między TYPEDESC i danego identyfikatora GUID.

## <a name="px_blob"></a><a name="px_blob"></a>PX_Blob

Wywołanie tej funkcji w `DoPropExchange` funkcji członkowskiej formantu do serializacji lub zainicjowania właściwości, która przechowuje dane dużego obiektu binarnego (BLOB).

```cpp
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>Parametry

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*hBlob (łuszczywość)*<br/>
Odwołanie do zmiennej, w której jest przechowywana właściwość (zazwyczaj zmienna elementu członkowskiego klasy).

*hBlobDefault (Niem.*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Wartość właściwości zostanie odczytana lub zapisana do zmiennej, do którego odwołuje się *hBlob*, odpowiednio. Ta zmienna powinna zostać zainicjowana `PX_Blob` do wartości NULL przed pierwszym wywołaniem (zazwyczaj można to zrobić w konstruktorze formantu). Jeśli *hBlobDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu proces inicjowania lub serializacji formantu zakończy się niepowodzeniem.

Uchwyty *hBlob* i *hBlobDefault* odnoszą się do bloku pamięci, który zawiera następujące elementy:

- A DWORD, który zawiera długość, w bajtach, danych binarnych, które następuje, a następnie natychmiast

- Blok pamięci zawierający rzeczywiste dane binarne.

Należy `PX_Blob` zauważyć, że przydzieli pamięć przy użyciu interfejsu API [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) systemu Windows podczas ładowania właściwości typu BLOB. Użytkownik jest odpowiedzialny za uwolnienie tej pamięci. W związku z tym destruktor formantu należy wywołać [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) na dozory właściwości typu BLOB, aby zwolnić dowolną pamięć przydzieloną do formantu.

## <a name="px_bool"></a><a name="px_bool"></a>PX_Bool

Wywołanie tej funkcji w `DoPropExchange` funkcji członkowskiej formantu, aby serializować lub inicjować właściwość typu BOOL.

```cpp
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

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*bWartość*<br/>
Odwołanie do zmiennej, w której jest przechowywana właściwość (zazwyczaj zmienna elementu członkowskiego klasy).

*bDefault (Domyślnie)*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Wartość właściwości zostanie odczytana lub zapisana do zmiennej, do którego odwołuje się *bValue*, odpowiednio. Jeśli *bDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu proces serializacji formantu zakończy się niepowodzeniem.

## <a name="px_color"></a><a name="px_color"></a>PX_Color

Wywołanie tej funkcji w `DoPropExchange` funkcji elementu członkowskiego formantu do serializacji lub zainicjowania właściwości typu OLE_COLOR.

```cpp
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

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*clrValue (clrValue)*<br/>
Odwołanie do zmiennej, w której jest przechowywana właściwość (zazwyczaj zmienna elementu członkowskiego klasy).

*clrDefault (niem.*<br/>
Wartość domyślna dla właściwości, zgodnie z definicją dewelopera formantu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Wartość właściwości zostanie odczytana lub zapisana do zmiennej, do którego odwołuje się *clrValue*, odpowiednio. Jeśli *clrDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu proces serializacji formantu zakończy się niepowodzeniem.

## <a name="px_currency"></a><a name="px_currency"></a>PX_Currency

Wywołanie tej funkcji w `DoPropExchange` funkcji członkowskiej formantu, aby serializować lub inicjować właściwość **waluty**typu .

```cpp
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

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*cyValue (cyValue)*<br/>
Odwołanie do zmiennej, w której jest przechowywana właściwość (zazwyczaj zmienna elementu członkowskiego klasy).

*cyDefault (cyDefault)*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Wartość właściwości zostanie odczytana lub zapisana do zmiennej, do którego odwołuje się *cyValue*, odpowiednio. Jeśli *cyDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu proces serializacji formantu zakończy się niepowodzeniem.

## <a name="px_datapath"></a><a name="px_datapath"></a>PX_DataPath

Wywołanie tej funkcji w `DoPropExchange` funkcji członkowskiej formantu w celu serializacji lub zainicjowania właściwości ścieżki danych typu [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md).

```cpp
BOOL PX_DataPath(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CDataPathProperty& dataPathProperty);

BOOL PX_DataPath(
    CPropExchange* pPX,
    CDataPathProperty& dataPathProperty);
```

### <a name="parameters"></a>Parametry

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*dataPathProperty*<br/>
Odwołanie do zmiennej, w której jest przechowywana właściwość (zazwyczaj zmienna elementu członkowskiego klasy).

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Właściwości ścieżki danych implementują właściwości formantu asynchronisty. Wartość właściwości zostanie odczytana lub zapisana do zmiennej, do którego odwołuje się *dataPathProperty*, odpowiednio.

## <a name="px_double"></a><a name="px_double"></a>PX_Double

Wywołanie tej funkcji w `DoPropExchange` funkcji członkowskiej formantu, aby serializować lub inicjować właściwość typu **double**.

```cpp
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

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*doubleValue (podwójna wartość)*<br/>
Odwołanie do zmiennej, w której jest przechowywana właściwość (zazwyczaj zmienna elementu członkowskiego klasy).

*doubleDefault (doubleDefault)*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana z lub zapisywana do zmiennej, do którego odwołuje się *doubleValue*, odpowiednio. Jeśli *doubleDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu proces serializacji formantu zakończy się niepowodzeniem.

## <a name="px_font"></a><a name="px_font"></a>PX_Font

Wywołanie tej funkcji w `DoPropExchange` funkcji elementu członkowskiego formantu do serializacji lub zainicjowania właściwości czcionki typu.

```cpp
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parametry

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*Czcionki*<br/>
Odwołanie do `CFontHolder` obiektu, który zawiera właściwość czcionki.

*pFontDesc ( pFontDesc )*<br/>
Wskaźnik do `FONTDESC` struktury zawierającej wartości do użycia podczas inicjowania domyślnego stanu właściwości czcionki, w przypadku gdy *pFontDispAmbient* ma wartość NULL.

*pFontDispAmbient*<br/>
Wskaźnik do `IFontDisp` interfejsu czcionki do użycia podczas inicjowania domyślnego stanu właściwości czcionki.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub `font`zapisywana `CFontHolder` do , odwołanie, w stosownych przypadkach. Jeśli *pFontDesc* i *pFontDispAmbient* są określone, są one używane do inicjowania wartości domyślnej właściwości, w razie potrzeby. Te wartości są używane, jeśli z jakiegokolwiek powodu proces serializacji formantu kończy się niepowodzeniem. Zazwyczaj należy przekazać NULL dla *pFontDesc* i `COleControl::AmbientFont` wartość otoczenia zwrócona przez *dla pFontDispAmbient*. Należy zauważyć, że `COleControl::AmbientFont` obiekt czcionki zwrócony `IFontDisp::Release` przez musi zostać zwolniony przez wywołanie funkcji elementu członkowskiego.

## <a name="px_float"></a><a name="px_float"></a>PX_Float

Wywołanie tej funkcji w `DoPropExchange` funkcji elementu członkowskiego formantu, aby serializować lub inicjować właściwość **typu float**.

```cpp
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

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*floatValue (wartość pływakowa)*<br/>
Odwołanie do zmiennej, w której jest przechowywana właściwość (zazwyczaj zmienna elementu członkowskiego klasy).

*floatDefault*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana z lub zapisywana do zmiennej, do którego odwołuje się *floatValue*, odpowiednio. Jeśli *floatDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu proces serializacji formantu zakończy się niepowodzeniem.

## <a name="px_iunknown"></a><a name="px_iunknown"></a>PX_IUnknown

Wywołanie tej funkcji w `DoPropExchange` funkcji elementu członkowskiego formantu do serializacji lub `IUnknown`zainicjowania właściwości reprezentowanej przez obiekt o interfejsie pochodnym.

```cpp
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>Parametry

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*Punk*<br/>
Odwołanie do zmiennej zawierającej interfejs obiektu, który reprezentuje wartość właściwości.

*Iid*<br/>
Identyfikator interfejsu wskazujący, który interfejs obiektu właściwości jest używany przez formant.

*pUnkDefault (Niedefault)*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub zapisywana do zmiennej, do którego odwołuje się *pUnk*, odpowiednio. Jeśli *pUnkDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu proces serializacji formantu zakończy się niepowodzeniem.

## <a name="px_long"></a><a name="px_long"></a>PX_Long

Wywołanie tej funkcji w `DoPropExchange` funkcji członkowskiej formantu, aby serializować lub inicjować właściwość typu **long**.

```cpp
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

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*Lvalue*<br/>
Odwołanie do zmiennej, w której jest przechowywana właściwość (zazwyczaj zmienna elementu członkowskiego klasy).

*lDefault (Niem.*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub zapisywana do zmiennej, do którego odwołuje się *lValue*, odpowiednio. Jeśli *lDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu proces serializacji formantu zakończy się niepowodzeniem.

## <a name="px_picture"></a><a name="px_picture"></a>PX_Picture

Wywołanie tej funkcji w `DoPropExchange` funkcji elementu członkowskiego formantu do serializacji lub zainicjowania właściwości obrazu formantu.

```cpp
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

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*Pict*<br/>
Odwołanie do [CPictureHolder](../../mfc/reference/cpictureholder-class.md) obiektu, w którym właściwość jest przechowywana (zazwyczaj zmienną elementu członkowskiego klasy).

*pictDefault (niem.*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub zapisywana do zmiennej, do którego odwołuje się *pict*, odpowiednio. Jeśli *pictDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu proces serializacji formantu zakończy się niepowodzeniem.

## <a name="px_short"></a><a name="px_short"></a>PX_Short

Wywołanie tej funkcji w `DoPropExchange` funkcji członkowskiej formantu, aby serializować lub inicjować właściwość typu **krótki**.

```cpp
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

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*sValue (wartość)*<br/>
Odwołanie do zmiennej, w której jest przechowywana właściwość (zazwyczaj zmienna elementu członkowskiego klasy).

*sDefault (Niem.*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana z lub zapisywana do zmiennej, do którego odwołuje się *sValue*, odpowiednio. Jeśli *sDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu proces serializacji formantu zakończy się niepowodzeniem.

## <a name="px_ulong"></a><a name="px_ulong"></a>PX_ULong

Wywołanie tej funkcji w `DoPropExchange` funkcji członkowskiej formantu, aby serializować lub inicjować właściwość typu **ULONG**.

```cpp
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

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*pszPropName*<br/>
Nazwa wymienianego obiektu.

*ulValue (wartość)*<br/>
Odwołanie do zmiennej, w której jest przechowywana właściwość (zazwyczaj zmienna elementu członkowskiego klasy).

*UlDefault (domyślne)*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana z lub zapisywana do zmiennej, do którego odwołuje się *wartość ulValue*, odpowiednio. Jeśli *ulDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu proces serializacji formantu zakończy się niepowodzeniem.

## <a name="px_ushort"></a><a name="px_ushort"></a>PX_UShort

Wywołanie tej funkcji w `DoPropExchange` funkcji członkowskiej formantu, aby serializować lub inicjować właściwość typu **niepodpisane krótkie**.

```cpp
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

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*pszPropName*<br/>
Nazwa wymienianego obiektu.

*usWartość*<br/>
Odwołanie do zmiennej, w której jest przechowywana właściwość (zazwyczaj zmienna elementu członkowskiego klasy).

*usDefault (Domyślnie)*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana z lub zapisywana do zmiennej, do którego odwołuje się *usValue*, odpowiednio. Jeśli *usDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu proces serializacji formantu zakończy się niepowodzeniem.

## <a name="pxstring"></a><a name="px_string"></a>PXstring (właśc.

Wywołanie tej funkcji w `DoPropExchange` funkcji elementu członkowskiego formantu do serializacji lub zainicjowania właściwości ciągu znaków.

```cpp
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

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*strValue (wartość)*<br/>
Odwołanie do zmiennej, w której jest przechowywana właściwość (zazwyczaj zmienna elementu członkowskiego klasy).

*strDefault (niem.*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana z lub zapisywana do zmiennej, do którego odwołuje się *strValue*, odpowiednio. Jeśli *strDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu proces serializacji formantu zakończy się niepowodzeniem.

## <a name="px_vbxfontconvert"></a><a name="px_vbxfontconvert"></a>PX_VBXFontConvert

Wywołanie tej funkcji w `DoPropExchange` funkcji elementu członkowskiego formantu, aby zainicjować właściwość czcionki, konwertując właściwości związane z czcionką formantu VBX.

```cpp
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>Parametry

*Ppx*<br/>
Wskaźnik do [obiektu CPropExchange](../../mfc/reference/cpropexchange-class.md) (zazwyczaj przekazywane `DoPropExchange`jako parametr do ).

*Czcionki*<br/>
Właściwość czcionki formantu OLE, która będzie zawierać przekonwertowane właściwości związane z czcionką VBX.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być używana tylko przez formant OLE, który jest zaprojektowany jako bezpośredni zamiennik formantu VBX. Gdy środowisko programistyczne języka Visual Basic konwertuje formularz zawierający formę VBX, aby `IDataObject::SetData` użyć odpowiedniego zastępczego formantu OLE, wywoła funkcję formantu, przekazując w zestawie właściwości, który zawiera dane właściwości formantu VBX. Ta operacja z kolei powoduje, `DoPropExchange` że funkcja formantu do wywołania. `DoPropExchange`można `PX_VBXFontConvert` wywołać, aby przekonwertować właściwości związane z czcionkami formantu VBX (na przykład "FontName", "FontSize" i tak dalej) na odpowiednie składniki właściwości czcionki formantu OLE.

`PX_VBXFontConvert`należy wywołać tylko wtedy, gdy formant jest faktycznie konwertowany z aplikacji formularza VBX. Przykład:

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
