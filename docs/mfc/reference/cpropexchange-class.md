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
ms.openlocfilehash: 7818b15e502bb32640d6b9dbfe1a6e4927c70650
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363971"
---
# <a name="cpropexchange-class"></a>Klasa CPropExchange

Obsługuje implementację trwałości dla formantów OLE.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CPropExchange
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|Wymienia binary large object (BLOB) właściwości.|
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|Wymienia właściwość czcionki.|
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|Wymienia właściwość między formantem a plikiem.|
|[CPropExchange::ExchangeProp](#exchangeprop)|Wymienia właściwości dowolnego typu wbudowanego.|
|[CPropExchange::ExchangeVersion](#exchangeversion)|Wymienia numer wersji formantu OLE.|
|[CPropExchange::GetVersion](#getversion)|Pobiera numer wersji formantu OLE.|
|[CPropExchange::IsAsynchronous](#isasynchronous)|Określa, czy wymiany właściwości są wykonywane asynchronicznie.|
|[CPropExchange::IsLoading](#isloading)|Wskazuje, czy właściwości są ładowane do formantu lub zapisane z niego.|

## <a name="remarks"></a>Uwagi

`CPropExchange`nie ma klasy podstawowej.

Ustanawia kontekst i kierunek wymiany właściwości.

Trwałość jest wymiana informacji o stanie formantu, zwykle reprezentowane przez jego właściwości, między formantem i medium.

Struktura tworzy obiekt pochodzący z `CPropExchange` gdy zostanie powiadomiony, że właściwości formantu OLE mają być ładowane z lub przechowywane do magazynu trwałego.

Struktura przekazuje wskaźnik do `CPropExchange` tego obiektu do `DoPropExchange` funkcji formantu. Jeśli do utworzenia plików startowych dla formantu `DoPropExchange` użyto `COleControl::DoPropExchange`kreatora, funkcja formantu wywołuje funkcję . Wersja klasy podstawowej wymienia właściwości zapasów formantu; zmodyfikujesz wersję klasy pochodnej, aby wymienić właściwości dodane do formantu.

`CPropExchange`może służyć do serializacji właściwości formantu lub zainicjować właściwości formantu na obciążenie lub tworzenie formantu. `ExchangeProp` Funkcje `ExchangeFontProp` i `CPropExchange` elementów członkowskich są w stanie przechowywać właściwości i ładować je z różnych nośników.

Aby uzyskać więcej `CPropExchange`informacji na temat używania , zobacz artykuł [MFC ActiveX Controls: Property Pages](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CPropExchange`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

## <a name="cpropexchangeexchangeblobprop"></a><a name="exchangeblobprop"></a>CPropExchange::ExchangeBlobProp

Serializuje właściwość, która przechowuje dane dużego obiektu binarnego (BLOB).

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>Parametry

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*phBlob (ł.*<br/>
Wskaźnik do zmiennej wskazującej, gdzie właściwość jest przechowywana (zmienna jest zazwyczaj członkiem klasy).

*hBlobDefault (Niem.*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest odczytywana lub zapisywana, odpowiednio, do zmiennej, do którego odwołuje się *phBlob.* Jeśli *hBlobDefault* jest określony, będzie używany jako wartość domyślna właściwości. Ta wartość jest używana, jeśli z jakiegokolwiek powodu serializacji formantu kończy się niepowodzeniem.

Funkcje `CArchivePropExchange::ExchangeBlobProp` `CResetPropExchange::ExchangeBlobProp`, `CPropsetPropExchange::ExchangeBlobProp` i zastąpić tę czystą funkcję wirtualną.

## <a name="cpropexchangeexchangefontprop"></a><a name="exchangefontprop"></a>CPropExchange::ExchangeFontProp

Wymienia właściwość czcionki między nośnikiem pamięci masowej a formantem.

```
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC* pFontDesc,
    LPFONTDISP pFontDispAmbient) = 0;
```

### <a name="parameters"></a>Parametry

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*Czcionki*<br/>
Odwołanie do [obiektu CFontHolder,](../../mfc/reference/cfontholder-class.md) który zawiera właściwość font.

*pFontDesc ( pFontDesc )*<br/>
Wskaźnik do struktury [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc) zawierający wartości inicjowania domyślnego stanu właściwości czcionki, gdy *pFontDispAmbient* ma wartość NULL.

*pFontDispAmbient*<br/>
Wskaźnik do `IFontDisp` interfejsu czcionki, która ma być używana do inicjowania domyślnego stanu właściwości czcionki.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Jeśli właściwość czcionki jest ładowany z nośnika do formantu, właściwości `CFontHolder` czcionki są pobierane z nośnika i obiekt, do którego odwołuje się *czcionka* jest inicjowany z nimi. Jeśli właściwość czcionki jest przechowywana, właściwości w obiekcie czcionki są zapisywane na nośniku.

Funkcje `CArchivePropExchange::ExchangeFontProp` `CResetPropExchange::ExchangeFontProp`, `CPropsetPropExchange::ExchangeFontProp` i zastąpić tę czystą funkcję wirtualną.

## <a name="cpropexchangeexchangepersistentprop"></a><a name="exchangepersistentprop"></a>CPropExchange::ExchangePersistentProp

Wymienia właściwość między formantem a plikiem.

```
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,
    LPUNKNOWN* ppUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault) = 0;
```

### <a name="parameters"></a>Parametry

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*ppUnk (polski)*<br/>
Wskaźnik do zmiennej zawierającej wskaźnik do `IUnknown` interfejsu właściwości (ta zmienna jest zazwyczaj członkiem klasy).

*Iid*<br/>
Identyfikator interfejsu na właściwości, która będzie używana przez formant.

*pUnkDefault (Niedefault)*<br/>
Wartość domyślna właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Jeśli właściwość jest ładowany z pliku do formantu, właściwość jest tworzona i inicjowana z pliku. Jeśli właściwość jest przechowywana, jej wartość jest zapisywana w pliku.

Funkcje `CArchivePropExchange::ExchangePersistentProp` `CResetPropExchange::ExchangePersistentProp`, `CPropsetPropExchange::ExchangePersistentProp` i zastąpić tę czystą funkcję wirtualną.

## <a name="cpropexchangeexchangeprop"></a><a name="exchangeprop"></a>CPropExchange::ExchangeProp

Wymienia właściwość między nośnikiem pamięci masowej a formantem.

```
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,
    VARTYPE vtProp,
    void* pvProp,
    const void* pvDefault = NULL) = 0 ;
```

### <a name="parameters"></a>Parametry

*pszPropName*<br/>
Nazwa wymienianej nieruchomości.

*vtProp (vtProp)*<br/>
Symbol określający typ wymienianej właściwości. Możliwe wartości:

|Symbol|Typ właściwości|
|------------|-------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_BOOL|**Bool**|
|Vt_bstr|`CString`|
|VT_CY|**CY**|
|VT_R4|**float**|
|VT_R8|**double**|

*pvProp*<br/>
Wskaźnik do wartości właściwości.

*pvDefault*<br/>
Wskaźnik do wartości domyślnej właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wymiana zakończyła się sukcesem; 0, jeśli się nie powiedzie.

### <a name="remarks"></a>Uwagi

Jeśli właściwość jest ładowany z medium do formantu, wartość właściwości jest pobierana z nośnika i przechowywane w obiekcie wskazanym przez *pvProp*. Jeśli właściwość jest przechowywana na nośniku, wartość obiektu wskazanego przez *pvProp* jest zapisywana na nośniku.

Funkcje `CArchivePropExchange::ExchangeProp` `CResetPropExchange::ExchangeProp`, `CPropsetPropExchange::ExchangeProp` i zastąpić tę czystą funkcję wirtualną.

## <a name="cpropexchangeexchangeversion"></a><a name="exchangeversion"></a>CPropExchange::ExchangeVersion

Wywoływana przez strukturę do obsługi trwałości numeru wersji.

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>Parametry

*dwVersionLoaded (Załadowano) dwVersion*<br/>
Odwołanie do zmiennej, w której zostanie przechowywany numer wersji ładowanych danych trwałych.

*dwVersionDefault (Niem.*<br/>
Bieżący numer wersji formantu.

*bKonwertowanie*<br/>
Wskazuje, czy mają być konwertowane dane trwałe do bieżącej wersji, czy zachować je w tej samej wersji, która została załadowana.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja powiodła się; 0 w przeciwnym razie.

## <a name="cpropexchangegetversion"></a><a name="getversion"></a>CPropExchange::GetVersion

Wywołanie tej funkcji, aby pobrać numer wersji formantu.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Wartość zwracana

Numer wersji formantu.

## <a name="cpropexchangeisasynchronous"></a><a name="isasynchronous"></a>CPropExchange::IsAsynchronous

Określa, czy wymiany właściwości są wykonywane asynchronicznie.

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli właściwości są wymieniane asynchronicznie, w przeciwnym razie FALSE.

## <a name="cpropexchangeisloading"></a><a name="isloading"></a>CPropExchange::IsLoading

Wywołanie tej funkcji, aby ustalić, czy właściwości są ładowane do formantu lub zapisane z niego.

```
BOOL IsLoading();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli właściwości są ładowane; w przeciwnym razie 0.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[COleControl::DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
