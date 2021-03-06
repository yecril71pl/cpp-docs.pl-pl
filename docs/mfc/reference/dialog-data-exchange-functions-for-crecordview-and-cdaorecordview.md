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
ms.openlocfilehash: 06d0511317c21f6b132349d7d6cd6c2d6f20bc1b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837375"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Funkcje wymiany danych w oknie dialogowym dla formularzy CRecordView i CDaoRecordView

W tym temacie wymieniono funkcje DDX_Field używane do wymiany danych między [CRecordset](../../mfc/reference/crecordset-class.md) i formularzem [formularzy CRecordView](../../mfc/reference/crecordview-class.md) lub formularzem [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) . Obiekty DAO są używane z bazami danych programu Access i są obsługiwane za pomocą pakietu Office 2013. Element DAO 3,6 jest wersją ostateczną i jest uznawany za przestarzały.

> [!NOTE]
> Funkcje DDX_Field są podobne do funkcji DDX w tym, że wymieniają dane za pomocą kontrolek w formularzu. Ale w przeciwieństwie do DDX, wymieniają dane z polami obiektu zestawu rekordów widoku, a nie z polami widoku rekordu. Aby uzyskać więcej informacji, zobacz klasy `CRecordView` i `CDaoRecordView` .

### <a name="ddx_field-functions"></a>Funkcje DDX_Field

