---
title: Klasa CMFCKeyMapDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::DoModal
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::FormatItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::GetCommandKeys
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnInsertItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintHeader
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnSetColumns
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::PrintKeyMap
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::SetColumnsWidth
dev_langs:
- C++
helpviewer_keywords:
- CMFCKeyMapDialog [MFC], CMFCKeyMapDialog
- CMFCKeyMapDialog [MFC], DoModal
- CMFCKeyMapDialog [MFC], FormatItem
- CMFCKeyMapDialog [MFC], GetCommandKeys
- CMFCKeyMapDialog [MFC], OnInsertItem
- CMFCKeyMapDialog [MFC], OnPrintHeader
- CMFCKeyMapDialog [MFC], OnPrintItem
- CMFCKeyMapDialog [MFC], OnSetColumns
- CMFCKeyMapDialog [MFC], PrintKeyMap
- CMFCKeyMapDialog [MFC], SetColumnsWidth
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 460dddeb04ae7cd99d1016234c96c18dc1402cc4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401924"
---
# <a name="cmfckeymapdialog-class"></a>Klasa CMFCKeyMapDialog

`CMFCKeyMapDialog` Klasy obsługuje formant, który mapuje polecenia na klawisze klawiatury.

## <a name="syntax"></a>Składnia

```
class CMFCKeyMapDialog : public CDialogEx
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCKeyMapDialog::CMFCKeyMapDialog](#cmfckeymapdialog)|Konstruuje `CMFCKeyMapDialog` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCKeyMapDialog::DoModal](#domodal)|Wyświetlane jest okno dialogowe mapowania klawiatury.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCKeyMapDialog::FormatItem](#formatitem)|Metoda wywoływana przez platformę, by tworzyć ciąg, który opisuje mapowanie klawiszy. Domyślnie ciąg zawiera nazwę polecenia klawiszy skrótów i Opis klucza skrótu.|
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|Pobiera ciąg, który zawiera listę skrótów skojarzony z określonym poleceniem.|
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|Wywoływane przez platformę, zanim nowy element jest wstawiany do formantu listy wewnętrzny, który obsługuje kontrolę mapowania klawiatury.|
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|Metoda wywoływana przez platformę, by wydrukować nagłówek mapy klawiatury na nowej stronie.|
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|Metoda wywoływana przez platformę, by wydrukować element mapowania klawiatury.|
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|Metoda wywoływana przez platformę, by ustawić podpisy dla kolumn w formancie listy wewnętrznej, który obsługuje kontrolę mapowania klawiatury.|
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|Wywoływane przez platformę, gdy użytkownik kliknie **drukowania** przycisku.|
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|Metoda wywoływana przez platformę, by ustawić szerokość kolumn w formancie listy wewnętrznej, który obsługuje kontrolę mapowania klawiatury.|

## <a name="remarks"></a>Uwagi

Użyj `CMFCKeyMapDialog` klasy do zaimplementowania okno dialogowe mapowania klawiatury o zmiennym rozmiarze. Okno dialogowe użyto kontrolka widoku listy, aby wyświetlić skróty klawiaturowe i skojarzone z nimi polecenia.

Aby użyć `CMFCKeyMapDialog` klasy w aplikacji, przekazać wskaźnik do ramki głównego okna jako parametr do `CMFCKeyMapDialog` konstruktora. Następnie wywołaj `DoModal` metodę, aby uruchomić okno modalne okno dialogowe.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxkeymapdialog.h

##  <a name="cmfckeymapdialog"></a>  CMFCKeyMapDialog::CMFCKeyMapDialog

Konstruuje `CMFCKeyMapDialog` obiektu.

```
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bEnablePrint=FALSE);
```

### <a name="parameters"></a>Parametry

*pWndParentFrame*<br/>
[in] Wskaźnik do okna nadrzędnego `CMFCKeyMapDialog` obiektu.

*bEnablePrint*<br/>
[in] Wartość TRUE, jeśli lista klawiszy skrótów, może zostać zrealizowane; w przeciwnym razie wartość FALSE. Wartość domyślna to FALSE.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCKeyMapDialog` klasy. W tym przykładzie jest częścią [Visual Studio przykład](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]

##  <a name="domodal"></a>  CMFCKeyMapDialog::DoModal

Wyświetlane jest okno dialogowe mapowania klawiatury.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita ze znakiem, takich jak IDOK lub IDCANCEL, który jest przekazywany do [CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog) metody. Metody, z kolei zamknięcie okna dialogowego. Aby uzyskać więcej informacji, zobacz [CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal).

### <a name="remarks"></a>Uwagi

Okno dialogowe mapowania klawiatury pozwala sposób wybierania i przypisywania klawiszy skrótów do różnych kategorii poleceń. Ponadto możesz skopiować wybrany klawiszy i ich opisy do Schowka.

##  <a name="formatitem"></a>  CMFCKeyMapDialog::FormatItem

Metoda wywoływana przez platformę, by tworzyć ciąg, który opisuje mapowanie klawiszy. Domyślnie ciąg zawiera nazwę polecenia klawiszy skrótów i Opis klucza skrótu.

