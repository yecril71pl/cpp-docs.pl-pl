---
title: Klasa CVSListBox
ms.date: 11/19/2018
f1_keywords:
- CVSListBox
- AFXVSLISTBOX/CVSListBox
- AFXVSLISTBOX/CVSListBox::CVSListBox
- AFXVSLISTBOX/CVSListBox::AddItem
- AFXVSLISTBOX/CVSListBox::EditItem
- AFXVSLISTBOX/CVSListBox::GetCount
- AFXVSLISTBOX/CVSListBox::GetItemData
- AFXVSLISTBOX/CVSListBox::GetItemText
- AFXVSLISTBOX/CVSListBox::GetSelItem
- AFXVSLISTBOX/CVSListBox::RemoveItem
- AFXVSLISTBOX/CVSListBox::SelectItem
- AFXVSLISTBOX/CVSListBox::SetItemData
- AFXVSLISTBOX/CVSListBox::GetListHwnd
helpviewer_keywords:
- CVSListBox [MFC], CVSListBox
- CVSListBox [MFC], AddItem
- CVSListBox [MFC], EditItem
- CVSListBox [MFC], GetCount
- CVSListBox [MFC], GetItemData
- CVSListBox [MFC], GetItemText
- CVSListBox [MFC], GetSelItem
- CVSListBox [MFC], RemoveItem
- CVSListBox [MFC], SelectItem
- CVSListBox [MFC], SetItemData
- CVSListBox [MFC], GetListHwnd
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
ms.openlocfilehash: 4ea48a263a01133419067979ee5fa3e62105c7f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373193"
---
# <a name="cvslistbox-class"></a>Klasa CVSListBox

Klasa `CVSListBox` obsługuje kontrolę listy edytowalnej.

## <a name="syntax"></a>Składnia