|Nazwa|Opis|
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|Przesyła dane całkowite między elementem członkowskim danych pola zestawu rekordów i indeksem bieżącego zaznaczenia w polu kombi w [formularzy CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|
|[DDX_FieldCBString](#ddx_fieldcbstring)|Przesyła `CString` dane między składową danych pola zestawu rekordów i kontrolki edycji pola kombi w `CRecordView` lub `CDaoRecordView` . Podczas przesuwania danych z zestawu rekordów do kontrolki ta funkcja wybiera element w polu kombi, który rozpoczyna się od znaków w określonym ciągu.|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|Przesyła `CString` dane między składową danych pola zestawu rekordów i kontrolki edycji pola kombi w `CRecordView` lub `CDaoRecordView` . Podczas przesuwania danych z zestawu rekordów do kontrolki ta funkcja wybiera element w polu kombi, który dokładnie pasuje do określonego ciągu.|
|[DDX_FieldCheck](#ddx_fieldcheck)|Przesyła dane logiczne między elementem członkowskim danych pola zestawu rekordów a polem wyboru w `CRecordView` lub `CDaoRecordView` .|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|Przenosi dane całkowite między elementem członkowskim danych pola zestawu rekordów a indeksem bieżącego zaznaczenia w polu listy w `CRecordView` lub `CDaoRecordView` .|
|[DDX_FieldLBString](#ddx_fieldlbstring)|Zarządza transferem danych [CString](../../atl-mfc-shared/reference/cstringt-class.md) między kontrolką pola listy i elementami członkowskimi danych pola zestawu rekordów. Podczas przesuwania danych z zestawu rekordów do kontrolki ta funkcja wybiera element w polu listy, który rozpoczyna się od znaków w określonym ciągu.|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|Zarządza przesyłaniem `CString` danych między kontrolką pola listy i elementami członkowskimi danych pola zestawu rekordów. Podczas przesuwania danych z zestawu rekordów do kontrolki ta funkcja wybiera pierwszy element, który dokładnie pasuje do określonego ciągu.|
|[DDX_FieldRadio](#ddx_fieldradio)|Przenosi dane całkowite między elementem członkowskim danych pola zestawu rekordów i grupą przycisków radiowych w `CRecordView` lub `CDaoRecordView` .|
|[DDX_FieldScroll](#ddx_fieldscroll)|Ustawia lub Pobiera pozycję przewijania kontrolki paska przewijania w `CRecordView` lub `CDaoRecordView` . Wywołanie z funkcji [DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) .|
|[DDX_FieldSlider](#ddx_fieldslider)|Synchronizuje położenie kciuka kontrolki suwaka w widoku rekordu i **`int`** element członkowski danych pola zestawu rekordów. |
|[DDX_FieldText](#ddx_fieldtext)|Przeciążone wersje są dostępne do transferowania **`int`** , **uint**,,, CString,,,, **`long`** `DWORD` [CString](../../atl-mfc-shared/reference/cstringt-class.md) **`float`** **`double`** **`short`** [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)i [COleCurrency](../../mfc/reference/colecurrency-class.md) danych między składową danych pola zestawu rekordów a polem edycji w `CRecordView` lub `CDaoRecordView` .|

## <a name="ddx_fieldcbindex"></a><a name="ddx_fieldcbindex"></a> DDX_FieldCBIndex

`DDX_FieldCBIndex`Funkcja synchronizuje indeks zaznaczonego elementu w kontrolce pole kombi w widoku rekordu i element **`int`** członkowski danych pola zestawu rekordów skojarzonego z widokiem rekordu.

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki w obiekcie [formularzy CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*index*<br/>
Odwołanie do elementu członkowskiego danych pola w obiekcie skojarzonym `CRecordset` lub `CDaoRecordset` .

*pRecordset*<br/>
Wskaźnik do obiektu [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Podczas przesuwania danych z zestawu rekordów do kontrolki ta funkcja ustawia zaznaczenie w kontrolce na podstawie wartości określonej w *indeksie*. W przypadku transferu z zestawu rekordów do formantu, jeśli pole zestaw rekordów ma wartość null, MFC ustawi wartość indeksu na 0. W przypadku transferu z kontroli do zestawu rekordów, Jeśli kontrolka jest pusta lub jeśli żaden element nie jest zaznaczony, pole zestaw rekordów jest ustawione na 0.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na programie DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla pól [formularzy CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) można znaleźć w artykułach [widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText](#ddx_fieldtext) , aby uzyskać przykład DDX_Field ogólny. Przykład będzie podobny do `DDX_FieldCBIndex` .

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="ddx_fieldcbstring"></a><a name="ddx_fieldcbstring"></a> DDX_FieldCBString

`DDX_FieldCBString`Funkcja zarządza transferem danych [CString](../../atl-mfc-shared/reference/cstringt-class.md) między kontrolką edycji kontrolki pola kombi w widoku rekordu i elementem `CString` członkowskim danych pola zestawu rekordów skojarzonego z widokiem rekordu.

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki w obiekcie [formularzy CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*wartościami*<br/>
Odwołanie do elementu członkowskiego danych pola w obiekcie skojarzonym `CRecordset` lub `CDaoRecordset` .

*pRecordset*<br/>
Wskaźnik do obiektu [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Podczas przesuwania danych z zestawu rekordów do kontrolki ta funkcja ustawia bieżące zaznaczenie w polu kombi na pierwszy wiersz, który rozpoczyna się od znaków w ciągu określonym w *wartości*. W przypadku transferu z zestawu rekordów do kontrolki, jeśli pole zestaw rekordów ma wartość null, każdy wybór zostanie usunięty z pola kombi, a kontrolka edycji pola kombi jest ustawiona na wartość puste. W przypadku przeniesienia z kontroli do zestawu rekordów, Jeśli kontrolka jest pusta, pole zestaw rekordów ma wartość null, jeśli pole zezwala.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na programie DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla pól [formularzy CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) można znaleźć w artykułach [widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText](#ddx_fieldtext) , aby uzyskać przykład DDX_Field ogólny. Przykład zawiera wywołanie `DDX_FieldCBString` .

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao. h

## <a name="ddx_fieldcbstringexact"></a><a name="ddx_fieldcbstringexact"></a> DDX_FieldCBStringExact

`DDX_FieldCBStringExact`Funkcja zarządza transferem danych [CString](../../atl-mfc-shared/reference/cstringt-class.md) między kontrolką edycji kontrolki pola kombi w widoku rekordu i elementem `CString` członkowskim danych pola zestawu rekordów skojarzonego z widokiem rekordu.

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki w obiekcie [formularzy CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*wartościami*<br/>
Odwołanie do elementu członkowskiego danych pola w obiekcie skojarzonym `CRecordset` lub `CDaoRecordset` .

*pRecordset*<br/>
Wskaźnik do obiektu [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Podczas przesuwania danych z zestawu rekordów do kontrolki ta funkcja ustawia bieżące zaznaczenie w polu kombi na pierwszy wiersz, który dokładnie pasuje do ciągu określonego w *wartości*. W przypadku transferu z zestawu rekordów do kontrolki, jeśli pole zestaw rekordów ma wartość NULL, każdy zaznaczony element zostanie usunięty z pola kombi, a pole kombi jest ustawione jako puste. W przypadku transferu z kontroli do zestawu rekordów, Jeśli kontrolka jest pusta, pole zestaw rekordów jest ustawione na wartość NULL.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na programie DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla pól [formularzy CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) można znaleźć w artykułach [widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText](#ddx_fieldtext) , aby uzyskać przykład DDX_Field ogólny. Wywołania `DDX_FieldCBStringExact` byłyby podobne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao. h

## <a name="ddx_fieldcheck"></a><a name="ddx_fieldcheck"></a> DDX_FieldCheck

`DDX_FieldCheck`Funkcja zarządza przesyłaniem **`int`** danych między kontrolką pola wyboru w oknie dialogowym, widoku Formularz lub obiektem widoku formantu i **`int`** elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator zasobu kontrolki pola wyboru skojarzonej z właściwością kontrolki.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym są wymieniane dane.

*pRecordset*<br/>
Wskaźnik do obiektu [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_FieldCheck` jest wywoływana, *wartość* jest ustawiana na bieżący stan kontrolki pole wyboru lub stan kontrolki jest ustawiony na *wartość*, w zależności od kierunku transferu.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao. h

## <a name="ddx_fieldlbindex"></a><a name="ddx_fieldlbindex"></a> DDX_FieldLBIndex

`DDX_FieldLBIndex`Funkcja synchronizuje indeks wybranego elementu w kontrolce pole listy w widoku rekordu i **`int`** element członkowski danych pola zestawu rekordów skojarzonego z widokiem rekordu.

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki w obiekcie [formularzy CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*index*<br/>
Odwołanie do elementu członkowskiego danych pola w obiekcie skojarzonym `CRecordset` lub `CDaoRecordset` .

*pRecordset*<br/>
Wskaźnik do obiektu [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Podczas przesuwania danych z zestawu rekordów do kontrolki ta funkcja ustawia zaznaczenie w kontrolce na podstawie wartości określonej w *indeksie*. W przypadku transferu z zestawu rekordów do formantu, jeśli pole zestaw rekordów ma wartość null, MFC ustawi wartość indeksu na 0. W przypadku przeniesienia z kontroli do zestawu rekordów, Jeśli kontrolka jest pusta, pole zestaw rekordów jest ustawione na 0.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na programie DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla pól [formularzy CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) można znaleźć w artykułach [widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText](#ddx_fieldtext) , aby uzyskać przykład DDX_Field ogólny.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao. h

## <a name="ddx_fieldlbstring"></a><a name="ddx_fieldlbstring"></a> DDX_FieldLBString

`DDX_FieldLBString`Kopiuje bieżące zaznaczenie kontrolki pole listy w widoku rekordu do elementu członkowskiego danych pola [CString](../../atl-mfc-shared/reference/cstringt-class.md) zestawu rekordów skojarzonego z widokiem rekordu.

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki w obiekcie [formularzy CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*wartościami*<br/>
Odwołanie do elementu członkowskiego danych pola w obiekcie skojarzonym `CRecordset` lub `CDaoRecordset` .

*pRecordset*<br/>
Wskaźnik do obiektu [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

W odwrotnym kierunku ta funkcja ustawia bieżące zaznaczenie w polu listy na pierwszy wiersz zaczynający się od znaków w ciągu określonym przez *wartość*. W przypadku transferu z zestawu rekordów do kontrolki, jeśli pole zestaw rekordów ma wartość null, wszystkie zaznaczenia zostaną usunięte z pola listy. W przypadku transferu z kontroli do zestawu rekordów, Jeśli kontrolka jest pusta, pole zestaw rekordów jest ustawione na wartość null.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na programie DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla pól [formularzy CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) można znaleźć w artykułach [widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText](#ddx_fieldtext) , aby uzyskać przykład DDX_Field ogólny. Wywołania `DDX_FieldLBString` byłyby podobne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao. h

## <a name="ddx_fieldlbstringexact"></a><a name="ddx_fieldlbstringexact"></a> DDX_FieldLBStringExact

`DDX_FieldLBStringExact`Funkcja kopiuje bieżące zaznaczenie kontrolki pole listy w widoku rekordu do elementu członkowskiego danych pola [CString](../../atl-mfc-shared/reference/cstringt-class.md) zestawu rekordów skojarzonego z widokiem rekordu.

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki w obiekcie [formularzy CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*wartościami*<br/>
Odwołanie do elementu członkowskiego danych pola w obiekcie skojarzonym `CRecordset` lub `CDaoRecordset` .

*pRecordset*<br/>
Wskaźnik do obiektu [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

W odwrotnym kierunku ta funkcja ustawia bieżące zaznaczenie w polu listy na pierwszy wiersz, który dokładnie pasuje do ciągu określonego w *wartości*. W przypadku transferu z zestawu rekordów do kontrolki, jeśli pole zestaw rekordów ma wartość null, wszystkie zaznaczenia zostaną usunięte z pola listy. W przypadku transferu z kontroli do zestawu rekordów, Jeśli kontrolka jest pusta, pole zestaw rekordów jest ustawione na wartość null.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na programie DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla pól [formularzy CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) można znaleźć w artykułach [widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText](#ddx_fieldtext) , aby uzyskać przykład DDX_Field ogólny. Wywołania `DDX_FieldLBStringExact` byłyby podobne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao. h

## <a name="ddx_fieldradio"></a><a name="ddx_fieldradio"></a> DDX_FieldRadio

`DDX_FieldRadio`Funkcja kojarzy **`int`** zmienną członkowską od zera zestawu rekordów widoku rekordu z aktualnie wybranym przyciskiem radiowym w grupie przycisków radiowych w widoku rekordu.

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator pierwszego w grupie (z stylem WS_GROUP) sąsiadujących kontrolek przycisków radiowych w obiekcie [formularzy CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*wartościami*<br/>
Odwołanie do elementu członkowskiego danych pola w obiekcie skojarzonym `CRecordset` lub `CDaoRecordset` .

*pRecordset*<br/>
Wskaźnik do obiektu [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Podczas przenoszenia z pola zestaw rekordów do widoku ta funkcja włącza *n-ty* przycisk radiowy (liczony od zera) i wyłącza pozostałe przyciski. W odwrotnym kierunku ta funkcja ustawia pole zestaw rekordów na numer porządkowy przycisku radiowego, który jest obecnie włączony (zaznaczone). W przypadku transferu z zestawu rekordów do kontrolki, jeśli pole zestaw rekordów ma wartość null, nie jest wybrany żaden przycisk. W przypadku transferu z kontroli do zestawu rekordów, jeśli żadna kontrola nie jest zaznaczona, pole zestaw rekordów jest ustawione na wartość null, jeśli pole to zezwoli.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na programie DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla pól [formularzy CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) można znaleźć w artykułach [widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText](#ddx_fieldtext) , aby uzyskać przykład DDX_Field ogólny. Wywołania `DDX_FieldRadio` byłyby podobne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao. h

## <a name="ddx_fieldscroll"></a><a name="ddx_fieldscroll"></a> DDX_FieldScroll

`DDX_FieldScroll`Funkcja synchronizuje położenie przewijania kontrolki pasek przewijania w widoku rekordu i **`int`** element członkowski danych pola zestawu rekordów skojarzonego z widokiem rekordu (lub z dowolną zmienną całkowitą wybraną do zmapowania).

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator pierwszego w grupie (z stylem WS_GROUP) sąsiadujących kontrolek przycisków radiowych w obiekcie [formularzy CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*wartościami*<br/>
Odwołanie do elementu członkowskiego danych pola w obiekcie skojarzonym `CRecordset` lub `CDaoRecordset` .

*pRecordset*<br/>
Wskaźnik do obiektu [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Podczas przesuwania danych z zestawu rekordów do kontrolki ta funkcja ustawia położenie przewijania kontrolki paska przewijania na wartość określoną w polu *wartość*. W przypadku transferu z zestawu rekordów do kontrolki, jeśli pole zestaw rekordów ma wartość null, kontrolka paska przewijania jest ustawiona na 0. W przypadku transferu z kontroli do zestawu rekordów, Jeśli kontrolka jest pusta, wartość pola zestaw rekordów jest równa 0.

Użyj pierwszej wersji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiej wersji, jeśli pracujesz z klasami opartymi na programie DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla pól [formularzy CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) można znaleźć w artykułach [widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText](#ddx_fieldtext) , aby uzyskać przykład DDX_Field ogólny. Wywołania `DDX_FieldScroll` byłyby podobne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao. h

## <a name="ddx_fieldslider"></a><a name="ddx_fieldslider"></a> DDX_FieldSlider

`DDX_FieldSlider`Funkcja synchronizuje położenie kciuka kontrolki suwaka w widoku rekordu i **`int`** element członkowski danych pola zestawu rekordów skojarzonego z widokiem rekordu (lub z dowolną zmienną całkowitą wybraną do mapowania).

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator zasobu kontrolki suwaka.

*wartościami*<br/>
Odwołanie do wartości, która ma zostać nadana wymianie. Ten parametr zawiera lub zostanie użyty do ustawienia bieżącego położenia kciuka kontrolki suwaka.

*pRecordset*<br/>
Wskaźnik do skojarzonego `CRecordset` lub obiektu, `CDaoRecordset` z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy przenosisz dane z zestawu rekordów do suwaka, ta funkcja ustawia pozycję suwaka na wartość określoną w polu *wartość*. W przypadku przeniesienia z zestawu rekordów do kontrolki, jeśli pole zestaw rekordów ma wartość null, pozycja kontrolki suwaka jest ustawiona na 0. W przypadku przeniesienia z formantu do zestawu rekordów, Jeśli kontrolka jest pusta, wartość pola zestaw rekordów jest równa 0.

`DDX_FieldSlider` nie wymienia informacji o zakresie z kontrolkami suwaka, które mogą ustawić zakres, a nie po prostu pozycji.

Użyj pierwszego przesłonięcia funkcji, jeśli pracujesz z klasami opartymi na ODBC. Użyj drugiego przesłonięcia przy użyciu klas opartych na programie DAO.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../dialog-data-exchange-and-validation.md). Aby uzyskać przykłady i więcej informacji na temat DDX dla `CRecordView` i `CDaoRecordView` pól, zobacz [widoki rekordów](../../data/record-views-mfc-data-access.md). Aby uzyskać informacje o kontrolkach suwaka, zobacz [using korzystanie CSliderCtrl](../using-csliderctrl.md).

### <a name="example"></a>Przykład

Zobacz [DDX_FieldText](#ddx_fieldtext) , aby uzyskać przykład DDX_Field ogólny. Wywołania `DDX_FieldSlider` byłyby podobne.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="ddx_fieldtext"></a><a name="ddx_fieldtext"></a> DDX_FieldText

`DDX_FieldText`Funkcja zarządza transferem danych, **`int`** **`short`** ,, **`long`** typu DWORD, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **`float`** , **`double`** , wartości **bool**lub **Byte** między kontrolką pola edycji i elementami członkowskimi danych pola zestawu rekordów.

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki w obiekcie [formularzy CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*wartościami*<br/>
Odwołanie do elementu członkowskiego danych pola w obiekcie skojarzonym `CRecordset` lub `CDaoRecordset` . Typ danych wartości zależy od tego, które z przeciążonych wersji są `DDX_FieldText` używane.

*pRecordset*<br/>
Wskaźnik do obiektu [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , z którym są wymieniane dane. Ten wskaźnik umożliwia `DDX_FieldText` wykrywanie i ustawianie wartości null.

### <a name="remarks"></a>Uwagi

Dla obiektów [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) `DDX_FieldText` zarządza również transferem wartości [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)i [COleCurrency](../../mfc/reference/colecurrency-class.md) . Pusta kontrolka pole edycji wskazuje wartość null. W przypadku transferu z zestawu rekordów do kontrolki, jeśli pole zestaw rekordów ma wartość null, pole edycji ma wartość puste. W przypadku transferu z kontroli do zestawu rekordów, Jeśli kontrolka jest pusta, pole zestaw rekordów jest ustawione na wartość null.

Jeśli pracujesz z klasami opartymi na ODBC, użyj wersji z parametrami [CRecordset](../../mfc/reference/crecordset-class.md) . Jeśli pracujesz z klasami opartymi na programie DAO, użyj wersji z parametrami [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) .

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla pól [formularzy CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) można znaleźć w artykułach [widoki rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Następująca `DoDataExchange` Funkcja dla elementu [formularzy CRecordView](../../mfc/reference/crecordview-class.md) zawiera `DDX_FieldText` wywołania funkcji dla trzech typów danych: `IDC_COURSELIST` jest polem kombi; pozostałe dwie kontrolki to pola edycji. W przypadku programowania DAO parametr *m_pSet* jest wskaźnikiem do elementu [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](mfc-macros-and-globals.md)