```
virtual CString FormatItem(int nItem) const;
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
[in] Liczony od zera indeks elementu na liście wewnętrznych mapowań klucza.

### <a name="return-value"></a>Wartość zwracana

A `CString` obiekt, który zawiera tekst sformatowany elementu.

### <a name="remarks"></a>Uwagi

##  <a name="getcommandkeys"></a>  CMFCKeyMapDialog::GetCommandKeys

Pobiera wartość ciągu. Ciąg zawiera listę skrótów klawiaturowych, które są skojarzone z określonym poleceniem.

```
virtual CString GetCommandKeys(UINT uiCmdID) const;
```

### <a name="parameters"></a>Parametry

*uiCmdID*<br/>
[in] Identyfikator polecenia.

### <a name="return-value"></a>Wartość zwracana

Rozdzielana średnikami (";") lista klawiszy skrótu, który jest skojarzony z określonym poleceniem.

### <a name="remarks"></a>Uwagi

##  <a name="oninsertitem"></a>  CMFCKeyMapDialog::OnInsertItem

Wywoływane przez platformę, zanim nowy element jest wstawiany do kontrolkę listy wewnętrznej, która obsługuje kontrolę mapowania klawiatury.

```
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,
    int nItem);
```

### <a name="parameters"></a>Parametry

*pButton*<br/>
[in] Wskaźnik na przycisku paska narzędzi, który służy do mapowania klawiatury kombinacji klawiszy polecenia nazwę i opis. Element mapy kluczy są przechowywane w kontrolce listy wewnętrznej.

*nItem*<br/>
[in] Liczony od zera indeks, który określa lokalizację wstawić nowy element mapy kluczy w formancie listy wewnętrznej.

### <a name="remarks"></a>Uwagi

##  <a name="onprintheader"></a>  CMFCKeyMapDialog::OnPrintHeader

Metoda wywoływana przez platformę, by wydrukować nagłówek mapy klawiatury na nowej stronie.

```
virtual int OnPrintHeader(
    CDC& dc,
    int nPage,
    int cx) const;
```

### <a name="parameters"></a>Parametry

*Kontroler domeny*<br/>
[in] Kontekst urządzenia dla drukarki.

*nPage*<br/>
[in] Numer strony do wydrukowania.

*CX*<br/>
[in] Przesunięcie w poziomie nagłówka, w pikselach.

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, wysokość drukowanego tekstu. Aby uzyskać więcej informacji, zobacz sekcję zwracają wartość [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext).

### <a name="remarks"></a>Uwagi

Struktura używa tej metody, aby wydrukować mapy klawiatury. Domyślnie ta metoda drukuje numer strony, nazwę aplikacji i tytuł okna dialogowego.

##  <a name="onprintitem"></a>  CMFCKeyMapDialog::OnPrintItem

Metoda wywoływana przez platformę, by wydrukować element mapowania klawiatury.

```
virtual int OnPrintItem(
    CDC& dc,
    int nItem,
    int y,
    int cx,
    BOOL bCalcHeight) const;
```

### <a name="parameters"></a>Parametry

*Kontroler domeny*<br/>
[in] Kontekst urządzenia drukarki.

*nItem*<br/>
[in] Liczony od zera indeks elementu do drukowania.

*y*<br/>
[in] Przesunięcie w pionie między górnej części strony i pozycja elementu.

*CX*<br/>
[in] Przesunięcie w poziomie między lewym rogu strony i pozycja elementu.

*bCalcHeight*<br/>
[in] Wartość TRUE, aby obliczyć najlepsze wysokość elementu wydruku; Wartość FAŁSZ, aby obciąć drukowania elementu, tak aby zmieścił domyślna przestrzeń.

### <a name="return-value"></a>Wartość zwracana

Wysokość elementu drukowanych.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, aby wydrukować elementu okna dialogowego mapy kluczy. Domyślnie ta metoda drukuje elementu nazwa polecenia klawiszy skrótów i opis polecenia.

##  <a name="onsetcolumns"></a>  CMFCKeyMapDialog::OnSetColumns

Metoda wywoływana przez platformę, by ustawić podpisy dla kolumn w formancie listy wewnętrznej, który obsługuje kontrolę mapowania klawiatury.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda uzyskuje dostęp do transkrypcji dla kolumn z trzech zasobów. Polecenie Podpis kolumny pochodzi z IDS_AFXBARRES_COMMAND, podpis kolumny klucza jest z IDS_AFXBARRES_KEYS, i podpis opis kolumny pochodzi z IDS_AFXBARRES_DESCRIPTION.

##  <a name="printkeymap"></a>  CMFCKeyMapDialog::PrintKeyMap

Wywoływane przez platformę, gdy użytkownik kliknie **drukowania** przycisku.

```
virtual void PrintKeyMap();
```

### <a name="remarks"></a>Uwagi

`PrintKeyMap` Metoda drukuje mapy kluczy. Inicjuje nowe zadanie drukowania, a następnie w wielokrotnie wywołuje [CMFCKeyMapDialog::OnPrintHeader](#onprintheader) i [CMFCKeyMapDialog::OnPrintItem](#onprintitem) metody do momentu, wydrukowaniu mapowań klucza.

##  <a name="setcolumnswidth"></a>  CMFCKeyMapDialog::SetColumnsWidth

Metoda wywoływana przez platformę, by ustawić szerokość kolumn w formancie listy wewnętrznej, który obsługuje kontrolę mapowania klawiatury.

```
virtual void SetColumnsWidth();
```

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia określenie listy wewnętrznych kolumn formantu do domyślnej szerokości. Po pierwsze jest obliczana szerokość kolumny klawiszy skrótów. Następnie jedną trzecią szerokości jest przydzielany do kolumny polecenia i pozostałych dwóch jest przydzielany do opis kolumny.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)
