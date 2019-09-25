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
ms.openlocfilehash: 6a33f5b64c5094bfe2ca2ff259b5cd8654058ed3
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "69502232"
---
# <a name="cvslistbox-class"></a>Klasa CVSListBox

`CVSListBox` Klasa obsługuje edytowalną kontrolkę listy.

## <a name="syntax"></a>Składnia

```
class CVSListBox : public CVSListBoxBase
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CVSListBox::CVSListBox](#cvslistbox)|Konstruuje `CVSListBox` obiekt.|
|`CVSListBox::~CVSListBox`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CVSListBox:: AddItem](#additem)|Dodaje ciąg do kontrolki listy. (Przesłania `CVSListBoxBase::AddItem`).|
|[CVSListBox::EditItem](#edititem)|Uruchamia operację edycji dla tekstu elementu kontrolki listy. (Przesłania `CVSListBoxBase::EditItem`).|
|[CVSListBox:: GetCount](#getcount)|Pobiera liczbę ciągów w kontrolce edytowalnej listy. (Przesłania `CVSListBoxBase::GetCount`).|
|[CVSListBox::GetItemData](#getitemdata)|Pobiera wartość 32-bitową specyficzną dla aplikacji, która jest skojarzona z edytowalnym elementem kontrolki listy. (Przesłania `CVSListBoxBase::GetItemData`).|
|[CVSListBox::GetItemText](#getitemtext)|Pobiera tekst edytowalnego elementu kontrolki listy. (Przesłania `CVSListBoxBase::GetItemText`).|
|[CVSListBox::GetSelItem](#getselitem)|Pobiera indeks (liczony od zera) aktualnie wybranego elementu w kontrolce listy edytowalnej. (Przesłania `CVSListBoxBase::GetSelItem`).|
|`CVSListBox::PreTranslateMessage`|Tłumaczy komunikaty okna przed ich wysłaniem do funkcji systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . Aby uzyskać więcej informacji i składni metod, zobacz [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Przesłania `CVSListBoxBase::PreTranslateMessage`).|
|[CVSListBox::RemoveItem](#removeitem)|Usuwa element z kontrolki edytowalnej listy. (Przesłania `CVSListBoxBase::RemoveItem`).|
|[CVSListBox::SelectItem](#selectitem)|Wybiera edytowalny ciąg kontrolny listy. (Przesłania `CVSListBoxBase::SelectItem`).|
|[CVSListBox::SetItemData](#setitemdata)|Kojarzy wartość 32-bitową specyficzną dla aplikacji z edytowalnym elementem kontrolki listy. (Przesłania `CVSListBoxBase::SetItemData`).|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CVSListBox::GetListHwnd](#getlisthwnd)|Zwraca uchwyt do bieżącej osadzonej kontrolki widoku listy.|

## <a name="remarks"></a>Uwagi

`CVSListBox` Klasa zawiera zestaw przycisków edycji, które umożliwiają użytkownikowi tworzenie, modyfikowanie, usuwanie lub zmienianie układu elementów w kontrolce listy.

Poniżej znajduje się obraz kontrolki edytowalnej listy. Drugi wpis listy zatytułowany "Item2 —" jest wybierany do edycji.

![CVSListBox — formant](../../mfc/reference/media/cvslistbox.png "CVSListBox — formant")

Jeśli używasz edytora zasobów do dodawania edytowalnej kontrolki listy, Zauważ, że okienko **przybornika** w edytorze nie udostępnia wstępnie zdefiniowanej kontrolki edytowalnej listy. Zamiast tego należy dodać kontrolkę statyczną, taką jak kontrolka **pole grupy** . Struktura używa kontrolki statycznej jako symbolu zastępczego, aby określić rozmiar i położenie kontrolki edytowalnej listy.

Aby użyć kontrolki listy edytowalnej w szablonie okna dialogowego, zadeklaruj `CVSListBox` zmienną w klasie okna dialogowego. Aby zapewnić obsługę wymiany danych między zmienną i formantem, zdefiniuj `DDX_Control` wpis makra `DoDataExchange` w metodzie okna dialogowego. Domyślnie kontrolka edytowalnej listy jest tworzona bez przycisków edycji. Użyj dziedziczonej metody CVSListBoxBase:: SetStandardButtons, aby włączyć przyciski edycji.

Aby uzyskać więcej informacji, zobacz katalog `New Controls` przykładów, przykład, pliki PAGE3. cpp i PAGE3. h.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CStatic](../../mfc/reference/cstatic-class.md)

`CVSListBoxBase`

[CVSListBox](../../mfc/reference/cvslistbox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxvslistbox. h

##  <a name="additem"></a>CVSListBox:: AddItem

Dodaje ciąg do kontrolki listy.

```
virtual int AddItem(
    const CString& strIext,
    DWORD_PTR dwData=0,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*strIext*<br/>
podczas Odwołanie do ciągu.

*dwData*<br/>
podczas Specyficzna dla aplikacji 32-bitowa wartość, która jest skojarzona z ciągiem. Wartość domyślna to 0.

*iIndex*<br/>
podczas Indeks (liczony od zera) pozycji, która będzie zawierać ciąg. Jeśli parametr *IIndex* ma wartość-1, ciąg zostanie dodany na końcu listy. Wartość domyślna to-1.

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) pozycji ciągu w kontrolce listy.

