---
title: Klasa CPropExchange
ms.date: 11/04/2016
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
ms.openlocfilehash: 09fb1bd34f3b5eadb78d8f9081450c042fe22f9e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226870"
---
# <a name="cpropexchange-class"></a>Klasa CPropExchange

Obsługuje implementację trwałości dla kontrolek OLE.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CPropExchange
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|Wymienia binarną Właściwość dużego obiektu (BLOB).|
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|Wymienia Właściwość Font.|
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|Wymienia Właściwość między kontrolką a plikiem.|
|[CPropExchange::ExchangeProp](#exchangeprop)|Wymienia właściwości dowolnego typu wbudowanego.|
|[CPropExchange::ExchangeVersion](#exchangeversion)|Wymienia numer wersji kontrolki OLE.|
|[CPropExchange:: GetVersion](#getversion)|Pobiera numer wersji kontrolki OLE.|
|[CPropExchange:: IsAsynchronous](#isasynchronous)|Określa, czy wymiana właściwości odbywa się asynchronicznie.|
|[CPropExchange:: IsLoading](#isloading)|Wskazuje, czy właściwości są ładowane do kontrolki, czy z niej zapisane.|

## <a name="remarks"></a>Uwagi

`CPropExchange`nie ma klasy bazowej.

Ustanawia kontekst i kierunek wymiany właściwości.

Trwałość polega na wymianie informacji o stanie kontrolki, zwykle reprezentowanych przez właściwości między samym formantem i średnią.

Struktura konstruuje obiekt pochodny `CPropExchange` , gdy zostanie powiadomiony o tym, że właściwości kontrolki OLE mają być ładowane z lub przechowywane do magazynu trwałego.

Struktura przekazuje wskaźnik do tego `CPropExchange` obiektu do funkcji kontrolki `DoPropExchange` . Jeśli użyto Kreatora do utworzenia plików początkowych dla formantu, funkcja kontrolki `DoPropExchange` wywołuje `COleControl::DoPropExchange` . Podstawowa wersja klasy wymienia właściwości giełdowe kontrolki; użytkownik modyfikuje wersję klasy pochodnej do właściwości Exchange, które zostały dodane do kontrolki.

`CPropExchange`może służyć do serializacji właściwości kontrolki lub inicjowania właściwości kontrolki podczas ładowania lub tworzenia kontrolki. `ExchangeProp`Funkcje i `ExchangeFontProp` składowe programu `CPropExchange` są w stanie przechowywać właściwości i ładować je z różnych nośników.

Aby uzyskać więcej informacji na temat korzystania z programu `CPropExchange` , zobacz [kontrolki ActiveX MFC: strony właściwości](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CPropExchange`

## <a name="requirements"></a>Wymagania

**Nagłówek:** 'afxctl. h

## <a name="cpropexchangeexchangeblobprop"></a><a name="exchangeblobprop"></a>CPropExchange::ExchangeBlobProp

Serializować właściwość, która przechowuje dane binarne obiektów binarnych (BLOB).

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>Parametry

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*phBlob*<br/>
Wskaźnik do zmiennej wskazującej lokalizację, w której jest przechowywana Właściwość (zmienna jest zazwyczaj składową klasy).

*hBlobDefault*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub zapisywana do, w zależności od potrzeb, zmiennej, do której odwołuje się *phBlob*. Jeśli *hBlobDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegoś powodu Serializacja formantu nie powiedzie się.

Funkcje `CArchivePropExchange::ExchangeBlobProp` `CResetPropExchange::ExchangeBlobProp` i `CPropsetPropExchange::ExchangeBlobProp` przesłonięcia tej czystej funkcji wirtualnej.

## <a name="cpropexchangeexchangefontprop"></a><a name="exchangefontprop"></a>CPropExchange::ExchangeFontProp

Wymienia Właściwość Font między nośnikiem magazynu i kontrolką.

```
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC* pFontDesc,
    LPFONTDISP pFontDispAmbient) = 0;
```

### <a name="parameters"></a>Parametry

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*Font*<br/>
Odwołanie do obiektu [CFontHolder](../../mfc/reference/cfontholder-class.md) , który zawiera właściwość Font.

*pFontDesc*<br/>
Wskaźnik do struktury [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc) zawierającej wartości do inicjowania stanu domyślnego właściwości font, gdy *pFontDispAmbient* ma wartość null.

*pFontDispAmbient*<br/>
Wskaźnik do `IFontDisp` interfejsu czcionki, który ma być używany do inicjowania stanu domyślnego właściwości czcionki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli właściwość Font jest ładowana z średniej do kontrolki, cechy czcionki są pobierane z nośnika, a `CFontHolder` obiekt, do którego odwołuje się *czcionka* , jest inicjowany z nimi. Jeśli właściwość Font jest przechowywana, cechy w obiekcie Font są zapisywane na nośniku.

Funkcje `CArchivePropExchange::ExchangeFontProp` `CResetPropExchange::ExchangeFontProp` i `CPropsetPropExchange::ExchangeFontProp` przesłonięcia tej czystej funkcji wirtualnej.

## <a name="cpropexchangeexchangepersistentprop"></a><a name="exchangepersistentprop"></a>CPropExchange::ExchangePersistentProp

Wymienia Właściwość między formantem a plikiem.

```
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,
    LPUNKNOWN* ppUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault) = 0;
```

### <a name="parameters"></a>Parametry

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*ppUnk*<br/>
Wskaźnik do zmiennej zawierającej wskaźnik do `IUnknown` interfejsu właściwości (Ta zmienna jest zazwyczaj składową klasy).

*IID*<br/>
Identyfikator interfejsu interfejsu we właściwości, która będzie używana przez formant.

*pUnkDefault*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli właściwość jest ładowana z pliku do kontrolki, właściwość zostanie utworzona i zainicjowana z pliku. Jeśli właściwość jest przechowywana, jej wartość jest zapisywana w pliku.

Funkcje `CArchivePropExchange::ExchangePersistentProp` `CResetPropExchange::ExchangePersistentProp` i `CPropsetPropExchange::ExchangePersistentProp` przesłonięcia tej czystej funkcji wirtualnej.

## <a name="cpropexchangeexchangeprop"></a><a name="exchangeprop"></a>CPropExchange::ExchangeProp

Wymienia Właściwość między nośnikiem magazynu a kontrolką.

```
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,
    VARTYPE vtProp,
    void* pvProp,
    const void* pvDefault = NULL) = 0 ;
```

### <a name="parameters"></a>Parametry

*pszPropName*<br/>
Nazwa wymienianej właściwości.

*vtProp*<br/>
Symbol określający typ wymienianej właściwości. Możliwe wartości:

|Symbol|Typ właściwości|
|------------|-------------------|
|VT_I2|**`short`**|
|VT_I4|**`long`**|
|VT_BOOL|**LOGICZNA**|
|VT_BSTR|`CString`|
|VT_CY|**CY**|
|VT_R4|**`float`**|
|VT_R8|**`double`**|

*pvProp*<br/>
Wskaźnik do wartości właściwości.

*pvDefault*<br/>
Wskaźnik na wartość domyślną właściwości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wymiana zakończyła się pomyślnie; 0, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli właściwość jest ładowana z średniej do kontrolki, wartość właściwości jest pobierana z nośnika i przechowywana w obiekcie wskazywanym przez *pvProp*. Jeśli właściwość jest przechowywana na nośniku, wartość obiektu wskazywanego przez *pvProp* jest zapisywana na nośniku.

Funkcje `CArchivePropExchange::ExchangeProp` `CResetPropExchange::ExchangeProp` i `CPropsetPropExchange::ExchangeProp` przesłonięcia tej czystej funkcji wirtualnej.

## <a name="cpropexchangeexchangeversion"></a><a name="exchangeversion"></a>CPropExchange::ExchangeVersion

Wywoływane przez platformę, aby obsłużyć trwałość numeru wersji.

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>Parametry

*dwVersionLoaded*<br/>
Odwołanie do zmiennej, w której zostanie zapisany numer wersji danych trwałych ładowanych.

*dwVersionDefault*<br/>
Numer bieżącej wersji formantu.

*bConvert*<br/>
Wskazuje, czy dane trwałe mają być konwertowane do bieżącej wersji, czy nie mają być przechowywane w tej samej wersji, która została załadowana.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; 0 w przeciwnym razie.

## <a name="cpropexchangegetversion"></a><a name="getversion"></a>CPropExchange:: GetVersion

Wywołaj tę funkcję, aby pobrać numer wersji formantu.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Wartość zwracana

Numer wersji formantu.

## <a name="cpropexchangeisasynchronous"></a><a name="isasynchronous"></a>CPropExchange:: IsAsynchronous

Określa, czy wymiana właściwości odbywa się asynchronicznie.

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli właściwości są wymieniane asynchronicznie, w przeciwnym razie FALSE.

## <a name="cpropexchangeisloading"></a><a name="isloading"></a>CPropExchange:: IsLoading

Wywołaj tę funkcję, aby określić, czy właściwości są ładowane do kontrolki, czy z niej zapisane.

```
BOOL IsLoading();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli są ładowane właściwości; w przeciwnym razie 0.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[COleControl::D oPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
