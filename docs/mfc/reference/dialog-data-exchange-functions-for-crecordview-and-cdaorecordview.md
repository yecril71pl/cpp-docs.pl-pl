---
title: Funkcje wymiany danych w oknie dialogowym dla formularzy CRecordView i CDaoRecordView | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 295e19d875585e0ea166dfce552866b8c1fc81b7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392273"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Funkcje wymiany danych w oknie dialogowym dla formularzy CRecordView i CDaoRecordView

W tym temacie wymieniono funkcje ddx_field — umożliwia wymianę danych między [CRecordset](../../mfc/reference/crecordset-class.md) i [CRecordView](../../mfc/reference/crecordview-class.md) formularza lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) i [ CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) formularza.

> [!NOTE]
>  Ddx_field — funkcje są podobne funkcje DDX, w tym, że ich wymiany danych z kontrolkami w formularzu. Jednak w przeciwieństwie do DDX, wymieniają danych z polami obiekt skojarzony zestaw rekordów tego widoku, a nie z polami samego widoku rekordu. Aby uzyskać więcej informacji, patrz klasy `CRecordView` i `CDaoRecordView`.

### <a name="ddxfield-functions"></a>Ddx_field — funkcje

|||
|-|-|
|[Ddx_fieldcbindex —](#ddx_fieldcbindex)|Transfer danych liczb całkowitych między element członkowski danych pola zestawu rekordów i indeks bieżącego zaznaczenia w polu kombi w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|
|[Ddx_fieldcbstring —](#ddx_fieldcbstring)|Transfery `CString` danych między element członkowski danych pola zestawu rekordów i kontrolki edycji kombi pole w `CRecordView` lub `CDaoRecordView`. Podczas przenoszenia danych w zestawie do kontrolki, ta funkcja wybiera element w polu kombi, które zaczyna się od znaków w ciągu określonej.|
|[Ddx_fieldcbstringexact —](#ddx_fieldcbstringexact)|Transfery `CString` danych między element członkowski danych pola zestawu rekordów i kontrolki edycji kombi pole w `CRecordView` lub `CDaoRecordView`. Podczas przenoszenia danych w zestawie do kontrolki, ta funkcja wybiera element w polu kombi, który dokładnie pasuje do określonego ciągu.|
|[Ddx_fieldcheck —](#ddx_fieldcheck)|Transfer danych logicznych między element członkowski danych pola zestawu rekordów i pola wyboru w `CRecordView` lub `CDaoRecordView`.|
|[Ddx_fieldlbindex —](#ddx_fieldlbindex)|Transfer danych liczb całkowitych między element członkowski danych pola zestawu rekordów i indeks bieżącego zaznaczenia w polu listy, w `CRecordView` lub `CDaoRecordView`.|
|[Ddx_fieldlbstring —](#ddx_fieldlbstring)|Zarządza transferem [CString](../../atl-mfc-shared/reference/cstringt-class.md) danych pomiędzy kontrolce pola listy i elementy członkowskie danych pola zestawu rekordów. Podczas przenoszenia danych w zestawie do kontrolki, ta funkcja wybiera element w polu listy, który zaczyna się od znaków w ciągu określonej.|
|[Ddx_fieldlbstringexact —](#ddx_fieldlbstringexact)|Zarządza transferem `CString` danych pomiędzy kontrolce pola listy i elementy członkowskie danych pola zestawu rekordów. Podczas przenoszenia danych w zestawie do kontrolki, ta funkcja wybiera pierwszy element, który dokładnie pasuje do określonego ciągu.|
|[Ddx_fieldradio —](#ddx_fieldradio)|Transfer danych liczb całkowitych między element członkowski danych pola zestawu rekordów i Grupa przycisków radiowych w `CRecordView` lub `CDaoRecordView`.|
|[Ddx_fieldscroll —](#ddx_fieldscroll)|Ustawia lub pobiera jego położenie przewijania pasek przewijania w `CRecordView` lub `CDaoRecordView`. Wywoływanie z Twojej [dofieldexchange —](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) funkcji.|
|[Ddx_fieldslider —](#ddx_fieldslider)|Synchronizuje pozycji przycisku przewijania kontrolki suwaka w widoku rekordu i `int` pole składowej danych zestawu rekordów. |
|[Ddx_fieldtext —](#ddx_fieldtext)|Przeciążone wersje są dostępne do przesyłania `int`, **UINT**, **długie**, `DWORD`, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float** , **double**, **krótki**, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), i [COleCurrency](../../mfc/reference/colecurrency-class.md) danych między element członkowski danych pola zestawu rekordów i edytowanie pole w `CRecordView` lub `CDaoRecordView`.|

##  <a name="ddx_fieldcbindex"></a>  Ddx_fieldcbindex —

`DDX_FieldCBIndex` Funkcja synchronizuje indeks zaznaczonego elementu w kontrolce pola listy z kontrolki pola kombi w widoku rekordu i `int` pole składowej danych zestawie rekordów skojarzonych z widokiem rekordów.

```
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
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*index*<br/>
Odwołanie do elementu członkowskiego danych pola w skojarzonej `CRecordset` lub `CDaoRecordset` obiektu.

*pRecordset*<br/>
Wskaźnik do [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.

### <a name="remarks"></a>Uwagi

Podczas przenoszenia danych w zestawie do formantu, funkcja ta ustawia zaznaczenie w kontrolce, w oparciu o wartość określoną w *indeksu*. Przesunięcia w zestawie do formantu jeśli zestaw rekordów pole ma wartość Null, MFC ustawia wartość indeksu 0. Na transfer z kontrolki do zestawu rekordów Jeśli formant jest pusty lub nie wybrano elementu, pole zestawu rekordów jest równa 0.

Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Jeśli pracujesz z klasy oparte na DAO, należy użyć drugiej wersji.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i dowiedzieć się więcej o DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ogólne funkcje DDX_Field. Przykładem może być podobne do `DDX_FieldCBIndex`.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

##  <a name="ddx_fieldcbstring"></a>  Ddx_fieldcbstring —

`DDX_FieldCBString` Funkcja zarządza transferem [CString](../../atl-mfc-shared/reference/cstringt-class.md) danych między kontrolki edycji z kontrolki pola kombi w widoku rekordu a `CString` pole składowej danych zestawie rekordów skojarzonych z widokiem rekordów.

```
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
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*value*<br/>
Odwołanie do elementu członkowskiego danych pola w skojarzonej `CRecordset` lub `CDaoRecordset` obiektu.

*pRecordset*<br/>
Wskaźnik do [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.

### <a name="remarks"></a>Uwagi

Podczas przenoszenia danych w zestawie do formantu, funkcja ta ustawia bieżące zaznaczenie w polu kombi na pierwszym wierszem, który rozpoczyna się od znaków w ciągu określonego w *wartość*. Przesunięcia w zestawie do formantu, jeśli zestaw rekordów pole ma wartość Null, dokonaj wyboru zostanie usunięte z pola kombi i kontrolki edycji pola kombi jest ustawiony na pusty. Na transfer z kontrolki do zestawu rekordów Jeśli kontrolka jest pusta, pole zestawu rekordów jest równa Null pozwala na pole.

Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Jeśli pracujesz z klasy oparte na DAO, należy użyć drugiej wersji.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i dowiedzieć się więcej o DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ogólne funkcje DDX_Field. Przykład zawiera wywołanie `DDX_FieldCBString`.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

## <a name="ddx_fieldcbstringexact"></a>  Ddx_fieldcbstringexact —

`DDX_FieldCBStringExact` Funkcja zarządza transferem [CString](../../atl-mfc-shared/reference/cstringt-class.md) danych między kontrolki edycji z kontrolki pola kombi w widoku rekordu a `CString` pole składowej danych zestawie rekordów skojarzonych z widokiem rekordów.

```
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
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*value*<br/>
Odwołanie do elementu członkowskiego danych pola w skojarzonej `CRecordset` lub `CDaoRecordset` obiektu.

*pRecordset*<br/>
Wskaźnik do [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.

### <a name="remarks"></a>Uwagi

Podczas przenoszenia danych w zestawie do formantu, funkcja ta ustawia bieżące zaznaczenie w polu kombi do pierwszego wiersza, który dokładnie pasuje do ciągu określonego w *wartość*. Przesunięcia w zestawie do formantu, jeśli zestaw rekordów pole ma wartość NULL, dokonaj wyboru zostanie usunięte z pola kombi i pole edycji pola kombi jest ustawiony na pusty. Na transfer z kontrolki do zestawu rekordów Jeśli kontrolka jest pusta, pole zestawu rekordów jest równa NULL.

Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Jeśli pracujesz z klasy oparte na DAO, należy użyć drugiej wersji.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i dowiedzieć się więcej o DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ogólne funkcje DDX_Field. Wywołania `DDX_FieldCBStringExact` mogą być podobne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

##  <a name="ddx_fieldcheck"></a>  Ddx_fieldcheck —

`DDX_FieldCheck` Funkcja zarządza transferem **int** danych pomiędzy kontrolce pola wyboru w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i **int** element członkowski danych okno dialogowe, widok formularza lub formantu Obiekt widoku.

```
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
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator zasobu w kontrolce pola wyboru skojarzone z właściwością kontrolki.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu obiekt widoku wymiany danych.

*pRecordset*<br/>
Wskaźnik do [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.

### <a name="remarks"></a>Uwagi

Gdy `DDX_FieldCheck` jest wywoływana, *wartość* jest ustawiona na bieżący stan formant pola wyboru lub stan kontrolki jest ustawiony na *wartość*, w zależności od kierunku transferu.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

##  <a name="ddx_fieldlbindex"></a>  Ddx_fieldlbindex —

`DDX_FieldLBIndex` Funkcja synchronizuje indeks zaznaczonego elementu w kontrolce pola listy, w widoku rekordu i **int** pole składowej danych zestawie rekordów skojarzonych z widokiem rekordów.

```
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
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*index*<br/>
Odwołanie do elementu członkowskiego danych pola w skojarzonej `CRecordset` lub `CDaoRecordset` obiektu.

*pRecordset*<br/>
Wskaźnik do [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.

### <a name="remarks"></a>Uwagi

Podczas przenoszenia danych w zestawie do formantu, funkcja ta ustawia zaznaczenie w kontrolce, w oparciu o wartość określoną w *indeksu*. Przesunięcia w zestawie do formantu jeśli zestaw rekordów pole ma wartość Null, MFC ustawia wartość indeksu 0. Na transfer z kontrolki do zestawu rekordów Jeśli kontrolka jest pusta, pole zestawu rekordów jest równa 0.

Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Jeśli pracujesz z klasy oparte na DAO, należy użyć drugiej wersji.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i dowiedzieć się więcej o DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ogólne funkcje DDX_Field.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

##  <a name="ddx_fieldlbstring"></a>  Ddx_fieldlbstring —

`DDX_FieldLBString` Kopiuje aktualnie wybrane pole listy w widoku rekordu do [CString](../../atl-mfc-shared/reference/cstringt-class.md) pole składowej danych zestawie rekordów skojarzonych z widokiem rekordów.

```
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
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*value*<br/>
Odwołanie do elementu członkowskiego danych pola w skojarzonej `CRecordset` lub `CDaoRecordset` obiektu.

*pRecordset*<br/>
Wskaźnik do [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.

### <a name="remarks"></a>Uwagi

W odwrotnym kierunku, funkcja ta ustawia bieżące zaznaczenie w polu listy, aby pierwszym wierszem, który rozpoczyna się od znaków w ciągu określonej przez *wartość*. Na transfer z tego zestawu rekordów do formantu Jeśli pole zestawu rekordów ma wartość Null, dokonaj wyboru zostanie usunięte z listy rozwijanej. Na transfer z kontrolki do zestawu rekordów Jeśli kontrolka jest pusta, pole zestawu rekordów jest równa Null.

Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Jeśli pracujesz z klasy oparte na DAO, należy użyć drugiej wersji.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i dowiedzieć się więcej o DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ogólne funkcje DDX_Field. Wywołania `DDX_FieldLBString` mogą być podobne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

##  <a name="ddx_fieldlbstringexact"></a>  Ddx_fieldlbstringexact —

`DDX_FieldLBStringExact` Funkcja kopiuje aktualnie wybrane pole listy w widoku rekordów do [CString](../../atl-mfc-shared/reference/cstringt-class.md) pole składowej danych zestawie rekordów skojarzonych z widokiem rekordów.

```
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
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*value*<br/>
Odwołanie do elementu członkowskiego danych pola w skojarzonej `CRecordset` lub `CDaoRecordset` obiektu.

*pRecordset*<br/>
Wskaźnik do [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.

### <a name="remarks"></a>Uwagi

W odwrotnym kierunku, funkcja ta ustawia bieżące zaznaczenie w polu listy, aby pierwszy wiersz, który dokładnie pasuje do ciągu określonego w *wartość*. Na transfer z tego zestawu rekordów do formantu Jeśli pole zestawu rekordów ma wartość Null, dokonaj wyboru zostanie usunięte z listy rozwijanej. Na transfer z kontrolki do zestawu rekordów Jeśli kontrolka jest pusta, pole zestawu rekordów jest równa Null.

Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Jeśli pracujesz z klasy oparte na DAO, należy użyć drugiej wersji.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i dowiedzieć się więcej o DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ogólne funkcje DDX_Field. Wywołania `DDX_FieldLBStringExact` mogą być podobne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

##  <a name="ddx_fieldradio"></a>  Ddx_fieldradio —

`DDX_FieldRadio` Funkcja kojarzy liczony od zera **int** zmiennej składowej rekordów z widoków rekordów z aktualnie wybranego przycisku radiowego w grupie przycisków radiowych w widoku rekordu.

```
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
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator pierwszego w grupie (ze stylem WS_GROUP) kontrolek przycisków radiowych sąsiadująco w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*value*<br/>
Odwołanie do elementu członkowskiego danych pola w skojarzonej `CRecordset` lub `CDaoRecordset` obiektu.

*pRecordset*<br/>
Wskaźnik do [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.

### <a name="remarks"></a>Uwagi

Podczas przenoszenia z pól rekordów do widoku, ta funkcja powoduje włączenie *n-ty* przycisku radiowego (liczony od zera) i wyłącza inne przyciski. W odwrotnym kierunku ta funkcja ustawia pole zestawu rekordów na liczbę porządkową przycisku radiowego, która znajduje się obecnie na (zaznaczony). Przesunięcia w zestawie do formantu, jeśli zestaw rekordów pole ma wartość Null, nie przycisk jest zaznaczony. Na transfer z kontrolki do zestawu rekordów zaznaczenie nie może kontrolować pole zestawu rekordów jest równa Null pozwala na pole.

Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Jeśli pracujesz z klasy oparte na DAO, należy użyć drugiej wersji.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i dowiedzieć się więcej o DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ogólne funkcje DDX_Field. Wywołania `DDX_FieldRadio` mogą być podobne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

##  <a name="ddx_fieldscroll"></a>  Ddx_fieldscroll —

`DDX_FieldScroll` Funkcja synchronizuje jego położenie przewijania pasek przewijania w widoku rekordu i **int** pole składowej danych zestawie rekordów skojarzonych z widoków rekordów (lub ze zmienną liczbą całkowitą, niezależnie od chcesz zamapować na) .

```
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
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator pierwszego w grupie (ze stylem WS_GROUP) kontrolek przycisków radiowych sąsiadująco w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*value*<br/>
Odwołanie do elementu członkowskiego danych pola w skojarzonej `CRecordset` lub `CDaoRecordset` obiektu.

*pRecordset*<br/>
Wskaźnik do [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.

### <a name="remarks"></a>Uwagi

Podczas przenoszenia danych w zestawie do formantu, funkcja ta Ustawia położenie przewijania formantu paska przewijania wartość określoną w *wartość*. Przesunięcia w zestawie do formantu jeśli zestaw rekordów pole ma wartość Null, pasek przewijania jest równa 0. Na transfer z kontrolki do zestawu rekordów Jeśli kontrolka jest pusta, wartość pola zestawu rekordów jest 0.

Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Jeśli pracujesz z klasy oparte na DAO, należy użyć drugiej wersji.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i dowiedzieć się więcej o DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ogólne funkcje DDX_Field. Wywołania `DDX_FieldScroll` mogą być podobne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

  ## <a name="nameddxfieldslidera--ddxfieldslider"></a>Nazwa = "ddx_fieldslider —" ></a> ddx_fieldslider —
`DDX_FieldSlider` Funkcja synchronizuje pozycji przycisku przewijania kontrolki suwaka w widoku rekordu i **int** pole składowej danych zestawie rekordów skojarzonych z widoków rekordów (lub ze zmienną liczbą całkowitą, niezależnie od chcesz zamapować na).

### <a name="syntax"></a>Składnia

  ```
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
Wskaźnik do [CDataExchange](cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator zasobu kontrolki suwaka.

*value*<br/>
Odwołanie do wartości wymieniane. Ten parametr zawiera lub będzie używany do ustawiania kontrolki slider bieżącej pozycji przycisku przewijania.

*pRecordset*<br/>
Wskaźnik do powiązanych `CRecordset` lub `CDaoRecordset` obiektu wymiany danych.

### <a name="remarks"></a>Uwagi

Podczas przenoszenia danych w zestawie suwaka, funkcja ta Ustawia położenie suwaka na wartość określoną w *wartość*. Przesunięcia w zestawie do formantu jeśli zestaw rekordów pole ma wartość Null, położenie kontrolki suwak jest równa 0. Na transfer z kontrolki do zestawu rekordów Jeśli kontrolka jest pusta, wartość pola zestawu rekordów jest 0.

`DDX_FieldSlider` nie wymiany informacji o zakresie z kontrolkami suwaka może ustawić zakresu, a nie po prostu stanie.

Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszego przesłonięcie funkcji. Zastąpienie drugiego za pomocą klasy oparte na DAO.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../dialog-data-exchange-and-validation.md). Przykłady i dowiedzieć się więcej o DDX dla `CRecordView` i `CDaoRecordView` pól, zobacz [widoków rekordów](../../data/record-views-mfc-data-access.md). Aby uzyskać informacji na temat kontrolki suwaka, zobacz [korzystanie z CSliderCtrl](../using-csliderctrl.md).

### <a name="example"></a>Przykład

Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ogólne funkcje DDX_Field. Wywołania `DDX_FieldSlider` mogą być podobne.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

### <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](mfc-macros-and-globals.md)

##  <a name="ddx_fieldtext"></a>  Ddx_fieldtext —

`DDX_FieldText` Funkcja zarządza transferem **int**, **krótki**, **długie**, DWORD, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **double**, **BOOL**, lub **BAJTÓW** danych między formant pola edycji i elementy członkowskie danych pola zestawu rekordów.

```
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
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.

*value*<br/>
Odwołanie do elementu członkowskiego danych pola w skojarzonej `CRecordset` lub `CDaoRecordset` obiektu. Typ danych wartości zależy, która przeciążone wersje `DDX_FieldText` używasz.

*pRecordset*<br/>
Wskaźnik do [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych. Włącza ten wskaźnik `DDX_FieldText` do wykrywania i ustawiania wartości Null.

### <a name="remarks"></a>Uwagi

Aby uzyskać [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektów `DDX_FieldText` zarządza także przesyłania [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), i [COleCurrency](../../mfc/reference/colecurrency-class.md) wartości. Formant pola edycji pusty wskazuje wartość Null. Przesunięcia w zestawie do formantu, jeśli zestaw rekordów pole ma wartość Null, pole edycji jest ustawiony na pusty. Na transfer z kontrolki do zestawu rekordów Jeśli kontrolka jest pusta, pole zestawu rekordów jest równa Null.

Użyj wersji za pomocą [CRecordset](../../mfc/reference/crecordset-class.md) parametrów, jeśli pracujesz z klasy oparte na ODBC. Użyj wersji za pomocą [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) parametrów, jeśli pracujesz z klasy oparte na DAO.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i dowiedzieć się więcej o DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Przykład

Następujące `DoDataExchange` działać w ramach [CRecordView](../../mfc/reference/crecordview-class.md) zawiera `DDX_FieldText` funkcja wywołuje dla typów danych trzy: `IDC_COURSELIST` ma postać pola kombi; inne formanty są pola tekstowe. W programowaniu DAO *m_pSet* parametru jest wskaźnikiem do [CRecordset](../../mfc/reference/crecordset-class.md) lub [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]


### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

## <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
