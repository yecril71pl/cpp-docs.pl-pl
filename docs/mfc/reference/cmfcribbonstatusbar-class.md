---
title: Klasa CMFCRibbonStatusBar
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddDynamicElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddSeparator
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::Create
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::CreateEx
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindByID
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExtendedArea
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetSpace
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsBottomFrame
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsInformationMode
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RecalcLayout
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveAll
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::SetInformation
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::OnDrawInformation
helpviewer_keywords:
- CMFCRibbonStatusBar [MFC], AddDynamicElement
- CMFCRibbonStatusBar [MFC], AddElement
- CMFCRibbonStatusBar [MFC], AddExtendedElement
- CMFCRibbonStatusBar [MFC], AddSeparator
- CMFCRibbonStatusBar [MFC], Create
- CMFCRibbonStatusBar [MFC], CreateEx
- CMFCRibbonStatusBar [MFC], FindByID
- CMFCRibbonStatusBar [MFC], FindElement
- CMFCRibbonStatusBar [MFC], GetCount
- CMFCRibbonStatusBar [MFC], GetElement
- CMFCRibbonStatusBar [MFC], GetExCount
- CMFCRibbonStatusBar [MFC], GetExElement
- CMFCRibbonStatusBar [MFC], GetExtendedArea
- CMFCRibbonStatusBar [MFC], GetSpace
- CMFCRibbonStatusBar [MFC], IsBottomFrame
- CMFCRibbonStatusBar [MFC], IsExtendedElement
- CMFCRibbonStatusBar [MFC], IsInformationMode
- CMFCRibbonStatusBar [MFC], RecalcLayout
- CMFCRibbonStatusBar [MFC], RemoveAll
- CMFCRibbonStatusBar [MFC], RemoveElement
- CMFCRibbonStatusBar [MFC], SetInformation
- CMFCRibbonStatusBar [MFC], OnDrawInformation
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
ms.openlocfilehash: 8d90e01db022c33edd654e83af05e9986799f2b9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754058"
---
# <a name="cmfcribbonstatusbar-class"></a>Klasa CMFCRibbonStatusBar

