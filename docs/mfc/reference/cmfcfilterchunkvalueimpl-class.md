---
title: Klasa CMFCFilterChunkValueImpl
ms.date: 11/04/2016
f1_keywords:
- CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::Clear
- AFXWIN/CMFCFilterChunkValueImpl::CopyChunk
- AFXWIN/CMFCFilterChunkValueImpl::CopyFrom
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkGUID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkPID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkType
- AFXWIN/CMFCFilterChunkValueImpl::GetString
- AFXWIN/CMFCFilterChunkValueImpl::GetValue
- AFXWIN/CMFCFilterChunkValueImpl::GetValueNoAlloc
- AFXWIN/CMFCFilterChunkValueImpl::IsValid
- AFXWIN/CMFCFilterChunkValueImpl::SetBoolValue
- AFXWIN/CMFCFilterChunkValueImpl::SetDwordValue
- AFXWIN/CMFCFilterChunkValueImpl::SetFileTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetInt64Value
- AFXWIN/CMFCFilterChunkValueImpl::SetIntValue
- AFXWIN/CMFCFilterChunkValueImpl::SetLongValue
- AFXWIN/CMFCFilterChunkValueImpl::SetSystemTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetTextValue
- AFXWIN/CMFCFilterChunkValueImpl::SetChunk
helpviewer_keywords:
- CMFCFilterChunkValueImpl [MFC], CMFCFilterChunkValueImpl
- CMFCFilterChunkValueImpl [MFC], Clear
- CMFCFilterChunkValueImpl [MFC], CopyChunk
- CMFCFilterChunkValueImpl [MFC], CopyFrom
- CMFCFilterChunkValueImpl [MFC], GetChunkGUID
- CMFCFilterChunkValueImpl [MFC], GetChunkPID
- CMFCFilterChunkValueImpl [MFC], GetChunkType
- CMFCFilterChunkValueImpl [MFC], GetString
- CMFCFilterChunkValueImpl [MFC], GetValue
- CMFCFilterChunkValueImpl [MFC], GetValueNoAlloc
- CMFCFilterChunkValueImpl [MFC], IsValid
- CMFCFilterChunkValueImpl [MFC], SetBoolValue
- CMFCFilterChunkValueImpl [MFC], SetDwordValue
- CMFCFilterChunkValueImpl [MFC], SetFileTimeValue
- CMFCFilterChunkValueImpl [MFC], SetInt64Value
- CMFCFilterChunkValueImpl [MFC], SetIntValue
- CMFCFilterChunkValueImpl [MFC], SetLongValue
- CMFCFilterChunkValueImpl [MFC], SetSystemTimeValue
- CMFCFilterChunkValueImpl [MFC], SetTextValue
- CMFCFilterChunkValueImpl [MFC], SetChunk
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
ms.openlocfilehash: 2c90a873033516710077d31c8bb8af5fb5172ca6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367505"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>Klasa CMFCFilterChunkValueImpl

Jest to klasa, która upraszcza logikę pary wartości fragmentu i właściwości.

## <a name="syntax"></a>Składnia

```
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|Niszczy obiekt.|
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|Konstruuje obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::Wyczyść](#clear)|Czyści ChunkValue.|
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|Kopiuje ten fragment do struktury opisującej cechy fragmentu.|
|[CMFCFilterChunkValueImpl::CopyFrom](#copyfrom)|Inicjuje tę wartość fragmentu z innej wartości.|
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|Pobiera identyfikator GUID fragmentu.|
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|Pobiera fragment PID (identyfikator właściwości).|
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|Pobiera typ fragmentu.|
|[CMFCFilterChunkValueImpl::GetString](#getstring)|Pobiera wartość ciągu.|
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|Pobiera wartość jako przydzielony propvariant.|
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|Zwraca niepodzielną (wartość wewnętrzną).|
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|Sprawdza, czy ta wartość właściwości jest prawidłowa, czy nie.|
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|Przeciążone. Ustawia właściwość według klucza na wartość logiczną.|
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|Ustawia właściwość według klucza na DWORD.|
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|Ustawia właściwość według klucza na czas pliku.|
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|Ustawia właściwość według klucza do int64.|
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|Ustawia właściwość według klucza na int.|
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|Ustawia właściwość według klucza na LONG.|
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|Ustawia właściwość według klucza na SystemTime.|
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|Ustawia właściwość według klucza na ciąg Unicode.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|Funkcja pomocnika, która ustawia wspólne właściwości fragmentu.|

## <a name="remarks"></a>Uwagi

Aby użyć, wystarczy utworzyć CMFCFilterChunkValueImpl klasy odpowiedniego rodzaju

Przykład:

CMFCFilterChunkValueImpl fragment;

hr = fragment. SetBoolValue(PKEY_IsAttachment, prawda);

lub

hr = fragment. SetFileTimeValue(PKEY_ItemDate, ftLastModified);

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ATL::IFilterChunkValue`

[CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cmfcfilterchunkvalueimplclear"></a><a name="clear"></a>CMFCFilterChunkValueImpl::Wyczyść

Czyści ChunkValue.

```
void Clear();
```

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="cmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl

Konstruuje obiekt.

```
CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="_dtorcmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl

Niszczy obiekt.

```
virtual ~CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplcopychunk"></a><a name="copychunk"></a>CMFCFilterChunkValueImpl::CopyChunk

Kopiuje ten fragment do struktury opisującej cechy fragmentu.

```
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```

### <a name="parameters"></a>Parametry

*pStatChunk (władanie)*<br/>
Wskaźnik do wartości docelowej opisujący właściwości fragmentu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplcopyfrom"></a><a name="copyfrom"></a>CMFCFilterChunkValueImpl::CopyFrom

Inicjuje tę wartość fragmentu z innej wartości.

```
void CopyFrom (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parametry

*wartość pValue*<br/>
Określa wartość źródłową do skopiowania.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplgetchunkguid"></a><a name="getchunkguid"></a>CMFCFilterChunkValueImpl::GetChunkGUID

Pobiera identyfikator GUID fragmentu.

```
REFGUID GetChunkGUID() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do identyfikatora GUID identyfikujące fragment.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplgetchunkpid"></a><a name="getchunkpid"></a>CMFCFilterChunkValueImpl::GetChunkPID

Pobiera fragment PID (identyfikator właściwości).

```
DWORD GetChunkPID() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość DWORD zawierająca identyfikator właściwości.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplgetchunktype"></a><a name="getchunktype"></a>CMFCFilterChunkValueImpl::GetChunkType

Pobiera typ fragmentu.

```
CHUNKSTATE GetChunkType() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość wyliczona CHUNKSTATE, która określa, czy bieżący fragment jest właściwością typu text, czy właściwością typu value.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplgetstring"></a><a name="getstring"></a>CMFCFilterChunkValueImpl::GetString

Pobiera wartość ciągu.

```
CString &GetString();
```

### <a name="return-value"></a>Wartość zwracana

Ciąg zawierający wartość fragmentu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplgetvalue"></a><a name="getvalue"></a>CMFCFilterChunkValueImpl::GetValue

Pobiera wartość jako przydzielony propvariant.

```
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```

### <a name="parameters"></a>Parametry

*ppPropWariant*<br/>
Gdy funkcja zwraca, ten parametr zawiera wartość fragmentu.

### <a name="return-value"></a>Wartość zwracana

S_OK, czy propvariant został przydzielony pomyślnie i wartość fragmentu została pomyślnie skopiowana do *ppPropVariant;* w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplgetvaluenoalloc"></a><a name="getvaluenoalloc"></a>CMFCFilterChunkValueImpl::GetValueNoAlloc

Zwraca wartość nieprzydzielone (wartość wewnętrzną).

```
PROPVARIANT GetValueNoAlloc ();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca bieżącą wartość fragmentu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplisvalid"></a><a name="isvalid"></a>CMFCFilterChunkValueImpl::IsValid

Sprawdza, czy ta wartość właściwości jest prawidłowa, czy nie.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli bieżąca wartość fragmentu jest prawidłowa; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplsetboolvalue"></a><a name="setboolvalue"></a>CMFCFilterChunkValueImpl::SetBoolValue

Przeciążone. Ustawia właściwość według klucza na wartość logiczną.

```
HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);

HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    VARIANT_BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*Pkey*<br/>
Określa klucz właściwości.

