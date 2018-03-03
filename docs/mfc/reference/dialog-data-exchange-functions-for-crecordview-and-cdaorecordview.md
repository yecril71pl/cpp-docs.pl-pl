---
title: Funkcje wymiany danych w oknie dialogowym dla formularzy CRecordView i CDaoRecordView | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f58b7ba7ae51c4db065cd7b30cc233128f7b7c68
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Funkcje wymiany danych w oknie dialogowym dla formularzy CRecordView i CDaoRecordView
W tym temacie wymieniono ddx_field — funkcje używane do wymiany danych między [crecordset —](../../mfc/reference/crecordset-class.md) i [CRecordView](../../mfc/reference/crecordview-class.md) formularza lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) i [ Cdaorecordview —](../../mfc/reference/cdaorecordview-class.md) formularza.  
  
> [!NOTE]
>  Ddx_field — funkcje są podobne funkcje DDX, w tym wymieniają danych za pomocą formantów w formularzu. Jednak w przeciwieństwie do DDX, ich wymiany danych z polami widoku rekordów skojarzony obiekt, a nie z polami samego widoku rekordu. Aby uzyskać więcej informacji, zobacz klasy `CRecordView` i `CDaoRecordView`.  
  
### <a name="ddxfield-functions"></a>Ddx_field — funkcje  
  
