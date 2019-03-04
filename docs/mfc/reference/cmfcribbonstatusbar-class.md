---
title: CMFCRibbonStatusBar Class
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
ms.openlocfilehash: b927012f241c30b1beec23ff7e0bbc9e8302d8da
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287647"
---
# <a name="cmfcribbonstatusbar-class"></a>CMFCRibbonStatusBar Class

`CMFCRibbonStatusBar` Klasa implementuje formant paska stanu, który może wyświetlać elementy wstążki.

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
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|Dodaje element wstążki do rozszerzonego obszar paska stanu wstążki.|
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|Dodaje separator do paska stanu wstążki.|
|[CMFCRibbonStatusBar::Create](#create)|Tworzy paska stanu wstążki.|
|[CMFCRibbonStatusBar::CreateEx](#createex)|Tworzy paska stanu wstążki z rozszerzonego stylu.|
|[CMFCRibbonStatusBar::FindByID](#findbyid)||
|[CMFCRibbonStatusBar::FindElement](#findelement)|Zwraca wskaźnik do elementu, który ma identyfikator określonego polecenia.|
|[CMFCRibbonStatusBar::GetCount](#getcount)|Zwraca liczbę elementów, które znajdują się w głównym obszarze paska stanu wstążki.|
|[CMFCRibbonStatusBar::GetElement](#getelement)|Zwraca wskaźnik do elementu, który jest umieszczony pod określonym indeksem.|
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|Zwraca liczbę elementów, które znajdują się w obszarze rozszerzonego paska stanu wstążki.|
|[CMFCRibbonStatusBar::GetExElement](#getexelement)|Zwraca wskaźnik do elementu, który jest umieszczony pod określonym indeksem w obszarze rozszerzonego paska stanu wstążki.|
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCRibbonStatusBar::GetSpace](#getspace)||
|[CMFCRibbonStatusBar::IsBottomFrame](#isbottomframe)||
|[CMFCRibbonStatusBar::IsExtendedElement](#isextendedelement)||
|[CMFCRibbonStatusBar::IsInformationMode](#isinformationmode)|Określa, czy informacje o trybie jest włączona dla paska stanu wstążki.|
|[CMFCRibbonStatusBar::RecalcLayout](#recalclayout)|(Przesłania [CMFCRibbonBar::RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout).)|
|[CMFCRibbonStatusBar::RemoveAll](#removeall)|Usuwa wszystkie elementy z paska stanu wstążki.|
|[CMFCRibbonStatusBar::RemoveElement](#removeelement)|Usuwa element, który zawiera polecenie o określonym identyfikatorze z paska stanu wstążki.|
|[CMFCRibbonStatusBar::SetInformation](#setinformation)|Włącza lub wyłącza tryb informacji dla paska stanu wstążki.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonStatusBar::OnDrawInformation](#ondrawinformation)|Wyświetla ciąg informacji, który pojawia się na pasku kiedy jest włączony tryb informacji stanu wstążki.|

## <a name="remarks"></a>Uwagi

Użytkownicy mogą zmieniać widoczność elementów wstążki, paska stanu wstążki przy użyciu menu kontekstowego wbudowane dla paska stanu wstążki. Można dodawać lub dynamicznie usunąć elementy.

Paska stanu wstążki zawiera dwa obszary: główne obszary i rozszerzonej. Rozszerzone obszar jest wyświetlany po prawej stronie paska stanu Wstążki i pojawia się w innym kolorze niż obszaru głównego.

Zazwyczaj główny obszar na pasku stanu wyświetla powiadomienia o stanie oraz rozszerzone obszaru kontrolki widoku. Rozszerzone obszaru pozostaje widoczna tak długo, jak to możliwe po użytkownik zmienia rozmiar paska stanu wstążki.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak korzystać z różnych metod w `CMFCRibbonStatusBar` klasy. W przykładzie pokazano metodę dodać nowy element wstążki do paska stanu wstążki, Dodawanie elementu wstążki do rozszerzonego obszar paska stanu wstążki, dodaj separator i włączyć tryb regularne paska stanu wstążki.

[!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)

[CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribbonstatusbar.h

##  <a name="adddynamicelement"></a>  CMFCRibbonStatusBar::AddDynamicElement

Dodaje element dynamiczny do paska stanu wstążki.

```
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>Parametry

*pElement*<br/>
[in] Wskaźnik do elementu dynamicznych.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do regularnych elementy dynamiczne elementy nie są możliwe do dostosowania i dostosowywanie menu na pasku stanu te nie są wyświetlane.

##  <a name="addelement"></a>  CMFCRibbonStatusBar::AddElement

Dodaje nowy element wstążki do paska stanu wstążki.

```
void AddElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parametry

*pElement*<br/>
[in] Wskaźnik do dodanego elementu.

*lpszLabel*<br/>
[in] Etykieta tekstowa elementu.

*bIsVisible*<br/>
[in] Wartość TRUE, jeśli chcesz dodać element jako widoczny, FALSE, jeśli chcesz dodać element jako ukryty.

##  <a name="addextendedelement"></a>  CMFCRibbonStatusBar::AddExtendedElement

Dodaje element wstążki do rozszerzonego obszar paska stanu wstążki.

```
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parametry

*pElement*<br/>
[in] Wskaźnik do dodanego elementu.

*lpszLabel*<br/>
[in] Etykieta tekstowa elementu.

*bIsVisible*<br/>
[in] Wartość TRUE, jeśli chcesz dodać element jako widoczny, FALSE, jeśli chcesz dodać element jako ukryty.

### <a name="remarks"></a>Uwagi

Obszar rozszerzonej jest po prawej stronie formantu paska stanu.

##  <a name="addseparator"></a>  CMFCRibbonStatusBar::AddSeparator

Dodaje separator do paska stanu wstążki.

```
void AddSeparator();
```

### <a name="remarks"></a>Uwagi

Struktura dodaje separator po metodzie [CMFCRibbonStatusBar::AddElement](#addelement). Wstawia po ostatnim elemencie.

##  <a name="create"></a>  CMFCRibbonStatusBar::Create

Tworzy paska stanu wstążki.

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[in] Wskaźnik do okna nadrzędnego.

*dwStyle*<br/>
[in] Logiczne OR kombinację style kontrolki.

*nID*<br/>
[in] Identyfikator formantu paska stanu.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pasek stanu został utworzony pomyślnie, wartość FALSE w przeciwnym razie.

##  <a name="createex"></a>  CMFCRibbonStatusBar::CreateEx

Tworzy paska stanu wstążki, który ma rozszerzonego stylu.

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
Logiczne OR kombinację dodatkowe style do tworzenia obiektu pasek stanu.

*dwStyle*<br/>
Styl kontrolki na pasku stanu.

*nID*<br/>
Identyfikator formantu paska stanu.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pasek stanu został utworzony pomyślnie, wartość FALSE w przeciwnym razie.

##  <a name="findbyid"></a>  CMFCRibbonStatusBar::FindByID

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```

### <a name="parameters"></a>Parametry

[in] *uiCmdID*<br/>
[in] *BOOL*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="findelement"></a>  CMFCRibbonStatusBar::FindElement

Zwraca wskaźnik do elementu, który ma identyfikator określonego polecenia.

```
CMFCRibbonBaseElement* FindElement(UINT uiID);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[in] Identyfikator elementu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu, który ma identyfikator określonego polecenia. Wartość NULL, jeśli nie ma żadnego takiego elementu.

##  <a name="getcount"></a>  CMFCRibbonStatusBar::GetCount

Zwraca liczbę elementów, które znajdują się w głównym obszarze paska stanu wstążki.

```
int GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, które znajdują się w głównym obszarze paska stanu wstążki.

##  <a name="getelement"></a>  CMFCRibbonStatusBar::GetElement

Zwraca wskaźnik do elementu, który jest umieszczony pod określonym indeksem.

```
CMFCRibbonBaseElement* GetElement(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Określa liczony od zera indeks elementu, który znajduje się w głównym obszarze formantu paska stanu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu, który jest umieszczony pod określonym indeksem. Wartość NULL, jeśli indeks jest ujemny lub większa niż liczba elementów w pasku stanu.

### <a name="remarks"></a>Uwagi

##  <a name="getexcount"></a>  CMFCRibbonStatusBar::GetExCount

Zwraca liczbę elementów, które znajdują się w obszarze rozszerzonego paska stanu wstążki.

```
int GetExCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, które znajdują się w obszarze rozszerzonego paska stanu wstążki.

##  <a name="getexelement"></a>  CMFCRibbonStatusBar::GetExElement

Zwraca wskaźnik do elementu, który jest umieszczony pod określonym indeksem w obszarze rozszerzonego paska stanu wstążki. Obszar rozszerzonej jest po prawej stronie formantu paska stanu.

```
CMFCRibbonBaseElement* GetExElement(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Określa liczony od zera indeks elementu, który znajduje się w obszarze rozszerzonej formantu paska stanu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu, który jest umieszczony pod określonym indeksem w obszarze rozszerzonego paska stanu wstążki. Wartość NULL, jeśli *nIndex* jest ujemny lub większa niż liczba elementów w obszarze rozszerzonego paska stanu wstążki.

### <a name="remarks"></a>Uwagi

##  <a name="getextendedarea"></a>  CMFCRibbonStatusBar::GetExtendedArea

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

[in] *rect*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getspace"></a>  CMFCRibbonStatusBar::GetSpace

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
int GetSpace() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isbottomframe"></a>  CMFCRibbonStatusBar::IsBottomFrame

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
BOOL IsBottomFrame() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isextendedelement"></a>  CMFCRibbonStatusBar::IsExtendedElement

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;
```

### <a name="parameters"></a>Parametry

[in] *pElement*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isinformationmode"></a>  CMFCRibbonStatusBar::IsInformationMode

Określa, czy informacje o trybie jest włączona dla paska stanu wstążki.

```
BOOL IsInformationMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli na pasku stanu może pracować w trybie informacji; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

W trybie informacji na pasku stanu powoduje ukrycie wszystkich okienek regularnych i wyświetla ciąg komunikatu.

##  <a name="ondrawinformation"></a>  CMFCRibbonStatusBar::OnDrawInformation

Wyświetla ciąg, który pojawia się na pasku po włączeniu trybu informacji stanu wstążki.

```
virtual void OnDrawInformation(
    CDC* pDC,
    CString& strInfo,
    CRect rectInfo);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia.

*strInfo*<br/>
[in] Ciąg informacji.

*rectInfo*<br/>
[in] Prostokąt otaczający.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w klasie pochodnej, jeśli chcesz dostosować wygląd ciągu informacji na pasku stanu. Użyj [CMFCRibbonStatusBar::SetInformation](#setinformation) metodę, aby umieścić na pasku stanu w trybie informacji. W tym trybie, na pasku stanu polega na schowaniu wszystkich okienek i wyświetla ciąg informacji określone przez *strInfo*.

##  <a name="recalclayout"></a>  CMFCRibbonStatusBar::RecalcLayout

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Uwagi

##  <a name="removeall"></a>  CMFCRibbonStatusBar::RemoveAll

Usuwa wszystkie elementy z paska stanu wstążki.

```
void RemoveAll();
```

##  <a name="removeelement"></a>  CMFCRibbonStatusBar::RemoveElement

Usuwa element, który zawiera polecenie o określonym identyfikatorze z paska stanu wstążki.

```
BOOL RemoveElement(UINT uiID);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[in] Identyfikator elementu do usunięcia na pasku stanu.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli element z określonym *uiID* zostanie usunięty. Wartość FALSE w przeciwnym razie.

##  <a name="setinformation"></a>  CMFCRibbonStatusBar::SetInformation

Włącza lub wyłącza tryb informacji dla paska stanu wstążki.

```
void SetInformation(LPCTSTR lpszInfo);
```

### <a name="parameters"></a>Parametry

*lpszInfo*<br/>
[in] Ciąg informacji.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia umieszczanie paska stanu w trybie informacji. W tym trybie, na pasku stanu polega na schowaniu wszystkich okienek i wyświetla ciąg informacji określone przez *lpszInfo*.

Gdy lpszInfo ma wartość NULL, na pasku stanu powraca do trybu normalnego.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)<br/>
[Klasa CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
