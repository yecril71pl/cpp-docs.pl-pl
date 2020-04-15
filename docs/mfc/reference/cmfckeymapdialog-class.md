---
title: Klasa CMFCKeyMapDialog
ms.date: 11/04/2016
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
ms.openlocfilehash: 22aa006ce214ca720192bb761e2ff2b35a64fce3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374413"
---
# <a name="cmfckeymapdialog-class"></a>Klasa CMFCKeyMapDialog

Klasa `CMFCKeyMapDialog` obsługuje formant, który mapuje polecenia do klawiszy na klawiaturze.

## <a name="syntax"></a>Składnia

```
class CMFCKeyMapDialog : public CDialogEx
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCKeyMapDialog::CMFCKeyMapDialog](#cmfckeymapdialog)|Konstruuje `CMFCKeyMapDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCKeyMapDialog::DoModal](#domodal)|Wyświetla okno dialogowe mapowania klawiatury.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCKeyMapDialog::FormatItem](#formatitem)|Wywoływane przez strukturę do tworzenia ciągu, który opisuje mapowanie klucza. Domyślnie ciąg zawiera nazwę polecenia, używane klawisze skrótów i opis klucza skrótu.|
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|Pobiera ciąg zawierający listę klawiszy skrótów skojarzonych z określonym poleceniem.|
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|Wywoływane przez platformę przed nowy element jest wstawiany do kontroli listy wewnętrznej, która obsługuje formant mapowania klawiatury.|
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|Wywoływana przez strukturę do drukowania nagłówka mapy klawiatury na nowej stronie.|
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|Wywoływane przez strukturę do drukowania elementu mapowania klawiatury.|
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|Wywoływane przez strukturę, aby ustawić podpisy dla kolumn w kontroli listy wewnętrznej, która obsługuje formant mapowania klawiatury.|
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|Wywoływane przez strukturę, gdy użytkownik kliknie przycisk **Drukuj.**|
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|Wywoływane przez strukturę, aby ustawić szerokość kolumn w kontroli listy wewnętrznej, która obsługuje formant mapowania klawiatury.|

## <a name="remarks"></a>Uwagi

Użyj `CMFCKeyMapDialog` klasy, aby zaimplementować okno dialogowe mapowania klawiatury o zmiennym rozmiarze. Okno dialogowe używa formantu widoku listy do wyświetlania skrótów klawiaturowych i skojarzonych z nimi poleceń.

Aby użyć `CMFCKeyMapDialog` klasy w aplikacji, przekaż w wskaźniku do okna `CMFCKeyMapDialog` ramki głównej jako parametr do konstruktora. Następnie wywołaj metodę, `DoModal` aby rozpocząć modalne okno dialogowe.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[Cdialogex](../../mfc/reference/cdialogex-class.md)

[CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxkeymapdialog.h

## <a name="cmfckeymapdialogcmfckeymapdialog"></a><a name="cmfckeymapdialog"></a>CMFCKeyMapDialog::CMFCKeyMapDialog

Konstruuje `CMFCKeyMapDialog` obiekt.

```
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bEnablePrint=FALSE);
```

### <a name="parameters"></a>Parametry

*pWndParentFrame*<br/>
[w] Wskaźnik do okna nadrzędnego `CMFCKeyMapDialog` obiektu.

*bWzdrowisk*<br/>
[w] PRAWDA, jeśli można wydrukować listę klawiszy akceleratora; w przeciwnym razie FALSE. Wartość domyślna to FALSE.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCKeyMapDialog` skonstruować obiekt klasy. W tym przykładzie jest częścią [przykładu demo programu Visual Studio.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]

## <a name="cmfckeymapdialogdomodal"></a><a name="domodal"></a>CMFCKeyMapDialog::DoModal

Wyświetla okno dialogowe mapowania klawiatury.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Podpisana liczba całkowita, taka jak IDOK lub IDCANCEL, przekazywana do [metody CDialog::EndDialog.](../../mfc/reference/cdialog-class.md#enddialog) Metoda z kolei zamyka okno dialogowe. Aby uzyskać więcej informacji, zobacz [CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal).

### <a name="remarks"></a>Uwagi

Okno dialogowe mapowanie klawiatury umożliwia zaznaczanie i przypisywanie klawiszy akceleratora do różnych kategorii poleceń. Ponadto można skopiować wybrane klawisze akceleratora i ich opis do schowka.

## <a name="cmfckeymapdialogformatitem"></a><a name="formatitem"></a>CMFCKeyMapDialog::FormatItem

Wywoływane przez strukturę do tworzenia ciągu, który opisuje mapowanie klucza. Domyślnie ciąg zawiera nazwę polecenia, używane klawisze skrótów i opis klucza skrótu.

```
virtual CString FormatItem(int nItem) const;
```

### <a name="parameters"></a>Parametry

*nJejsza*<br/>
[w] Indeks od zera elementu na wewnętrznej liście mapowań kluczy.

### <a name="return-value"></a>Wartość zwracana

Obiekt `CString` zawierający sformatowany tekst elementu.

### <a name="remarks"></a>Uwagi

## <a name="cmfckeymapdialoggetcommandkeys"></a><a name="getcommandkeys"></a>CMFCKeyMapDialog::GetCommandKeys

Pobiera wartość ciągu. Ciąg zawiera listę klawiszy skrótów skojarzonych z określonym poleceniem.

```
virtual CString GetCommandKeys(UINT uiCmdID) const;
```

### <a name="parameters"></a>Parametry

*identyfikator uiCmdID*<br/>
[w] Identyfikator polecenia.

### <a name="return-value"></a>Wartość zwracana

Lista klawiszy skrótów rozdzielana średnikami (';') skojarzona z określonym poleceniem.

### <a name="remarks"></a>Uwagi

## <a name="cmfckeymapdialogoninsertitem"></a><a name="oninsertitem"></a>CMFCKeyMapDialog::OnInsertItem

Wywoływana przez platformę, zanim nowy element zostanie wstawiony do wewnętrznej kontroli listy, która obsługuje formant mapowania klawiatury.

```
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,
    int nItem);
```

### <a name="parameters"></a>Parametry

*pButton (przycisk)*<br/>
[w] Wskaźnik do przycisku paska narzędzi, który służy do mapowania kombinacji klawiszy klawiatury na nazwę polecenia i opis. Element mapy klucza jest przechowywany w wewnętrznej kontroli listy.

*nJejsza*<br/>
[w] Indeks oparty na wartości zero, który określa, gdzie należy wstawić nowy element mapy klucza do kontroli listy wewnętrznej.

### <a name="remarks"></a>Uwagi

## <a name="cmfckeymapdialogonprintheader"></a><a name="onprintheader"></a>CMFCKeyMapDialog::OnPrintHeader

Wywoływana przez strukturę do drukowania nagłówka mapy klawiatury na nowej stronie.

```
virtual int OnPrintHeader(
    CDC& dc,
    int nPage,
    int cx) const;
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
[w] Kontekst urządzenia dla drukarki.

*strona nPage*<br/>
[w] Numer strony do wydrukowania.

*Cx*<br/>
[w] Przesunięcie poziome nagłówka w pikselach.

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, wysokość drukowanego tekstu. Aby uzyskać więcej informacji, zobacz sekcję Wartość zwrotu [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext).

### <a name="remarks"></a>Uwagi

Struktura używa tej metody do drukowania mapy klawiatury. Domyślnie ta metoda drukuje numer strony, nazwę aplikacji i tytuł okna dialogowego.

## <a name="cmfckeymapdialogonprintitem"></a><a name="onprintitem"></a>CMFCKeyMapDialog::OnPrintItem

Wywoływane przez strukturę do drukowania elementu mapowania klawiatury.

```
virtual int OnPrintItem(
    CDC& dc,
    int nItem,
    int y,
    int cx,
    BOOL bCalcHeight) const;
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
[w] Kontekst urządzenia drukarki.

*nJejsza*<br/>
[w] Indeks od zera towaru do wydrukowania.

*Y*<br/>
[w] Przesunięcie w pionie między górną częścią strony a położeniem elementu.

*Cx*<br/>
[w] Przesunięcie poziome między lewą stroną strony a położeniem elementu.

*bCalcHeight*<br/>
[w] PRAWDA, aby obliczyć najlepszą wysokość dla elementu wydruku; FALSE, aby obciąć element wydruku tak, aby pasował do miejsca domyślnego.

### <a name="return-value"></a>Wartość zwracana

Wysokość drukowanego elementu.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, aby wydrukować element okna dialogowego mapy klucza. Domyślnie ta metoda drukuje nazwę polecenia elementu, klawisze skrótów i opis polecenia.

## <a name="cmfckeymapdialogonsetcolumns"></a><a name="onsetcolumns"></a>CMFCKeyMapDialog::OnSetColumns

Wywoływane przez strukturę, aby ustawić podpisy dla kolumn w kontroli listy wewnętrznej, która obsługuje formant mapowania klawiatury.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda uzyskuje podpisy dla kolumn z trzech zasobów. Podpis kolumny polecenia pochodzi z IDS_AFXBARRES_COMMAND, podpis kolumny klucza pochodzi z IDS_AFXBARRES_KEYS, a podpis kolumny opisu pochodzi z IDS_AFXBARRES_DESCRIPTION.

## <a name="cmfckeymapdialogprintkeymap"></a><a name="printkeymap"></a>CMFCKeyMapDialog::PrintKeyMap

Wywoływane przez strukturę, gdy użytkownik kliknie przycisk **Drukuj.**

```
virtual void PrintKeyMap();
```

### <a name="remarks"></a>Uwagi

Metoda `PrintKeyMap` drukuje mapę klucza. Inicjuje nowe zadanie drukowania, a następnie wielokrotnie wywołuje [CMFCKeyMapDialog::OnPrintHeader](#onprintheader) i [CMFCKeyMapDialog::OnPrintItem](#onprintitem) metody, aż wszystkie mapowania kluczy są drukowane.

## <a name="cmfckeymapdialogsetcolumnswidth"></a><a name="setcolumnswidth"></a>CMFCKeyMapDialog::SetColumnsWidth

Wywoływane przez strukturę, aby ustawić szerokość kolumn w kontroli listy wewnętrznej, która obsługuje formant mapowania klawiatury.

```
virtual void SetColumnsWidth();
```

### <a name="remarks"></a>Uwagi

Ta metoda ustawia kolumny kontrolki listy wewnętrznej na domyślne szerokości. Najpierw obliczana jest szerokość kolumny klawiszy skrótów. Następnie jedna trzecia pozostałej szerokości jest przydzielana do kolumny polecenia, a pozostałe dwie trzecie jest przydzielane do kolumny opisu.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)