|||  
|-|-|  
|[Ddx_fieldcbindex —](#ddx_fieldcbindex)|Transfer danych liczb całkowitych między elementem członkowskim danych pola rekordów i indeks bieżącego zaznaczenia w polu kombi w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|  
|[Ddx_fieldcbstring —](#ddx_fieldcbstring)|Transfery `CString` danych między elementem członkowskim danych pola rekordów i kontrolki edycji kombi pole `CRecordView` lub `CDaoRecordView`. Podczas przenoszenia danych w zestawie do formantu, funkcja wybiera element w polu kombi, który rozpoczyna się od znaków w ciągu określonej.|  
|[Ddx_fieldcbstringexact —](#ddx_fieldcbstringexact)|Transfery `CString` danych między elementem członkowskim danych pola rekordów i kontrolki edycji kombi pole `CRecordView` lub `CDaoRecordView`. Podczas przenoszenia danych w zestawie do formantu, funkcja wybiera element w polu kombi, która dokładnie odpowiada określonego ciągu.|  
|[Ddx_fieldcheck —](#ddx_fieldcheck)|Transfery danych logicznych między elementem członkowskim danych pola rekordów i pola wyboru w `CRecordView` lub `CDaoRecordView`.|  
|[Ddx_fieldlbindex —](#ddx_fieldlbindex)|Transfer danych liczb całkowitych między elementem członkowskim danych pola rekordów i indeks bieżącego zaznaczenia w polu listy w `CRecordView` lub `CDaoRecordView`.|  
|[Ddx_fieldlbstring —](#ddx_fieldlbstring)|Zarządza transferem [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) danych między kontrolkę pola listy i elementy członkowskie danych pola zestawu rekordów. Podczas przenoszenia danych w zestawie do formantu, funkcja wybiera element w polu listy, który rozpoczyna się od znaków w ciągu określonej.|  
|[Ddx_fieldlbstringexact —](#ddx_fieldlbstringexact)|Zarządza transferem `CString` danych między kontrolkę pola listy i elementy członkowskie danych pola zestawu rekordów. Podczas przenoszenia danych w zestawie do formantu, funkcja wybiera pierwszy element, która dokładnie odpowiada określonego ciągu.|  
|[Ddx_fieldradio —](#ddx_fieldradio)|Transfer danych liczb całkowitych między elementem członkowskim danych pola rekordów i Grupa przycisków radiowych w `CRecordView` lub `CDaoRecordView`.|  
|[Ddx_fieldscroll —](#ddx_fieldscroll)|Ustawia lub pobiera jego położenie przewijania formantu paska przewijania w `CRecordView` lub `CDaoRecordView`. Wywoływanie z Twojej [DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) funkcji.|  
|[Ddx_fieldslider —](#ddx_fieldslider)|Synchronizuje pozycji przycisku przewijania suwaka w widoku rekordu i `int` pola danych członkiem zestawu rekordów. |
|[Ddx_fieldtext —](#ddx_fieldtext)|Przeciążone wersje są dostępne do przesyłania `int`, **UINT**, **długi**, `DWORD`, [cstring —](../../atl-mfc-shared/reference/cstringt-class.md), **float** , **podwójne**, **krótki**, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), i [COleCurrency](../../mfc/reference/colecurrency-class.md) danych między elementem członkowskim danych pola rekordów i edytowanie pole `CRecordView` lub `CDaoRecordView`.|  
  
##  <a name="ddx_fieldcbindex"></a>Ddx_fieldcbindex —  
 `DDX_FieldCBIndex` Funkcja synchronizuje indeks wybranego elementu w formancie pola listy z kontrolki pola kombi w widoku rekordu i `int` pola danych członkiem zestawu rekordów skojarzonego z widokiem rekordu.  
  
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
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator formantu w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.  
  
 *Indeks*  
 Odwołanie do elementu członkowskiego danych pola w skojarzonym `CRecordset` lub `CDaoRecordset` obiektu.  
  
 `pRecordset`  
 Wskaźnik do [crecordset —](../../mfc/reference/crecordset-class.md) lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Podczas przenoszenia danych w zestawie do formantu, ta funkcja ustawia zaznaczenie w formancie na podstawie wartości określone w *indeksu*. Przesunięcia w zestawie do formantu Jeśli pole rekordów ma wartość Null, MFC ustawia wartość indeksu na 0. Na transfer z formantu do zestawu rekordów Jeśli formant jest pusty lub nie wybrano elementów, w polu rekordów jest równa 0.  
  
 Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Druga wersja należy użyć, jeśli pracujesz z klasy oparte na DAO.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ddx_field — ogólne. Przykładem może być podobne do `DDX_FieldCBIndex`.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  

##  <a name="ddx_fieldcbstring"></a>Ddx_fieldcbstring —  
 `DDX_FieldCBString` Funkcji zarządzania transferem [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) danych między kontrolki edycji kontrolki pola kombi w widoku rekordu a `CString` pola danych członkiem zestawu rekordów skojarzonego z widokiem rekordu.  
  
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
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator formantu w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.  
  
 *value*  
 Odwołanie do elementu członkowskiego danych pola w skojarzonym `CRecordset` lub `CDaoRecordset` obiektu.  
  
 `pRecordset`  
 Wskaźnik do [crecordset —](../../mfc/reference/crecordset-class.md) lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Podczas przenoszenia danych w zestawie do formantu, ta funkcja ustawia bieżące zaznaczenie w polu kombi pierwszy wiersz, który rozpoczyna się od znaków w ciągu określonego w *wartość*. Na transfer z tego zestawu rekordów do formantu, jeśli pole rekordów ma wartość Null, dokonaj wyboru zostanie usunięte z pola kombi i formancie edycyjnym pola kombi ma wartość pustą. Na transfer z formantu do zestawu rekordów Jeśli formant jest pusty, pole rekordów ma ustawioną wartość Null pozwala na pole.  
  
 Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Druga wersja należy użyć, jeśli pracujesz z klasy oparte na DAO.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ddx_field — ogólne. Przykład zawiera wywołanie `DDX_FieldCBString`.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdao.h  
  
## <a name="ddx_fieldcbstringexact"></a>Ddx_fieldcbstringexact —  
 `DDX_FieldCBStringExact` Funkcji zarządzania transferem [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) danych między kontrolki edycji kontrolki pola kombi w widoku rekordu a `CString` pola danych członkiem zestawu rekordów skojarzonego z widokiem rekordu.  
  
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
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator formantu w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.  
  
 *value*  
 Odwołanie do elementu członkowskiego danych pola w skojarzonym `CRecordset` lub `CDaoRecordset` obiektu.  
  
 `pRecordset`  
 Wskaźnik do [crecordset —](../../mfc/reference/crecordset-class.md) lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Podczas przenoszenia danych w zestawie do formantu, ta funkcja ustawia bieżące zaznaczenie w polu kombi do pierwszego wiersza, która dokładnie odpowiada określonym w ciągu *wartość*. Na transfer z tego zestawu rekordów do formantu, jeśli pole rekordów ma wartość NULL, dokonaj wyboru zostanie usunięte z pola kombi i edycji pole kombi ma wartość pustą. Na transfer z formantu do zestawu rekordów Jeśli formant jest pusta, pole rekordów ma ustawioną wartość NULL.  
  
 Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Druga wersja należy użyć, jeśli pracujesz z klasy oparte na DAO.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ddx_field — ogólne. Wywołuje się `DDX_FieldCBStringExact` mogą być podobne.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdao.h  
  
##  <a name="ddx_fieldcheck"></a>Ddx_fieldcheck —  
 `DDX_FieldCheck` Funkcji zarządzania transferem `int` tworzą dane między kontrolkę pola wyboru w oknie dialogowym, widoku lub formantu widoku obiektu i `int` element członkowski danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
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
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator zasobu kontrolkę pola wyboru skojarzone z właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant widoku obiektu wymiany danych.  
  
 `pRecordset`  
 Wskaźnik do [crecordset —](../../mfc/reference/crecordset-class.md) lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `DDX_FieldCheck` jest wywoływana, *wartość* ustawiono bieżący stan kontrolkę pola wyboru lub stan formantu ma wartość *wartość*w zależności od kierunku transferu.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdao.h  
  
##  <a name="ddx_fieldlbindex"></a>Ddx_fieldlbindex —  
 `DDX_FieldLBIndex` Funkcja synchronizuje indeks wybranego elementu w formancie pola listy, w widoku rekordu i `int` pola danych członkiem zestawu rekordów skojarzonego z widokiem rekordu.  
  
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
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator formantu w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.  
  
 *Indeks*  
 Odwołanie do elementu członkowskiego danych pola w skojarzonym `CRecordset` lub `CDaoRecordset` obiektu.  
  
 `pRecordset`  
 Wskaźnik do [crecordset —](../../mfc/reference/crecordset-class.md) lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Podczas przenoszenia danych w zestawie do formantu, ta funkcja ustawia zaznaczenie w formancie na podstawie wartości określone w *indeksu*. Przesunięcia w zestawie do formantu Jeśli pole rekordów ma wartość Null, MFC ustawia wartość indeksu na 0. Na transfer z formantu do zestawu rekordów Jeśli formant jest pusta, w polu rekordów jest równa 0.  
  
 Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Druga wersja należy użyć, jeśli pracujesz z klasy oparte na DAO.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ddx_field — ogólne.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdao.h  
  
##  <a name="ddx_fieldlbstring"></a>Ddx_fieldlbstring —  
 `DDX_FieldLBString` Kopiuje aktualnie zaznaczone pole listy w widoku rekordów do [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) pola danych członkiem zestawu rekordów skojarzonego z widokiem rekordu.  
  
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
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator formantu w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.  
  
 *value*  
 Odwołanie do elementu członkowskiego danych pola w skojarzonym `CRecordset` lub `CDaoRecordset` obiektu.  
  
 `pRecordset`  
 Wskaźnik do [crecordset —](../../mfc/reference/crecordset-class.md) lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 W kierunku odwrotnym, ta funkcja ustawia bieżące zaznaczenie w polu listy pierwszy wiersz, który rozpoczyna się od znaków w ciągu określonej przez *wartość*. Na transfer z tego zestawu rekordów do formantu Jeśli pole rekordów ma wartość Null, dokonaj wyboru zostanie usunięte z pola listy. Na transfer z formantu do zestawu rekordów Jeśli formant jest pusta, pole rekordów ma ustawioną wartość Null.  
  
 Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Druga wersja należy użyć, jeśli pracujesz z klasy oparte na DAO.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ddx_field — ogólne. Wywołuje się `DDX_FieldLBString` mogą być podobne.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdao.h  
  
##  <a name="ddx_fieldlbstringexact"></a>Ddx_fieldlbstringexact —  
 `DDX_FieldLBStringExact` Funkcja kopiuje aktualnie zaznaczone pole listy w widoku rekordów do [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) pola danych członkiem zestawu rekordów skojarzonego z widokiem rekordu.  
  
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
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator formantu w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.  
  
 *value*  
 Odwołanie do elementu członkowskiego danych pola w skojarzonym `CRecordset` lub `CDaoRecordset` obiektu.  
  
 `pRecordset`  
 Wskaźnik do [crecordset —](../../mfc/reference/crecordset-class.md) lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 W kierunku odwrotnym, ta funkcja ustawia bieżące zaznaczenie w polu listy do pierwszego wiersza, która dokładnie odpowiada określonym w ciągu *wartość*. Na transfer z tego zestawu rekordów do formantu Jeśli pole rekordów ma wartość Null, dokonaj wyboru zostanie usunięte z pola listy. Na transfer z formantu do zestawu rekordów Jeśli formant jest pusta, pole rekordów ma ustawioną wartość Null.  
  
 Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Druga wersja należy użyć, jeśli pracujesz z klasy oparte na DAO.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ddx_field — ogólne. Wywołuje się `DDX_FieldLBStringExact` mogą być podobne.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdao.h  
  
##  <a name="ddx_fieldradio"></a>Ddx_fieldradio —  
 `DDX_FieldRadio` Kojarzy liczony od zera funkcja `int` zmiennej członkowskiej rekordów z widoków rekordów z aktualnie wybranego przycisku radiowego w grupie przycisków radiowych w widoku rekordu.  
  
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
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator pierwszego w grupie (stylem **ws_group —**) kontrolek przycisków radiowych sąsiadujących ze sobą w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.  
  
 *value*  
 Odwołanie do elementu członkowskiego danych pola w skojarzonym `CRecordset` lub `CDaoRecordset` obiektu.  
  
 `pRecordset`  
 Wskaźnik do [crecordset —](../../mfc/reference/crecordset-class.md) lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Podczas przenoszenia z pola rekordów do widoku, włączenie tej funkcji *n-ty* przycisk radiowy (liczony od zera) i wyłącza innych przycisków. W kierunku odwrotnym ta funkcja ustawia pola rekordów numerem porządkowym przycisku radiowego, który jest obecnie na (zaznaczone). Przesunięcia w zestawie do formantu, jeśli pole rekordów ma wartość Null, nie przycisk jest zaznaczony. Na transfer z formantu do zestawu rekordów Jeśli formant nie jest zaznaczone, pole rekordów ma ustawioną wartość Null pole pozwala na który.  
  
 Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Druga wersja należy użyć, jeśli pracujesz z klasy oparte na DAO.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ddx_field — ogólne. Wywołuje się `DDX_FieldRadio` mogą być podobne.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdao.h  
  
##  <a name="ddx_fieldscroll"></a>Ddx_fieldscroll —  
 `DDX_FieldScroll` Funkcja synchronizuje jego położenie przewijania formantu paska przewijania w widoku rekordu i `int` pola danych członkiem zestawu rekordów skojarzonego z widokiem rekordu (lub z dowolnego zmienna całkowitoliczbowa wybrać go do mapowania).  
  
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
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *nIDC\**  
 Identyfikator pierwszego w grupie (stylem **ws_group —**) kontrolek przycisków radiowych sąsiadujących ze sobą w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.  
  
 *value*  
 Odwołanie do elementu członkowskiego danych pola w skojarzonym `CRecordset` lub `CDaoRecordset` obiektu.  
  
 `pRecordset`  
 Wskaźnik do [crecordset —](../../mfc/reference/crecordset-class.md) lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Podczas przenoszenia danych w zestawie do formantu, ta funkcja Ustawia położenie przewijania formantu paska przewijania wartość określoną w *wartość*. Przesunięcia w zestawie do formantu Jeśli pole rekordów ma wartość Null, pasek przewijania jest równa 0. Na transfer z formantu do zestawu rekordów Jeśli formant jest pusta, wartość pola rekordów jest 0.  
  
 Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszej wersji. Druga wersja należy użyć, jeśli pracujesz z klasy oparte na DAO.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ddx_field — ogólne. Wywołuje się `DDX_FieldScroll` mogą być podobne.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdao.h  

  ## <a name="nameddxfieldslidera--ddxfieldslider"></a>name = "ddx_fieldslider —" ></a> ddx_fieldslider —
`DDX_FieldSlider` Funkcja synchronizuje pozycji przycisku przewijania suwaka w widoku rekordu i `int` pola danych członkiem zestawu rekordów skojarzonego z widokiem rekordu (lub z dowolnego zmienna całkowitoliczbowa wybrać go do mapowania).  
   
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
 `pDX`  
 Wskaźnik do [cdataexchange —](cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator zasobu suwaka.  
  
 *value*  
 Odwołanie do wartości, aby wymienić. Ten parametr zawiera lub będzie można określić bieżącej pozycji przycisku przewijania suwaka.  
  
 `pRecordset`  
 Wskaźnik do skojarzonego `CRecordset` lub `CDaoRecordset` obiektu wymiany danych.  
   
### <a name="remarks"></a>Uwagi  
 Podczas przenoszenia danych w zestawie na suwaku, ta funkcja Ustawia położenie suwaka do wartości określonej w *wartość*. Przesunięcia w zestawie do formantu Jeśli pole rekordów ma wartość Null, położenie kontrolki suwaka jest równa 0. Na transfer z formantu do zestawu rekordów Jeśli formant jest pusta, wartość pola rekordów jest 0.  
  
 `DDX_FieldSlider`nie wymieniają informacje zakresu z kontrolkami suwaka możliwość ustawiania zakresu, a nie po prostu pozycji.  
  
 Jeśli pracujesz z klasy oparte na ODBC, należy użyć pierwszego zastąpienie funkcji. Drugi zastąpienie za pomocą klasy oparte na DAO.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla `CRecordView` i `CDaoRecordView` pól, zobacz [widoków rekordów](../../data/record-views-mfc-data-access.md). Uzyskać informacje o formantach suwaka, zobacz [przy użyciu CSliderCtrl](../using-csliderctrl.md).  
   
### <a name="example"></a>Przykład  
 Zobacz [ddx_fieldtext —](#ddx_fieldtext) przykład ddx_field — ogólne. Wywołuje się `DDX_FieldSlider` mogą być podobne.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
  
##  <a name="ddx_fieldtext"></a>Ddx_fieldtext —  
 `DDX_FieldText` Funkcji zarządzania transferem `int`, **krótki**, **długi**, `DWORD`, [cstring —](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **podwójne**, **BOOL**, lub **BAJTÓW** danych między kontrolkę pola edycji i elementy członkowskie danych pola zestawu rekordów.  
  
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
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator formantu w [CRecordView](../../mfc/reference/crecordview-class.md) lub [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) obiektu.  
  
 *value*  
 Odwołanie do elementu członkowskiego danych pola w skojarzonym `CRecordset` lub `CDaoRecordset` obiektu. Typ danych wartości zależy od której zastąpionej wersji `DDX_FieldText` używasz.  
  
 `pRecordset`  
 Wskaźnik do [crecordset —](../../mfc/reference/crecordset-class.md) lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu wymiany danych. Włącza ten wskaźnik `DDX_FieldText` wykrywania i ustawić wartości Null.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektów, `DDX_FieldText` zarządza także przesyłania [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), i [COleCurrency](../../mfc/reference/colecurrency-class.md) wartości. Puste okno edycji wskazuje wartość Null. Na transfer z tego zestawu rekordów do formantu, jeśli pole rekordów ma wartość Null, pole edycji ma wartość pustą. Na transfer z formantu do zestawu rekordów Jeśli formant jest pusta, pole rekordów ma ustawioną wartość Null.  
  
 Użyj wersji z [crecordset —](../../mfc/reference/crecordset-class.md) parametrów podczas pracy z klasy oparte na ODBC. Użyj wersji z [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) parametrów podczas pracy z klasy oparte na DAO.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md). Przykłady i więcej informacji na temat DDX dla [CRecordView](../../mfc/reference/crecordview-class.md) i [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pól, zobacz artykuł [widoków rekordów](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Przykład  
 Następujące `DoDataExchange` działać w ramach [CRecordView](../../mfc/reference/crecordview-class.md) zawiera `DDX_FieldText` funkcja wymaga trzech typów: `IDC_COURSELIST` jest pole kombi; inne formanty są pola edycji. Obiekty DAO programowania, *m_pSet* parametr jest wskaźnikiem do [crecordset —](../../mfc/reference/crecordset-class.md) lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md).  
  
 [!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]  

  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdao.h  
    
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
