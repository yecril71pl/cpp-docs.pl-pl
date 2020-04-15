---
title: Klasa CMFCRibbonSeparator
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::AddToListBox
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CopyFrom
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::GetRegularSize
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsTabStop
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDraw
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDrawOnList
helpviewer_keywords:
- CMFCRibbonSeparator [MFC], CMFCRibbonSeparator
- CMFCRibbonSeparator [MFC], AddToListBox
- CMFCRibbonSeparator [MFC], CopyFrom
- CMFCRibbonSeparator [MFC], GetRegularSize
- CMFCRibbonSeparator [MFC], IsSeparator
- CMFCRibbonSeparator [MFC], IsTabStop
- CMFCRibbonSeparator [MFC], OnDraw
- CMFCRibbonSeparator [MFC], OnDrawOnList
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
ms.openlocfilehash: 41a958c78719f6aedf1cc02f8e3ff5a2dbbf0e1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368852"
---
# <a name="cmfcribbonseparator-class"></a>Klasa CMFCRibbonSeparator

Implementuje separator wstążki.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCRibbonParator::CMFCRibbonSeparator](#cmfcribbonseparator)|Konstruuje `CMFCRibbonSeparator` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|Dodaje separator do listy **Polecenia** w oknie dialogowym **Dostosowywanie.** (Zastępuje [CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|
|`CMFCRibbonSeparator::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|`CMFCRibbonSeparator::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|

### <a name="protected-methods"></a>Metody chronione

|||
|-|-|
|Nazwa|Opis|
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|Metoda kopiowania, która ustawia zmienne członkowskie separatora z innego obiektu.|
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|Zwraca rozmiar separatora.|
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|Wskazuje, czy jest to separator.|
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|Wskazuje, czy jest to tabulator.|
|[CMFCRibbonSeparator::OnDraw](#ondraw)|Wywoływane przez system do rysowania separatora na wstążce lub pasku narzędzi Szybki dostęp.|
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|Wywoływany przez system do rysowania separatora na liście **Polecenia.**|

## <a name="remarks"></a>Uwagi

Separator wstążki to pionowa lub pozioma linia, która logicznie oddziela elementy wstążki. Separator można narysować na formancie wstążki, głównym menu aplikacji, pasku stanu wstążki i pasku narzędzi Szybki dostęp.

Aby użyć separatora w aplikacji, skonstruuj nowy obiekt i dodaj go do głównego menu aplikacji, jak pokazano poniżej:

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```

Wywołanie [CMFCRibbonPanel::AddSeparator,](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) aby dodać separatory do paneli wstążki. Separatory są przydzielane i dodawane wewnętrznie przez `AddSeparator` metodę.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonParator](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxbaseribbonelement.h

## <a name="cmfcribbonseparatoraddtolistbox"></a><a name="addtolistbox"></a>CMFCRibbonSeparator::AddToListBox

Dodaje separator do listy **Polecenia** w oknie dialogowym **Dostosowywanie.**

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>Parametry

*pWndListBox (Skrzynka pocztowa)*<br/>
[w] Wskaźnik do listy **Polecenia,** na którym jest dodawany separator.

*bDeep*<br/>
[w] Ignorowane.

### <a name="return-value"></a>Wartość zwracana

Indeks od zera do ciągu w polu listy określonym przez *pWndListBox*.

## <a name="cmfcribbonseparatorcmfcribbonseparator"></a><a name="cmfcribbonseparator"></a>CMFCRibbonParator::CMFCRibbonSeparator

Konstruuje `CMFCRibbonSeparator` obiekt.

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>Parametry

*bIsHoriz (własobie)*<br/>
[w] Jeśli prawda, separator jest poziomy; jeśli FALSE, separator jest pionowy.

### <a name="remarks"></a>Uwagi

Separatory poziome są używane w menu aplikacji. Separatory pionowe są używane na paskach narzędzi.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCRibbonSeparator` skonstruować obiekt klasy.

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

## <a name="cmfcribbonseparatorcopyfrom"></a><a name="copyfrom"></a>CMFCRibbonSeparator::CopyFrom

Metoda kopiowania, która ustawia zmienne członkowskie separatora z innego obiektu.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parametry

*Src*<br/>
[w] Element wstążki źródłowej do skopiowania.

## <a name="cmfcribbonseparatorgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonSeparator::GetRegularSize

Zwraca rozmiar separatora.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do zawartości urządzenia.

### <a name="return-value"></a>Wartość zwracana

Rozmiar separatora w danym kontekście urządzenia.

## <a name="cmfcribbonseparatorisseparator"></a><a name="isseparator"></a>CMFCRibbonSeparator::IsSeparator

Wskazuje, czy jest to separator.

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze prawda dla tej klasy.

## <a name="cmfcribbonseparatoristabstop"></a><a name="istabstop"></a>CMFCRibbonSeparator::IsTabStop

Wskazuje, czy jest to tabulator.

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze FALSE dla tej klasy.

### <a name="remarks"></a>Uwagi

Separator wstążki nie jest tabulatorem.

## <a name="cmfcribbonseparatorondraw"></a><a name="ondraw"></a>CMFCRibbonSeparator::OnDraw

Wywoływane przez system do rysowania separatora na wstążce lub pasku narzędzi Szybki dostęp.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

## <a name="cmfcribbonseparatorondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonSeparator::OnDrawOnList

Wywoływany przez system do rysowania separatora na liście **Polecenia.**

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Pdc*|[w] Wskaźnik do kontekstu urządzenia.|
|*strText (tekst)*|[w] Tekst wyświetlany na liście.|
|*nTextOffset (Zestaw nTextOffset)*|[w] Odstępy między tekstem a lewą stroną prostokąta ograniczającego.|
|*Rect*|[w] Określa prostokąt ograniczający.|
|*bWybrany*|[w] Ignorowane.|
|*bWyświetlony*|[w] Ignorowane.|

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