*bVal (Ł.*<br/>
Określa wartość fragmentu do ustawionego.

*chunkType*<br/>
Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flag są pobierane z wyliczenia CHUNKSTATE.

*Ustawień regionalnych*<br/>
Język i podjęzyk skojarzony z fragmentem tekstu. Ustawienia regionalne fragmentu są używane przez indeksatory dokumentów do wykonywania prawidłowego podziału wyrazów tekstu. Jeśli fragment nie jest ani typem tekstowym, ani typem wartości z typem danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.

*źródło cwcLenSource*<br/>
Długość znaków tekstu źródłowego, z którego pochodzi bieżący fragment. Wartość zerowa oznacza zgodność między tekstem źródłowym a tekstem pochodnym. Wartość niezerowa oznacza, że taka bezpośrednia korespondencja nie istnieje.

*źródło cwcStartSource*<br/>
Przesunięcie, od którego rozpoczyna się tekst źródłowy dla fragmentu pochodnego w fragmencie źródłowym.

*chunkBreakType (Typ podziału)*<br/>
Typ podziału, który oddziela poprzedni fragment od bieżącego fragmentu. Wartości pochodzą z wyliczenia CHUNK_BREAKTYPE.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplsetchunk"></a><a name="setchunk"></a>CMFCFilterChunkValueImpl::SetChunk

Funkcja pomocnika, która ustawia wspólne właściwości fragmentu.

```
HRESULT SetChunk(
    REFPROPERTYKEY pkey,
    CHUNKSTATE chunkType=CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*Pkey*<br/>
Określa klucz właściwości.

*chunkType*<br/>
Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flag są pobierane z wyliczenia CHUNKSTATE.

*Ustawień regionalnych*<br/>
Język i podjęzyk skojarzony z fragmentem tekstu. Ustawienia regionalne fragmentu są używane przez indeksatory dokumentów do wykonywania prawidłowego podziału wyrazów tekstu. Jeśli fragment nie jest ani typem tekstowym, ani typem wartości z typem danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.

*źródło cwcLenSource*<br/>
Długość znaków tekstu źródłowego, z którego pochodzi bieżący fragment. Wartość zerowa oznacza zgodność między tekstem źródłowym a tekstem pochodnym. Wartość niezerowa oznacza, że taka bezpośrednia korespondencja nie istnieje.

*źródło cwcStartSource*<br/>
Przesunięcie, od którego rozpoczyna się tekst źródłowy dla fragmentu pochodnego w fragmencie źródłowym.

*chunkBreakType (Typ podziału)*<br/>
Typ podziału, który oddziela poprzedni fragment od bieżącego fragmentu. Wartości pochodzą z wyliczenia CHUNK_BREAKTYPE.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplsetdwordvalue"></a><a name="setdwordvalue"></a>CMFCFilterChunkValueImpl::SetDwordValue

Ustaw właściwość według klucza na DWORD.

```
HRESULT SetDwordValue(
    REFPROPERTYKEY pkey,
    DWORD dwVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*Pkey*<br/>
Określa klucz właściwości.

*Dwval*<br/>
Określa wartość fragmentu do ustawionego.

*chunkType*<br/>
Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flag są pobierane z wyliczenia CHUNKSTATE.

*Ustawień regionalnych*<br/>
Język i podjęzyk skojarzony z fragmentem tekstu. Ustawienia regionalne fragmentu są używane przez indeksatory dokumentów do wykonywania prawidłowego podziału wyrazów tekstu. Jeśli fragment nie jest ani typem tekstowym, ani typem wartości z typem danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.

*źródło cwcLenSource*<br/>
Długość znaków tekstu źródłowego, z którego pochodzi bieżący fragment. Wartość zerowa oznacza zgodność między tekstem źródłowym a tekstem pochodnym. Wartość niezerowa oznacza, że taka bezpośrednia korespondencja nie istnieje.

*źródło cwcStartSource*<br/>
Przesunięcie, od którego rozpoczyna się tekst źródłowy dla fragmentu pochodnego w fragmencie źródłowym.

*chunkBreakType (Typ podziału)*<br/>
Typ podziału, który oddziela poprzedni fragment od bieżącego fragmentu. Wartości pochodzą z wyliczenia CHUNK_BREAKTYPE.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplsetfiletimevalue"></a><a name="setfiletimevalue"></a>CMFCFilterChunkValueImpl::SetFileTimeValue

Ustaw właściwość według klucza na czas pliku.

```
HRESULT SetFileTimeValue(
    REFPROPERTYKEY pkey,
    FILETIME dtVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*Pkey*<br/>
Określa klucz właściwości.

*dtVal (właso)*<br/>
Określa wartość fragmentu do ustawionego.

*chunkType*<br/>
Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flag są pobierane z wyliczenia CHUNKSTATE.

*Ustawień regionalnych*<br/>
Język i podjęzyk skojarzony z fragmentem tekstu. Ustawienia regionalne fragmentu są używane przez indeksatory dokumentów do wykonywania prawidłowego podziału wyrazów tekstu. Jeśli fragment nie jest ani typem tekstowym, ani typem wartości z typem danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.

*źródło cwcLenSource*<br/>
Długość znaków tekstu źródłowego, z którego pochodzi bieżący fragment. Wartość zerowa oznacza zgodność między tekstem źródłowym a tekstem pochodnym. Wartość niezerowa oznacza, że taka bezpośrednia korespondencja nie istnieje.

*źródło cwcStartSource*<br/>
Przesunięcie, od którego rozpoczyna się tekst źródłowy dla fragmentu pochodnego w fragmencie źródłowym.

*chunkBreakType (Typ podziału)*<br/>
Typ podziału, który oddziela poprzedni fragment od bieżącego fragmentu. Wartości pochodzą z wyliczenia CHUNK_BREAKTYPE.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplsetint64value"></a><a name="setint64value"></a>CMFCFilterChunkValueImpl::SetInt64Value

Ustaw właściwość według klucza do int64.

```
HRESULT SetInt64Value(
    REFPROPERTYKEY pkey,
    __int64 nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*Pkey*<br/>
Określa klucz właściwości.

*nVal (Ł.*<br/>
Określa wartość fragmentu do ustawionego.

*chunkType*<br/>
Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flag są pobierane z wyliczenia CHUNKSTATE.

*Ustawień regionalnych*<br/>
Język i podjęzyk skojarzony z fragmentem tekstu. Ustawienia regionalne fragmentu są używane przez indeksatory dokumentów do wykonywania prawidłowego podziału wyrazów tekstu. Jeśli fragment nie jest ani typem tekstowym, ani typem wartości z typem danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.

*źródło cwcLenSource*<br/>
Długość znaków tekstu źródłowego, z którego pochodzi bieżący fragment. Wartość zerowa oznacza zgodność między tekstem źródłowym a tekstem pochodnym. Wartość niezerowa oznacza, że taka bezpośrednia korespondencja nie istnieje.

*źródło cwcStartSource*<br/>
Przesunięcie, od którego rozpoczyna się tekst źródłowy dla fragmentu pochodnego w fragmencie źródłowym.

*chunkBreakType (Typ podziału)*<br/>
Typ podziału, który oddziela poprzedni fragment od bieżącego fragmentu. Wartości pochodzą z wyliczenia CHUNK_BREAKTYPE.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplsetintvalue"></a><a name="setintvalue"></a>CMFCFilterChunkValueImpl::SetIntValue

Ustaw właściwość według klucza do int.

```
HRESULT SetIntValue(
    REFPROPERTYKEY pkey,
    int nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*Pkey*<br/>
Określa klucz właściwości.

*nVal (Ł.*<br/>
Określa wartość fragmentu do ustawionego.

*chunkType*<br/>
Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flag są pobierane z wyliczenia CHUNKSTATE.

*Ustawień regionalnych*<br/>
Język i podjęzyk skojarzony z fragmentem tekstu. Ustawienia regionalne fragmentu są używane przez indeksatory dokumentów do wykonywania prawidłowego podziału wyrazów tekstu. Jeśli fragment nie jest ani typem tekstowym, ani typem wartości z typem danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.

*źródło cwcLenSource*<br/>
Długość znaków tekstu źródłowego, z którego pochodzi bieżący fragment. Wartość zerowa oznacza zgodność między tekstem źródłowym a tekstem pochodnym. Wartość niezerowa oznacza, że taka bezpośrednia korespondencja nie istnieje.

*źródło cwcStartSource*<br/>
Przesunięcie, od którego rozpoczyna się tekst źródłowy dla fragmentu pochodnego w fragmencie źródłowym.

*chunkBreakType (Typ podziału)*<br/>
Typ podziału, który oddziela poprzedni fragment od bieżącego fragmentu. Wartości pochodzą z wyliczenia CHUNK_BREAKTYPE.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplsetlongvalue"></a><a name="setlongvalue"></a>CMFCFilterChunkValueImpl::SetLongValue

Ustaw właściwość według klucza na LONG.

```
HRESULT SetLongValue(
    REFPROPERTYKEY pkey,
    long lVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*Pkey*<br/>
Określa klucz właściwości.

*lVal (Ł.*<br/>
Określa wartość fragmentu do ustawionego.

*chunkType*<br/>
Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flag są pobierane z wyliczenia CHUNKSTATE.

*Ustawień regionalnych*<br/>
Język i podjęzyk skojarzony z fragmentem tekstu. Ustawienia regionalne fragmentu są używane przez indeksatory dokumentów do wykonywania prawidłowego podziału wyrazów tekstu. Jeśli fragment nie jest ani typem tekstowym, ani typem wartości z typem danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.

*źródło cwcLenSource*<br/>
Długość znaków tekstu źródłowego, z którego pochodzi bieżący fragment. Wartość zerowa oznacza zgodność między tekstem źródłowym a tekstem pochodnym. Wartość niezerowa oznacza, że taka bezpośrednia korespondencja nie istnieje.

*źródło cwcStartSource*<br/>
Przesunięcie, od którego rozpoczyna się tekst źródłowy dla fragmentu pochodnego w fragmencie źródłowym.

*chunkBreakType (Typ podziału)*<br/>
Typ podziału, który oddziela poprzedni fragment od bieżącego fragmentu. Wartości pochodzą z wyliczenia CHUNK_BREAKTYPE.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplsetsystemtimevalue"></a><a name="setsystemtimevalue"></a>CMFCFilterChunkValueImpl::SetSystemTimeValue

Ustawia właściwość według klucza na SystemTime.

```
HRESULT SetSystemTimeValue(
    REFPROPERTYKEY pkey,
    const SYSTEMTIME& systemTime,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*Pkey*<br/>
Określa klucz właściwości.

*Systemtime*<br/>
Określa wartość fragmentu do ustawionego.

*chunkType*<br/>
Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flag są pobierane z wyliczenia CHUNKSTATE.

*Ustawień regionalnych*<br/>
Język i podjęzyk skojarzony z fragmentem tekstu. Ustawienia regionalne fragmentu są używane przez indeksatory dokumentów do wykonywania prawidłowego podziału wyrazów tekstu. Jeśli fragment nie jest ani typem tekstowym, ani typem wartości z typem danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.

*źródło cwcLenSource*<br/>
Długość znaków tekstu źródłowego, z którego pochodzi bieżący fragment. Wartość zerowa oznacza zgodność między tekstem źródłowym a tekstem pochodnym. Wartość niezerowa oznacza, że taka bezpośrednia korespondencja nie istnieje.

*źródło cwcStartSource*<br/>
Przesunięcie, od którego rozpoczyna się tekst źródłowy dla fragmentu pochodnego w fragmencie źródłowym.

*chunkBreakType (Typ podziału)*<br/>
Typ podziału, który oddziela poprzedni fragment od bieżącego fragmentu. Wartości pochodzą z wyliczenia CHUNK_BREAKTYPE.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcfilterchunkvalueimplsettextvalue"></a><a name="settextvalue"></a>CMFCFilterChunkValueImpl::SetTextValue

Ustawia właściwość według klucza na ciąg Unicode.

```
HRESULT SetTextValue(
    REFPROPERTYKEY pkey,
    LPCTSTR pszValue,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*Pkey*<br/>
Określa klucz właściwości.

*pszValue (właskw.*<br/>
Określa wartość fragmentu do ustawionego.

*chunkType*<br/>
Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flag są pobierane z wyliczenia CHUNKSTATE.

*Ustawień regionalnych*<br/>
Język i podjęzyk skojarzony z fragmentem tekstu. Ustawienia regionalne fragmentu są używane przez indeksatory dokumentów do wykonywania prawidłowego podziału wyrazów tekstu. Jeśli fragment nie jest ani typem tekstowym, ani typem wartości z typem danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.

*źródło cwcLenSource*<br/>
Długość znaków tekstu źródłowego, z którego pochodzi bieżący fragment. Wartość zerowa oznacza zgodność między tekstem źródłowym a tekstem pochodnym. Wartość niezerowa oznacza, że taka bezpośrednia korespondencja nie istnieje.

*źródło cwcStartSource*<br/>
Przesunięcie, od którego rozpoczyna się tekst źródłowy dla fragmentu pochodnego w fragmencie źródłowym.

*chunkBreakType (Typ podziału)*<br/>
Typ podziału, który oddziela poprzedni fragment od bieżącego fragmentu. Wartości pochodzą z wyliczenia CHUNK_BREAKTYPE.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