```
class CVSListBox : public CVSListBoxBase
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CVSListBox::CVSListBox](#cvslistbox)|Konstruuje `CVSListBox` obiekt.|
|`CVSListBox::~CVSListBox`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CVSListBox::AddItem](#additem)|Dodaje ciąg do formantu listy. (Przesłania `CVSListBoxBase::AddItem`).|
|[CVSListBox::EditItem](#edititem)|Rozpoczyna operację edycji na tekście elementu kontrolnego listy. (Przesłania `CVSListBoxBase::EditItem`).|
|[CVSListBox::GetCount](#getcount)|Pobiera liczbę ciągów w kontrolce listy edytowalnej. (Przesłania `CVSListBoxBase::GetCount`).|
|[CVSListBox::GetItemData](#getitemdata)|Pobiera wartość 32-bitową specyficzną dla aplikacji, która jest skojarzona z edytowalnym elementem kontroli listy. (Przesłania `CVSListBoxBase::GetItemData`).|
|[CVSListBox::GetItemText](#getitemtext)|Pobiera tekst edytowanego elementu kontrolnego listy. (Przesłania `CVSListBoxBase::GetItemText`).|
|[CVSListBox::GetSelItem](#getselitem)|Pobiera indeks od zera aktualnie wybranego elementu w kontrolce listy edytowalnej. (Przesłania `CVSListBoxBase::GetSelItem`).|
|`CVSListBox::PreTranslateMessage`|Tłumaczy komunikaty okna, zanim zostaną wysłane do [funkcji TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systemu Windows. Aby uzyskać więcej informacji i składni metody, zobacz [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Przesłania `CVSListBoxBase::PreTranslateMessage`).|
|[CVSListBox::Usuńnik](#removeitem)|Usuwa element z kontrolki listy edytowalnej. (Przesłania `CVSListBoxBase::RemoveItem`).|
|[CVSListBox::SelectItem](#selectitem)|Wybiera edytowalny ciąg kontrolny listy. (Przesłania `CVSListBoxBase::SelectItem`).|
|[CVSListBox::SetItemData](#setitemdata)|Kojarzy wartość 32-bitową specyficzną dla aplikacji z edytowalnym elementem kontroli listy. (Przesłania `CVSListBoxBase::SetItemData`).|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CVSListBox::GetListHwnd](#getlisthwnd)|Zwraca uchwyt do bieżącego widoku osadzonej listy.|

## <a name="remarks"></a>Uwagi

Klasa `CVSListBox` zawiera zestaw przycisków edycji, które umożliwiają użytkownikowi tworzenie, modyfikowanie, usuwanie lub zmienianie rozmieszczenia elementów w formancie listy.

Poniżej znajduje się obraz kontrolki listy edytowalnej. Drugi wpis listy, zatytułowany "Item2", jest wybrany do edycji.

![Sterowanie CVSListBox](../../mfc/reference/media/cvslistbox.png "Sterowanie CVSListBox")

Jeśli edytor zasobów służy do dodawania kontrolki listy edytowalnej, należy zauważyć, że **okienko Przybornik** edytora nie zawiera wstępnie zdefiniowanej kontrolki listy edytowalnej. Zamiast tego należy dodać formant statyczny, taki jak formant **Pole grupy.** Struktura używa formantu statycznego jako symbolu zastępczego, aby określić rozmiar i położenie kontrolki listy edytowalnej.

Aby użyć kontrolki edytowalnej listy w `CVSListBox` szablonie okna dialogowego, zadeklaruj zmienną w klasie okna dialogowego. Aby wspierać wymianę danych między zmienną `DDX_Control` a formantem, należy zdefiniować wpis makra w `DoDataExchange` metodzie okna dialogowego. Domyślnie kontrolka listy edytowalnej jest tworzona bez przycisków edycji. Użyj odziedziczonej metody CVSListBoxBase::SetStandardButtons, aby włączyć przyciski edycji.

Aby uzyskać więcej informacji, zobacz katalog `New Controls` Przykłady, przykład, pliki Page3.cpp i Page3.h.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cstatic](../../mfc/reference/cstatic-class.md)

`CVSListBoxBase`

[CVSListBox (Polski)](../../mfc/reference/cvslistbox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxvslistbox.h

## <a name="cvslistboxadditem"></a><a name="additem"></a>CVSListBox::AddItem

Dodaje ciąg do formantu listy.

```
virtual int AddItem(
    const CString& strIext,
    DWORD_PTR dwData=0,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*strIext (striext)*<br/>
[w] Odwołanie do ciągu.

*dwData (dane)*<br/>
[w] Wartość 32-bitowa specyficzne dla aplikacji, która jest skojarzona z ciągiem. Wartość domyślna to 0.

*Iindex*<br/>
[w] Indeks od zera pozycji, która będzie zawierać ciąg. Jeśli parametr *iIndex* wynosi -1, ciąg jest dodawany na końcu listy. Wartość domyślna to -1.

### <a name="return-value"></a>Wartość zwracana

Indeks od zera pozycji ciągu w formancie listy.

### <a name="remarks"></a>Uwagi

Użyj [metody CVSListBox::GetItemData,](#getitemdata) aby pobrać wartość określoną przez parametr *dwData.* Ta wartość może być całkowitej specyficznej dla aplikacji lub wskaźnik do innych danych.

## <a name="cvslistboxcvslistbox"></a><a name="cvslistbox"></a>CVSListBox::CVSListBox

Konstruuje `CVSListBox` obiekt.

```
CVSListBox();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cvslistboxedititem"></a><a name="edititem"></a>CVSListBox::EditItem

Rozpoczyna operację edycji na tekście elementu kontrolnego listy.

```
virtual BOOL EditItem(int iIndex);
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
[w] Indeks od zera elementu kontroli listy.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli operacja edycji zostanie pomyślnie rozpocznie się; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użytkownik rozpoczyna operację edycji, klikając dwukrotnie etykietę elementu lub naciskając klawisz **F2** lub **klawisz SPACJA,** gdy element ma fokus.

## <a name="cvslistboxgetcount"></a><a name="getcount"></a>CVSListBox::GetCount

Pobiera liczbę ciągów w kontrolce listy edytowalnej.

```
virtual int GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w formancie listy.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że liczba jest o jeden większa niż wartość indeksu ostatniego elementu, ponieważ indeks jest oparty na wartości zero.

## <a name="cvslistboxgetitemdata"></a><a name="getitemdata"></a>CVSListBox::GetItemData

Pobiera wartość 32-bitową specyficzną dla aplikacji, która jest skojarzona z edytowalnym elementem kontroli listy.

```
virtual DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
[w] Indeks od zera edytowalny element kontrolny listy.

### <a name="return-value"></a>Wartość zwracana

Wartość 32-bitowa skojarzona z określonym elementem.

### <a name="remarks"></a>Uwagi

Użyj [metody CVSListBox::SetItemData](#setitemdata) lub [CVSListBox::AddItem,](#additem) aby skojarzyć wartość 32-bitową z elementem kontroli listy. Ta wartość może być całkowitej specyficznej dla aplikacji lub wskaźnik do innych danych.

## <a name="cvslistboxgetitemtext"></a><a name="getitemtext"></a>CVSListBox::GetItemText

Pobiera tekst edytowanego elementu kontrolnego listy.

```
virtual CString GetItemText(int iIndex) const;
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
[w] Indeks od zera edytowalny element kontrolny listy.

### <a name="return-value"></a>Wartość zwracana

Obiekt [CString,](../../atl-mfc-shared/reference/cstringt-class.md) który zawiera tekst określonego elementu.

### <a name="remarks"></a>Uwagi

## <a name="cvslistboxgetlisthwnd"></a><a name="getlisthwnd"></a>CVSListBox::GetListHwnd

Zwraca uchwyt do bieżącego widoku osadzonej listy.

```
virtual HWND GetListHwnd() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do formantu widoku listy osadzonej.

### <a name="remarks"></a>Uwagi

Ta metoda służy do pobierania dojścia do formantu widoku listy osadzonej, który obsługuje `CVSListBox` klasę.

## <a name="cvslistboxgetselitem"></a><a name="getselitem"></a>CVSListBox::GetSelItem

Pobiera indeks od zera aktualnie wybranego elementu w kontrolce listy edytowalnej.

```
virtual int GetSelItem() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli ta metoda zakończy się pomyślnie, indeks od zera aktualnie wybranego elementu; w przeciwnym razie -1.

### <a name="remarks"></a>Uwagi

## <a name="cvslistboxremoveitem"></a><a name="removeitem"></a>CVSListBox::Usuńnik

Usuwa element z kontrolki listy edytowalnej.

```
virtual BOOL RemoveItem(int iIndex);
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
[w] Indeks od zera edytowalny element kontrolny listy.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli określony element zostanie usunięty; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cvslistboxselectitem"></a><a name="selectitem"></a>CVSListBox::SelectItem

Wybiera edytowalny ciąg kontrolny listy.

```
virtual BOOL SelectItem(int iItem);
```

### <a name="parameters"></a>Parametry

*Iitem*<br/>
[w] Indeks od zera edytowalny element kontrolny listy.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wybiera określony element, a jeśli jest to wymagane, przewija element do widoku.

## <a name="cvslistboxsetitemdata"></a><a name="setitemdata"></a>CVSListBox::SetItemData

Kojarzy wartość 32-bitową specyficzną dla aplikacji z edytowalnym elementem kontroli listy.

```
virtual void SetItemData(
    int iIndex,
    DWORD_PTR dwData);
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
[w] Indeks od zera edytowalny element kontrolny listy.

*dwData (dane)*<br/>
[w] Wartość 32-bitowa. Ta wartość może być całkowitej specyficznej dla aplikacji lub wskaźnik do innych danych.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