Klasa `CMFCRibbonStatusBar` implementuje formant paska stanu, który może wyświetlać elementy wstążki.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonStatusBar : public CMFCRibbonBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonStatusBar::AddDynamicElement](#adddynamicelement)|Dodaje element dynamiczny do paska stanu wstążki.|
|[CMFCRibbonStatusBar::AddElement](#addelement)|Dodaje nowy element wstążki do paska stanu wstążki.|
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|Dodaje element wstążki do rozszerzonego obszaru paska stanu wstążki.|
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|Dodaje separator do paska stanu wstążki.|
|[CMFCRibbonStatusBar::Tworzenie](#create)|Tworzy pasek stanu wstążki.|
|[CMFCRibbonStatusBar::CreateEx](#createex)|Tworzy pasek stanu wstążki z rozszerzonym stylem.|
|[CMFCRibbonStatusBar::FindByID](#findbyid)||
|[CMFCRibbonStatusBar::FindElement](#findelement)|Zwraca wskaźnik do elementu, który ma określony identyfikator polecenia.|
|[CMFCRibbonStatusBar::GetCount](#getcount)|Zwraca liczbę elementów znajdujących się w głównym obszarze paska stanu wstążki.|
|[CMFCRibbonStatusBar::GetElement](#getelement)|Zwraca wskaźnik do elementu, który znajduje się w określonym indeksie.|
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|Zwraca liczbę elementów, które znajdują się w rozszerzonym obszarze paska stanu wstążki.|
|[CMFCRibbonStatusBar::GetExElement](#getexelement)|Zwraca wskaźnik do elementu, który znajduje się przy określonym indeksie w rozszerzonym obszarze paska stanu wstążki.|
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCRibbonStatusBar::GetSpace](#getspace)||
|[CMFCRibbonStatusBar::IsBottomFrame](#isbottomframe)||
|[CMFCRibbonStatusBar::IsExtendedElement](#isextendedelement)||
|[CMFCRibbonStatusBar::IsInformationMode](#isinformationmode)|Określa, czy tryb informacyjny jest włączony dla paska stanu wstążki.|
|[CMFCRibbonStatusBar::RecalcLayout](#recalclayout)|(Zastępuje [CMFCRibbonBar::RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout).)|
|[CMFCRibbonStatusBar::UsuńWszystki](#removeall)|Usuwa wszystkie elementy z paska stanu wstążki.|
|[CMFCRibbonStatusBar::UsuńElement](#removeelement)|Usuwa element o określonym identyfikatorze polecenia z paska stanu wstążki.|
|[CMFCRibbonStatusBar::SetInformation](#setinformation)|Włącza lub wyłącza tryb informacyjny paska stanu wstążki.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonStatusBar::OnDrawInformation](#ondrawinformation)|Wyświetla ciąg informacji wyświetlany na pasku stanu wstążki po włączeniu trybu informacyjnego.|

## <a name="remarks"></a>Uwagi

Użytkownicy mogą zmieniać widoczność elementów wstążki na pasku stanu wstążki za pomocą wbudowanego menu kontekstowego paska stanu wstążki. Elementy można dodawać lub usuwać dynamicznie.

Pasek stanu wstążki ma dwa obszary: główny obszar i obszar rozszerzony. Rozszerzony obszar jest wyświetlany po prawej stronie paska stanu wstążki i jest wyświetlany w innym kolorze niż główny obszar.

Zazwyczaj w głównym obszarze paska stanu są wyświetlane powiadomienia o stanie, a w rozszerzonym obszarze są wyświetlane formanty widoku. Rozszerzony obszar pozostaje widoczny tak długo, jak to możliwe, gdy użytkownik zmieni rozmiar paska stanu wstążki.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCRibbonStatusBar` używać różnych metod w klasie. W przykładzie pokazano, jak dodać nowy element wstążki do paska stanu wstążki, dodać element wstążki do rozszerzonego obszaru paska stanu wstążki, dodać separator i włączyć tryb normalny paska stanu wstążki.

[!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Panel CBasePane](../../mfc/reference/cbasepane-class.md)

[Cpane](../../mfc/reference/cpane-class.md)

[Cmfcribbonbar](../../mfc/reference/cmfcribbonbar-class.md)

[CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribbonstatusbar.h

## <a name="cmfcribbonstatusbaradddynamicelement"></a><a name="adddynamicelement"></a>CMFCRibbonStatusBar::AddDynamicElement

Dodaje element dynamiczny do paska stanu wstążki.

```cpp
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>Parametry

*pElement (właśc.*<br/>
[w] Wskaźnik do elementu dynamicznego.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do zwykłych elementów, elementy dynamiczne nie są konfigurowalne, a menu dostosowywania paska stanu nie wyświetla ich.

## <a name="cmfcribbonstatusbaraddelement"></a><a name="addelement"></a>CMFCRibbonStatusBar::AddElement

Dodaje nowy element wstążki do paska stanu wstążki.

```cpp
void AddElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parametry

*pElement (właśc.*<br/>
[w] Wskaźnik do dodanego elementu.

*lpszLabel (lpszLabel)*<br/>
[w] Etykieta tekstowa elementu.

*bIsVisible (Widoczne)*<br/>
[w] PRAWDA, jeśli chcesz dodać element jako widoczny, FALSE, jeśli chcesz dodać element jako ukryty.

## <a name="cmfcribbonstatusbaraddextendedelement"></a><a name="addextendedelement"></a>CMFCRibbonStatusBar::AddExtendedElement

Dodaje element wstążki do rozszerzonego obszaru paska stanu wstążki.

```cpp
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parametry

*pElement (właśc.*<br/>
[w] Wskaźnik do dodanego elementu.

*lpszLabel (lpszLabel)*<br/>
[w] Etykieta tekstowa elementu.

*bIsVisible (Widoczne)*<br/>
[w] PRAWDA, jeśli chcesz dodać element jako widoczny, FALSE, jeśli chcesz dodać element jako ukryty.

### <a name="remarks"></a>Uwagi

Rozszerzony obszar znajduje się po prawej stronie kontrolki paska stanu.

## <a name="cmfcribbonstatusbaraddseparator"></a><a name="addseparator"></a>CMFCRibbonStatusBar::AddSeparator

Dodaje separator do paska stanu wstążki.

```cpp
void AddSeparator();
```

### <a name="remarks"></a>Uwagi

Struktura dodaje separator po metodzie [CMFCRibbonStatusBar::AddElement](#addelement). wstawia ostatni element.

## <a name="cmfcribbonstatusbarcreate"></a><a name="create"></a>CMFCRibbonStatusBar::Tworzenie

Tworzy pasek stanu wstążki.

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[w] Wskaźnik do okna nadrzędnego.

*Dwstyle*<br/>
[w] Logiczna kombinacja stylów sterowania lub.

*Nid*<br/>
[w] Identyfikator formantu paska stanu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli pasek stanu został utworzony pomyślnie, w przeciwnym razie WARTOŚĆ FAŁSZUj.

## <a name="cmfcribbonstatusbarcreateex"></a><a name="createex"></a>CMFCRibbonStatusBar::CreateEx

Tworzy pasek stanu wstążki o rozszerzonym stylu.

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle=0,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego.

*dwCtrlStyle*<br/>
Logiczna kombinacja lub dodatkowych stylów do tworzenia obiektu paska stanu.

*Dwstyle*<br/>
Styl sterowania paska stanu.

*Nid*<br/>
Identyfikator formantu paska stanu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli pasek stanu został utworzony pomyślnie, w przeciwnym razie WARTOŚĆ FAŁSZUj.

## <a name="cmfcribbonstatusbarfindbyid"></a><a name="findbyid"></a>CMFCRibbonStatusBar::FindByID

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```

### <a name="parameters"></a>Parametry

[w] *identyfikator uiCmdID*<br/>
[w] *BOOL (BOOL)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonstatusbarfindelement"></a><a name="findelement"></a>CMFCRibbonStatusBar::FindElement

Zwraca wskaźnik do elementu, który ma określony identyfikator polecenia.

```
CMFCRibbonBaseElement* FindElement(UINT uiID);
```

### <a name="parameters"></a>Parametry

*Uiid*<br/>
[w] Identyfikator elementu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu, który ma określony identyfikator polecenia. NULL, jeśli nie ma takiego elementu.

## <a name="cmfcribbonstatusbargetcount"></a><a name="getcount"></a>CMFCRibbonStatusBar::GetCount

Zwraca liczbę elementów znajdujących się w głównym obszarze paska stanu wstążki.

```
int GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów znajdujących się w głównym obszarze paska stanu wstążki.

## <a name="cmfcribbonstatusbargetelement"></a><a name="getelement"></a>CMFCRibbonStatusBar::GetElement

Zwraca wskaźnik do elementu, który znajduje się w określonym indeksie.

```
CMFCRibbonBaseElement* GetElement(int nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
[w] Określa indeks od zera elementu, który znajduje się w głównym obszarze formantu paska stanu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu, który znajduje się w określonym indeksie. NULL, jeśli indeks jest ujemny lub przekracza liczbę elementów na pasku stanu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonstatusbargetexcount"></a><a name="getexcount"></a>CMFCRibbonStatusBar::GetExCount

Zwraca liczbę elementów, które znajdują się w rozszerzonym obszarze paska stanu wstążki.

```
int GetExCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów znajdujących się w rozszerzonym obszarze paska stanu wstążki.

## <a name="cmfcribbonstatusbargetexelement"></a><a name="getexelement"></a>CMFCRibbonStatusBar::GetExElement

Zwraca wskaźnik do elementu, który znajduje się przy określonym indeksie w rozszerzonym obszarze paska stanu wstążki. Rozszerzony obszar znajduje się po prawej stronie kontrolki paska stanu.

```
CMFCRibbonBaseElement* GetExElement(int nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
[w] Określa indeks od zera elementu, który znajduje się w rozszerzonym obszarze formantu paska stanu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu, który znajduje się przy określonym indeksie w rozszerzonym obszarze paska stanu wstążki. NULL, jeśli *nIndex* jest ujemny lub przekracza liczbę elementów w rozszerzonym obszarze paska stanu wstążki.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFCRibbonStatusBar::GetExtendedArea

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

[w] *rect*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonstatusbargetspace"></a><a name="getspace"></a>CMFCRibbonStatusBar::GetSpace

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
int GetSpace() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonstatusbarisbottomframe"></a><a name="isbottomframe"></a>CMFCRibbonStatusBar::IsBottomFrame

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
BOOL IsBottomFrame() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonstatusbarisextendedelement"></a><a name="isextendedelement"></a>CMFCRibbonStatusBar::IsExtendedElement

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;
```

### <a name="parameters"></a>Parametry

[w] *pElement (właśc.*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonstatusbarisinformationmode"></a><a name="isinformationmode"></a>CMFCRibbonStatusBar::IsInformationMode

Określa, czy tryb informacyjny jest włączony dla paska stanu wstążki.

```
BOOL IsInformationMode() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli pasek stanu może działać w trybie informacyjnym; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

W trybie informacyjnym pasek stanu ukrywa wszystkie zwykłe okienka i wyświetla ciąg komunikatu.

## <a name="cmfcribbonstatusbarondrawinformation"></a><a name="ondrawinformation"></a>CMFCRibbonStatusBar::OnDrawInformation

Wyświetla ciąg wyświetlany na pasku stanu wstążki, gdy włączony jest tryb informacyjny.

```
virtual void OnDrawInformation(
    CDC* pDC,
    CString& strInfo,
    CRect rectInfo);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*strInfo (strInfo)*<br/>
[w] Ciąg informacyjny.

*rectInfo*<br/>
[w] Prostokąt ograniczający.

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, jeśli chcesz dostosować wygląd ciągu informacji na pasku stanu. Użyj [CMFCRibbonStatusBar::SetInformation](#setinformation) metody umieścić pasek stanu w trybie informacyjnym. W tym trybie pasek stanu ukrywa wszystkie okienka i wyświetla ciąg informacji określony przez *strInfo*.

## <a name="cmfcribbonstatusbarrecalclayout"></a><a name="recalclayout"></a>CMFCRibbonStatusBar::RecalcLayout

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonstatusbarremoveall"></a><a name="removeall"></a>CMFCRibbonStatusBar::UsuńWszystki

Usuwa wszystkie elementy z paska stanu wstążki.

```cpp
void RemoveAll();
```

## <a name="cmfcribbonstatusbarremoveelement"></a><a name="removeelement"></a>CMFCRibbonStatusBar::UsuńElement

Usuwa element o określonym identyfikatorze polecenia z paska stanu wstążki.

```
BOOL RemoveElement(UINT uiID);
```

### <a name="parameters"></a>Parametry

*Uiid*<br/>
[w] Identyfikator elementu do usunięcia z paska stanu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli element o określonym *identyfikatorze użytkownika* zostanie usunięty. FAŁSZ inaczej.

## <a name="cmfcribbonstatusbarsetinformation"></a><a name="setinformation"></a>CMFCRibbonStatusBar::SetInformation

Włącza lub wyłącza tryb informacyjny paska stanu wstążki.

```cpp
void SetInformation(LPCTSTR lpszInfo);
```

### <a name="parameters"></a>Parametry

*lpszInfo*<br/>
[w] Ciąg informacyjny.

### <a name="remarks"></a>Uwagi

Ta metoda służy do umieszczania paska stanu w trybie informacyjnym. W tym trybie pasek stanu ukrywa wszystkie okienka i wyświetla ciąg informacji określony przez *lpszInfo*.

Gdy lpszInfo jest NULL, pasek stanu powraca do trybu regularnego.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)<br/>
[Klasa CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