### <a name="remarks"></a>Uwagi

Użyj metody [CVSListBox:: GetItemData](#getitemdata) , aby pobrać wartość określoną przez parametr *dwData* . Ta wartość może być liczbą całkowitą specyficzną dla aplikacji lub wskaźnikiem do innych danych.

##  <a name="cvslistbox"></a>CVSListBox::CVSListBox

Konstruuje `CVSListBox` obiekt.

```
CVSListBox();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="edititem"></a>CVSListBox::EditItem

Uruchamia operację edycji dla tekstu elementu kontrolki listy.

```
virtual BOOL EditItem(int iIndex);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
podczas Indeks (liczony od zera) elementu kontrolki listy.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli operacja edycji zostanie uruchomiona pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użytkownik uruchamia operację edycji przez dwukrotne kliknięcie etykiety elementu lub naciśnięcie klawisza **F2** lub **spacja** , gdy element ma fokus.

##  <a name="getcount"></a>CVSListBox:: GetCount

Pobiera liczbę ciągów w kontrolce edytowalnej listy.

```
virtual int GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w kontrolce listy.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że liczba jest większa niż wartość indeksu ostatniego elementu, ponieważ indeks jest liczony od zera.

##  <a name="getitemdata"></a>CVSListBox::GetItemData

Pobiera wartość 32-bitową specyficzną dla aplikacji, która jest skojarzona z edytowalnym elementem kontrolki listy.

```
virtual DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
podczas Indeks (liczony od zera) elementu kontrolki listy edytowalnej.

### <a name="return-value"></a>Wartość zwracana

Wartość 32-bitowa, która jest skojarzona z określonym elementem.

### <a name="remarks"></a>Uwagi

Użyj metody [CVSListBox:: SetItemData](#setitemdata) lub [CVSListBox:: AddItem](#additem) , aby skojarzyć wartość 32-bitową z elementem kontrolki listy. Ta wartość może być liczbą całkowitą specyficzną dla aplikacji lub wskaźnikiem do innych danych.

##  <a name="getitemtext"></a>CVSListBox::GetItemText

Pobiera tekst edytowalnego elementu kontrolki listy.

```
virtual CString GetItemText(int iIndex) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
podczas Indeks (liczony od zera) elementu kontrolki listy edytowalnej.

### <a name="return-value"></a>Wartość zwracana

Obiekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) , który zawiera tekst określonego elementu.

### <a name="remarks"></a>Uwagi

##  <a name="getlisthwnd"></a>CVSListBox::GetListHwnd

Zwraca uchwyt do bieżącej osadzonej kontrolki widoku listy.

```
virtual HWND GetListHwnd() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do kontrolki widoku osadzonej listy.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby pobrać uchwyt do kontrolki widoku osadzonej listy, która `CVSListBox` obsługuje klasę.

##  <a name="getselitem"></a>CVSListBox::GetSelItem

Pobiera indeks (liczony od zera) aktualnie wybranego elementu w kontrolce listy edytowalnej.

```
virtual int GetSelItem() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli ta metoda zakończy się pomyślnie, indeks aktualnie wybranego elementu (liczony od zera); w przeciwnym razie-1.

### <a name="remarks"></a>Uwagi

##  <a name="removeitem"></a>CVSListBox:: RemoveItem

Usuwa element z kontrolki edytowalnej listy.

```
virtual BOOL RemoveItem(int iIndex);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
podczas Indeks (liczony od zera) elementu kontrolki listy edytowalnej.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli określony element zostanie usunięty; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="selectitem"></a>CVSListBox::SelectItem

Wybiera edytowalny ciąg kontrolny listy.

```
virtual BOOL SelectItem(int iItem);
```

### <a name="parameters"></a>Parametry

*iItem*<br/>
podczas Indeks (liczony od zera) elementu kontrolki listy edytowalnej.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wybiera określony element, a jeśli jest wymagana, przewija element do widoku.

##  <a name="setitemdata"></a>CVSListBox::SetItemData

Kojarzy wartość 32-bitową specyficzną dla aplikacji z edytowalnym elementem kontrolki listy.

```
virtual void SetItemData(
    int iIndex,
    DWORD_PTR dwData);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
podczas Indeks (liczony od zera) elementu kontrolki listy edytowalnej.

*dwData*<br/>
podczas Wartość 32-bitowa. Ta wartość może być liczbą całkowitą specyficzną dla aplikacji lub wskaźnikiem do innych danych.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
