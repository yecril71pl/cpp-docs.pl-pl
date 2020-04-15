---
title: Funkcje wymiany danych w oknie dialogowym dla formularzy CRecordView i CDaoRecordView
ms.date: 09/17/2019
f1_keywords:
- AFXDAO/DDX_FieldCBIndex
- AFXDAO/DDX_FieldCBString
- AFXDAO/DDX_FieldCBStringExact
- AFXDAO/DDX_FieldCheck
- AFXDAO/DDX_FieldLBIndex
- AFXDAO/DDX_FieldLBString
- AFXDAO/DDX_FieldLBStringExact
- AFXDAO/DDX_FieldRadio
- AFXDAO/DDX_FieldScroll
- AFXDAO/DDX_FieldText
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
ms.openlocfilehash: 3128b1ba459cb017d1cdb2321bc55d865aa4f8b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365776"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Funkcje wymiany danych w oknie dialogowym dla formularzy CRecordView i CDaoRecordView

W tym temacie wymieniono DDX_Field funkcji używanych do wymiany danych między [CRecordset](../../mfc/reference/crecordset-class.md) i [CRecordView](../../mfc/reference/crecordview-class.md) formularza lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) formularza. DAO jest używany z bazami danych programu Access i jest obsługiwany przez pakiet Office 2013. DAO 3.6 jest ostateczną wersją i jest uważana za przestarzałą.

> [!NOTE]
> DDX_Field funkcje są jak funkcje DDX, ponieważ wymieniają dane z formantami w formularzu. Jednak w przeciwieństwie do DDX wymieniają dane z polami obiektu skojarzonego z zestawem rekordów widoku, a nie z polami samego widoku rekordu. Aby uzyskać więcej `CRecordView` informacji, zobacz klasy i `CDaoRecordView`.

