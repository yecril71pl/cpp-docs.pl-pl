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
ms.openlocfilehash: de2c6c45e4a91aa4efa0ebacba4019be74e03c72
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560871"
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
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|Konstruuje `CMFCRibbonSeparator` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|Dodaje separator do listy **poleceń** w oknie dialogowym **Dostosuj** . (Przesłania [CMFCRibbonBaseElement:: AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|
|`CMFCRibbonSeparator::CreateObject`|Używane przez platformę do tworzenia wystąpienia dynamicznego tego typu klasy.|
|`CMFCRibbonSeparator::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|

### <a name="protected-methods"></a>Metody chronione

|||
|-|-|
|Nazwa|Opis|
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|Metoda kopiowania, która ustawia zmienne składowe separatora z innego obiektu.|
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|Zwraca rozmiar separatora.|
|[CMFCRibbonSeparator:: IsSeparator](#isseparator)|Wskazuje, czy ten element jest separatorem.|
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|Wskazuje, czy jest to tabulator tabulator.|
|[CMFCRibbonSeparator:: OnDraw](#ondraw)|Wywoływane przez system, aby narysować separator na Wstążce lub pasku narzędzi Szybki dostęp.|
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|Wywoływane przez system, aby narysować separator na liście **poleceń** .|

## <a name="remarks"></a>Uwagi

Separator wstążki to pionowa lub pozioma linia, która logicznie oddziela elementy wstążki. Separator może być rysowany w kontrolce wstążki, menu główne aplikacja, pasek stanu wstążki i pasek narzędzi Szybki dostęp.

Aby użyć separatora w aplikacji, Utwórz nowy obiekt i dodaj go do głównego menu aplikacji, jak pokazano poniżej:

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```

Wywołaj [CMFCRibbonPanel:: AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) , aby dodać separatory do paneli wstążki. Separatory są przydzielone i dodawane wewnętrznie przez `AddSeparator` metodę.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxbaseribbonelement. h

## <a name="cmfcribbonseparatoraddtolistbox"></a><a name="addtolistbox"></a> CMFCRibbonSeparator::AddToListBox

Dodaje separator do listy **poleceń** w oknie dialogowym **Dostosuj** .

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>Parametry

*pWndListBox*<br/>
podczas Wskaźnik do listy **poleceń** , gdzie zostanie dodany separator.

*bDeep*<br/>
podczas Ignoruj.

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) do ciągu w polu listy określonym przez *pWndListBox*.

## <a name="cmfcribbonseparatorcmfcribbonseparator"></a><a name="cmfcribbonseparator"></a> CMFCRibbonSeparator::CMFCRibbonSeparator

Konstruuje `CMFCRibbonSeparator` obiekt.

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>Parametry

*bIsHoriz*<br/>
podczas W przypadku wartości TRUE separator jest poziomy. w przypadku wartości FALSE separator jest pionowy.

### <a name="remarks"></a>Uwagi

Separatory poziome są używane w menu aplikacji. Separatory pionowe są używane w paskach narzędzi.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konstruowania obiektu `CMFCRibbonSeparator` klasy.

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

## <a name="cmfcribbonseparatorcopyfrom"></a><a name="copyfrom"></a> CMFCRibbonSeparator::CopyFrom

Metoda kopiowania, która ustawia zmienne składowe separatora z innego obiektu.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parametry

*SRC*<br/>
podczas Źródłowy element wstążki, z którego mają zostać skopiowane.

## <a name="cmfcribbonseparatorgetregularsize"></a><a name="getregularsize"></a> CMFCRibbonSeparator::GetRegularSize

Zwraca rozmiar separatora.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskaźnik do zawartości urządzenia.

### <a name="return-value"></a>Wartość zwracana

Rozmiar separatora w danym kontekście urządzenia.

## <a name="cmfcribbonseparatorisseparator"></a><a name="isseparator"></a> CMFCRibbonSeparator:: IsSeparator

Wskazuje, czy ten element jest separatorem.

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze TRUE dla tej klasy.

## <a name="cmfcribbonseparatoristabstop"></a><a name="istabstop"></a> CMFCRibbonSeparator::IsTabStop

Wskazuje, czy jest to tabulator tabulator.

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze wartość FALSE dla tej klasy.

### <a name="remarks"></a>Uwagi

Separator wstążki nie jest tabulatorem.

## <a name="cmfcribbonseparatorondraw"></a><a name="ondraw"></a> CMFCRibbonSeparator:: OnDraw

Wywoływane przez system, aby narysować separator na Wstążce lub pasku narzędzi Szybki dostęp.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskaźnik do kontekstu urządzenia.

## <a name="cmfcribbonseparatorondrawonlist"></a><a name="ondrawonlist"></a> CMFCRibbonSeparator::OnDrawOnList

Wywoływane przez system, aby narysować separator na liście **poleceń** .

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

*Domeny*\
podczas Wskaźnik do kontekstu urządzenia.

*strText*\
podczas Tekst wyświetlany na liście.

*nTextOffset*\
podczas Odstępy między tekstem a lewą krawędzią prostokąta ograniczenia.

*cinania*\
podczas Określa prostokąt ograniczający.

*bIsSelected*\
podczas Ignoruj.

*bHighlighted*\
podczas Ignoruj.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