### <a name="ddx_field-functions"></a>funkcje DDX_Field

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|Przesyła dane całkowite między elementem członkowskim pola pliku recordset a indeksem bieżącego zaznaczenia w polu kombi w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|
|[DDX_FieldCBString](#ddx_fieldcbstring)|Przesyła `CString` dane między elementem członkowskim danych pola zbioru rekordów `CRecordView` `CDaoRecordView`a formantem edycji pola kombi w pliku a lub . Podczas przenoszenia danych z zestawu rekordów do formantu ta funkcja wybiera element w polu kombi, który rozpoczyna się od znaków w określonym ciągu.|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|Przesyła `CString` dane między elementem członkowskim danych pola zbioru rekordów `CRecordView` `CDaoRecordView`a formantem edycji pola kombi w pliku a lub . Podczas przenoszenia danych z zestawu rekordów do formantu ta funkcja wybiera element w polu kombi, który dokładnie pasuje do określonego ciągu.|
|[DDX_FieldCheck](#ddx_fieldcheck)|Przesyła dane logiczne między elementem członkowskim pola zbioru rekordów a polem `CRecordView` wyboru w polu . `CDaoRecordView`|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|Przesyła dane całkowite między elementem członkowskim danych pola zestawie rekordów a indeksem bieżącego zaznaczenia w polu listy w `CRecordView` polu lub . `CDaoRecordView`|
|[DDX_FieldLBString](#ddx_fieldlbstring)|Zarządza transferem danych [CString](../../atl-mfc-shared/reference/cstringt-class.md) między formantem pola listy a członkami danych pola zestawie rekordów. Podczas przenoszenia danych z zestawie rekordów do formantu ta funkcja wybiera element w polu listy, który rozpoczyna się od znaków w określonym ciągu.|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|Zarządza transferem `CString` danych między formantem pola listy a członkami danych pola zestawie rekordów. Podczas przenoszenia danych z zestawu rekordów do formantu ta funkcja wybiera pierwszy element, który dokładnie pasuje do określonego ciągu.|
|[DDX_FieldRadio](#ddx_fieldradio)|Przesyła dane całkowite między elementem członkowskim pola pliku recordset `CRecordView` a `CDaoRecordView`grupą przycisków radiowych w pliku lub .|
|[DDX_FieldScroll](#ddx_fieldscroll)|Ustawia lub pobiera pozycję przewijania formantu paska przewijania w lub `CRecordView` . `CDaoRecordView` Zadzwoń z funkcji [DoFieldExchange.](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)|
|[DDX_FieldSlider](#ddx_fieldslider)|Synchronizuje położenie kciuka formantu suwaka w `int` widoku rekordu i członka danych pola w zbiorze rekordów. |
|[DDX_FieldText](#ddx_fieldtext)|Przeciążone wersje są dostępne `int`do przesyłania , `DWORD` **UINT**, **long**, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **double**, **short**, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)i [COleCurrency](../../mfc/reference/colecurrency-class.md) danych między elementem członkowskim pola recordset i pole edycji w `CRecordView` lub . `CDaoRecordView`|

## <a name="ddx_fieldcbindex"></a><a name="ddx_fieldcbindex"></a>DDX_FieldCBIndex

Funkcja `DDX_FieldCBIndex` synchronizuje indeks zaznaczonego elementu w formancie pola listy formantu pola `int` kombi w widoku rekordu i członka danych pola z zestawem rekordów skojarzonym z widokiem rekordu.

```cpp
void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*Indeks*<br/>
Odwołanie do elementu członkowskiego danych pola `CRecordset` `CDaoRecordset` w skojarzonym lub obiektu.

*pRekord*<br/>
Wskaźnik do [obiektu CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) za pomocą którego są wymieniane dane.

### <a name="remarks"></a>Uwagi

Podczas przenoszenia danych z zestawu rekordów do formantu ta funkcja ustawia zaznaczenie w formancie na podstawie wartości określonej w *indeksie*. W przypadku transferu z zestawu rekordów do formantu, jeśli pole zestaw rekordów jest Null, MFC ustawia wartość indeksu na 0. W przypadku transferu z formantu do zestawu rekordów, jeśli formant jest pusty lub jeśli nie wybrano żadnego elementu, pole zestawu rekordów jest ustawione na 0.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać przykłady i więcej informacji na temat pól DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) zobacz artykuł [Widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText,](#ddx_fieldtext) aby zapoznać się DDX_Field przykładem. Przykład może być `DDX_FieldCBIndex`podobny dla .

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="ddx_fieldcbstring"></a><a name="ddx_fieldcbstring"></a>DDX_FieldCBString

Funkcja `DDX_FieldCBString` zarządza transferem danych [CString](../../atl-mfc-shared/reference/cstringt-class.md) między formantem edycji formantu pola `CString` kombi w widoku rekordu a elementem członkowskim danych pola z zestawem rekordów skojarzonym z widokiem rekordu.

```cpp
void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*value*<br/>
Odwołanie do elementu członkowskiego danych pola `CRecordset` `CDaoRecordset` w skojarzonym lub obiektu.

*pRekord*<br/>
Wskaźnik do [obiektu CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) za pomocą którego są wymieniane dane.

### <a name="remarks"></a>Uwagi

Podczas przenoszenia danych z zbioru rekordów do formantu ta funkcja ustawia bieżące zaznaczenie w polu kombi na pierwszy wiersz rozpoczynający się od znaków w ciągu określonym w *wartości*. W przypadku transferu z zestawu rekordów do formantu, jeśli pole zestawu rekordów jest null, wszelkie zaznaczenia są usuwane z pola kombi, a formant edycji pola kombi jest ustawiony na pusty. W przypadku transferu z formantu do zestawu rekordów, jeśli formant jest pusty, pole zestawu rekordów jest ustawione na Null, jeśli pole na to pozwala.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać przykłady i więcej informacji na temat pól DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) zobacz artykuł [Widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText,](#ddx_fieldtext) aby zapoznać się DDX_Field przykładem. Przykład zawiera wywołanie `DDX_FieldCBString`.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

## <a name="ddx_fieldcbstringexact"></a><a name="ddx_fieldcbstringexact"></a>DDX_FieldCBStringExact

Funkcja `DDX_FieldCBStringExact` zarządza transferem danych [CString](../../atl-mfc-shared/reference/cstringt-class.md) między formantem edycji formantu pola `CString` kombi w widoku rekordu a elementem członkowskim danych pola z zestawem rekordów skojarzonym z widokiem rekordu.

```cpp
void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*value*<br/>
Odwołanie do elementu członkowskiego danych pola `CRecordset` `CDaoRecordset` w skojarzonym lub obiektu.

*pRekord*<br/>
Wskaźnik do [obiektu CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) za pomocą którego są wymieniane dane.

### <a name="remarks"></a>Uwagi

Podczas przenoszenia danych z zestawu rekordów do formantu ta funkcja ustawia bieżące zaznaczenie w polu kombi na pierwszy wiersz, który dokładnie odpowiada ciągowi określonej w *wartości*. W przypadku transferu z zestawu rekordów do formantu, jeśli pole zestawu rekordów ma wartość NULL, każde zaznaczenie jest usuwane z pola kombi, a pole edycji pola kombi jest puste. W przypadku transferu z formantu do zestawu rekordów, jeśli formant jest pusty, pole zestawu rekordów jest ustawione na wartość NULL.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać przykłady i więcej informacji na temat pól DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) zobacz artykuł [Widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText,](#ddx_fieldtext) aby zapoznać się DDX_Field przykładem. Wezwania `DDX_FieldCBStringExact` byłyby podobne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

## <a name="ddx_fieldcheck"></a><a name="ddx_fieldcheck"></a>DDX_FieldCheck

Funkcja `DDX_FieldCheck` zarządza transferem danych **int** między formantem pola wyboru w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem członkowskim danych **int** okna dialogowego, widoku formularza lub obiektu widoku sterującego.

```cpp
void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu pola wyboru skojarzonego z właściwością formantu.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

*pRekord*<br/>
Wskaźnik do [obiektu CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) za pomocą którego są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_FieldCheck` jest wywoływana, *wartość* jest ustawiona na bieżący stan formantu pola wyboru lub stan formantu jest ustawiona na *wartość*, w zależności od kierunku transferu.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

## <a name="ddx_fieldlbindex"></a><a name="ddx_fieldlbindex"></a>DDX_FieldLBIndex

Funkcja `DDX_FieldLBIndex` synchronizuje indeks zaznaczonego elementu w formancie pola listy w widoku rekordu i element członkowski danych pola **int** zestawie rekordów skojarzony z widokiem rekordu.

```cpp
void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*Indeks*<br/>
Odwołanie do elementu członkowskiego danych pola `CRecordset` `CDaoRecordset` w skojarzonym lub obiektu.

*pRekord*<br/>
Wskaźnik do [obiektu CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) za pomocą którego są wymieniane dane.

### <a name="remarks"></a>Uwagi

Podczas przenoszenia danych z zestawu rekordów do formantu ta funkcja ustawia zaznaczenie w formancie na podstawie wartości określonej w *indeksie*. W przypadku transferu z zestawu rekordów do formantu, jeśli pole zestaw rekordów jest Null, MFC ustawia wartość indeksu na 0. W przypadku transferu z formantu do zestawu rekordów, jeśli formant jest pusty, pole zestawu rekordów jest ustawione na 0.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać przykłady i więcej informacji na temat pól DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) zobacz artykuł [Widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText,](#ddx_fieldtext) aby zapoznać się DDX_Field przykładem.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

## <a name="ddx_fieldlbstring"></a><a name="ddx_fieldlbstring"></a>DDX_FieldLBString

Kopiuje `DDX_FieldLBString` bieżący wybór formantu pola listy w widoku rekordu do członka danych pola [CString](../../atl-mfc-shared/reference/cstringt-class.md) w zestawie rekordów skojarzonym z widokiem rekordu.

```cpp
void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*value*<br/>
Odwołanie do elementu członkowskiego danych pola `CRecordset` `CDaoRecordset` w skojarzonym lub obiektu.

*pRekord*<br/>
Wskaźnik do [obiektu CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) za pomocą którego są wymieniane dane.

### <a name="remarks"></a>Uwagi

W kierunku odwrotnym ta funkcja ustawia bieżące zaznaczenie w polu listy na pierwszy wiersz, który zaczyna się od znaków w ciągu określonym przez *wartość*. W przypadku transferu z zestawie rekordów do formantu, jeśli pole zestawie rekordów jest null, wszelkie zaznaczenia są usuwane z pola listy. W przypadku transferu z formantu do zestawu rekordów, jeśli formant jest pusty, pole zestawu rekordów jest ustawione na Wartość Null.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać przykłady i więcej informacji na temat pól DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) zobacz artykuł [Widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText,](#ddx_fieldtext) aby zapoznać się DDX_Field przykładem. Wezwania `DDX_FieldLBString` byłyby podobne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

## <a name="ddx_fieldlbstringexact"></a><a name="ddx_fieldlbstringexact"></a>DDX_FieldLBStringExact

Funkcja `DDX_FieldLBStringExact` kopiuje bieżący wybór formantu pola listy w widoku rekordu do elementu członkowskiego danych pola [CString](../../atl-mfc-shared/reference/cstringt-class.md) w zestawie rekordów skojarzonym z widokiem rekordu.

```cpp
void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*value*<br/>
Odwołanie do elementu członkowskiego danych pola `CRecordset` `CDaoRecordset` w skojarzonym lub obiektu.

*pRekord*<br/>
Wskaźnik do [obiektu CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) za pomocą którego są wymieniane dane.

### <a name="remarks"></a>Uwagi

W odwrotnym kierunku ta funkcja ustawia bieżące zaznaczenie w polu listy na pierwszy wiersz, który dokładnie pasuje do ciągu określonego w *wartości*. W przypadku transferu z zestawie rekordów do formantu, jeśli pole zestawie rekordów jest null, wszelkie zaznaczenia są usuwane z pola listy. W przypadku transferu z formantu do zestawu rekordów, jeśli formant jest pusty, pole zestawu rekordów jest ustawione na Wartość Null.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać przykłady i więcej informacji na temat pól DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) zobacz artykuł [Widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText,](#ddx_fieldtext) aby zapoznać się DDX_Field przykładem. Wezwania `DDX_FieldLBStringExact` byłyby podobne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

## <a name="ddx_fieldradio"></a><a name="ddx_fieldradio"></a>DDX_FieldRadio

Funkcja `DDX_FieldRadio` kojarzy zmienną **elementów** członkowskich int opartą na wartości zerowej w akuplcie widoku rekordu z aktualnie wybranym przyciskiem opcji w grupie przycisków radiowych w widoku rekordu.

```cpp
void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator pierwszego w grupie (ze stylem WS_GROUP) sąsiednich formantu przycisku radiowego w [obiekcie CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Odwołanie do elementu członkowskiego danych pola `CRecordset` `CDaoRecordset` w skojarzonym lub obiektu.

*pRekord*<br/>
Wskaźnik do [obiektu CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) za pomocą którego są wymieniane dane.

### <a name="remarks"></a>Uwagi

Podczas przenoszenia z pola zestaw rekordów do widoku ta funkcja włącza *n-ty* przycisk radiowy (oparty na wartości zero) i wyłącza inne przyciski. W odwrotnym kierunku ta funkcja ustawia pole zestawu rekordów na numer porządkowy przycisku opcji, który jest aktualnie włączony (zaznaczony). W przypadku transferu z listy rekordów do formantu, jeśli polemikawnika rekordów ma wartość Null, nie wybrano żadnego przycisku. W przypadku transferu z formantu do zestawu rekordów, jeśli nie wybrano żadnej kontroli, pole zestawu rekordów jest ustawione na Null, jeśli pole na to zezwala.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać przykłady i więcej informacji na temat pól DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) zobacz artykuł [Widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText,](#ddx_fieldtext) aby zapoznać się DDX_Field przykładem. Wezwania `DDX_FieldRadio` byłyby podobne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

## <a name="ddx_fieldscroll"></a><a name="ddx_fieldscroll"></a>DDX_FieldScroll

Funkcja `DDX_FieldScroll` synchronizuje położenie przewijania formantu paska przewijania w widoku rekordu i elementu członkowskiego danych pola **int** w komecie rekordów skojarzonego z widokiem rekordu (lub ze zmienną całkowitą, na którą chcesz go zamapować).

```cpp
void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator pierwszego w grupie (ze stylem WS_GROUP) sąsiednich formantu przycisku radiowego w [obiekcie CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Odwołanie do elementu członkowskiego danych pola `CRecordset` `CDaoRecordset` w skojarzonym lub obiektu.

*pRekord*<br/>
Wskaźnik do [obiektu CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) za pomocą którego są wymieniane dane.

### <a name="remarks"></a>Uwagi

Podczas przenoszenia danych z zestawu rekordów do formantu ta funkcja ustawia położenie przewijania formantu paska przewijania na wartość *określoną*w wartości . W przypadku transferu z zestawu rekordów do formantu, jeśli pole zestawu rekordów jest null, kontrolka paska przewijania jest ustawiona na 0. W przypadku transferu z formantu do formantu, jeśli formant jest pusty, wartość pola pliku recordset wynosi 0.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać przykłady i więcej informacji na temat pól DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) zobacz artykuł [Widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText,](#ddx_fieldtext) aby zapoznać się DDX_Field przykładem. Wezwania `DDX_FieldScroll` byłyby podobne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

## <a name="ddx_fieldslider"></a><a name="ddx_fieldslider"></a>DDX_FieldSlider

Funkcja `DDX_FieldSlider` synchronizuje położenie kciuka formantu suwaka w widoku rekordu i element członkowski danych pola **int** zestawu rekordów skojarzonego z widokiem rekordu (lub ze zmienną całkowitą, na którą chcesz go zamapować).

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI DDX_FieldSlider(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset );

void AFXAPI DDX_FieldSlider(
   CDataExchange* pDX,
   int nIDC,
   int& value,
   CDaoRecordset* pRecordset );
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu suwaka.

*value*<br/>
Odwołanie do wartości, która ma zostać wymieniona. Ten parametr zawiera lub będzie używany do ustawiania bieżącej pozycji kciuka formantu suwaka.

*pRekord*<br/>
Wskaźnik do skojarzonego `CRecordset` `CDaoRecordset` lub obiektu, z którym dane są wymieniane.

### <a name="remarks"></a>Uwagi

Podczas przenoszenia danych z zestawu rekordów do suwaka ta funkcja ustawia położenie suwaka na wartość *określoną*w wartości . W przypadku transferu z zestawu rekordów do formantu, jeśli pole zestawu rekordów jest Null, położenie formantu suwaka jest ustawione na 0. W przypadku transferu z formantu do formantu, jeśli formant jest pusty, wartość pola recordset wynosi 0.

`DDX_FieldSlider`nie wymienia informacji o zakresie za pomocą suwaków umożliwiających ustawienie zakresu, a nie tylko pozycję.

Użyj pierwszego zastąpienia funkcji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiego zastąpienia z klasami opartymi na DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../dialog-data-exchange-and-validation.md). Aby uzyskać przykłady i więcej `CRecordView` informacji `CDaoRecordView` o DDX dla i pola, zobacz [Rejestrowanie widoków](../../data/record-views-mfc-data-access.md). Aby uzyskać informacje na temat kontrolek suwaków, zobacz [Korzystanie z CSliderCtrl](../using-csliderctrl.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText,](#ddx_fieldtext) aby zapoznać się DDX_Field przykładem. Wezwania `DDX_FieldSlider` byłyby podobne.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="ddx_fieldtext"></a><a name="ddx_fieldtext"></a>DDX_FieldText

Funkcja `DDX_FieldText` zarządza transferem danych **int,** **short,** **long**, DWORD, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **double**, **BOOL**lub **BYTE** między formantem pola edycji a elementami elementów członkowskich danych pola w zbiorze rekordów.

```cpp
void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    UINT& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    short& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BOOL& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*value*<br/>
Odwołanie do elementu członkowskiego danych pola `CRecordset` `CDaoRecordset` w skojarzonym lub obiektu. Typ danych wartości zależy od tego, które `DDX_FieldText` z przeciążonych wersji używasz.

*pRekord*<br/>
Wskaźnik do [obiektu CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) za pomocą którego są wymieniane dane. Ten wskaźnik `DDX_FieldText` umożliwia wykrywanie i ustawianie wartości null.

### <a name="remarks"></a>Uwagi

W przypadku obiektów [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) zarządza `DDX_FieldText` również transferami [wartości COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)i [COleCurrency.](../../mfc/reference/colecurrency-class.md) Formant pustego pola edycji wskazuje wartość Null. W przypadku transferu z zestawu rekordów do formantu, jeśli pole zestawu rekordów ma wartość Null, pole edycji jest ustawione na puste. W przypadku transferu z formantu do zestawu rekordów, jeśli formant jest pusty, pole zestawu rekordów jest ustawione na Wartość Null.

Użyj wersji z [CRecordset](../../mfc/reference/crecordset-class.md) parametrów, jeśli pracujesz z klas opartych na ODBC. Użyj wersji z parametrami [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) jeśli pracujesz z klasami opartymi na DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać przykłady i więcej informacji na temat pól DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) zobacz artykuł [Widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Następująca `DoDataExchange` funkcja dla [CRecordView](../../mfc/reference/crecordview-class.md) zawiera `DDX_FieldText` wywołania `IDC_COURSELIST` funkcji dla trzech typów danych: jest polem kombi; pozostałe dwa formanty są pola edycji. W przypadku programowania DAO parametr *m_pSet* jest wskaźnikiem do [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](mfc-macros-and-globals.md)
