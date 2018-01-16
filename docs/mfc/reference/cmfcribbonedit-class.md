---
title: Klasa CMFCRibbonEdit | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CanBeStretched
- AFXRIBBONEDIT/CMFCRibbonEdit::CopyFrom
- AFXRIBBONEDIT/CMFCRibbonEdit::CreateEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::DestroyCtrl
- AFXRIBBONEDIT/CMFCRibbonEdit::DropDownList
- AFXRIBBONEDIT/CMFCRibbonEdit::EnableSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::GetCompactSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::GetIntermediateSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::GetWidth
- AFXRIBBONEDIT/CMFCRibbonEdit::HasCompactMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasFocus
- AFXRIBBONEDIT/CMFCRibbonEdit::HasLargeMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::IsHighlighted
- AFXRIBBONEDIT/CMFCRibbonEdit::OnAfterChangeRect
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDraw
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawLabelAndImage
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawOnList
- AFXRIBBONEDIT/CMFCRibbonEdit::OnEnable
- AFXRIBBONEDIT/CMFCRibbonEdit::OnHighlight
- AFXRIBBONEDIT/CMFCRibbonEdit::OnKey
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonDown
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonUp
- AFXRIBBONEDIT/CMFCRibbonEdit::OnRTLChanged
- AFXRIBBONEDIT/CMFCRibbonEdit::OnShow
- AFXRIBBONEDIT/CMFCRibbonEdit::Redraw
- AFXRIBBONEDIT/CMFCRibbonEdit::SetACCData
- AFXRIBBONEDIT/CMFCRibbonEdit::SetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::SetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::SetWidth
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CanBeStretched
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CopyFrom
- CMFCRibbonEdit [MFC], CreateEdit
- CMFCRibbonEdit [MFC], DestroyCtrl
- CMFCRibbonEdit [MFC], DropDownList
- CMFCRibbonEdit [MFC], EnableSpinButtons
- CMFCRibbonEdit [MFC], GetCompactSize
- CMFCRibbonEdit [MFC], GetEditText
- CMFCRibbonEdit [MFC], GetIntermediateSize
- CMFCRibbonEdit [MFC], GetTextAlign
- CMFCRibbonEdit [MFC], GetWidth
- CMFCRibbonEdit [MFC], HasCompactMode
- CMFCRibbonEdit [MFC], HasFocus
- CMFCRibbonEdit [MFC], HasLargeMode
- CMFCRibbonEdit [MFC], HasSpinButtons
- CMFCRibbonEdit [MFC], IsHighlighted
- CMFCRibbonEdit [MFC], OnAfterChangeRect
- CMFCRibbonEdit [MFC], OnDraw
- CMFCRibbonEdit [MFC], OnDrawLabelAndImage
- CMFCRibbonEdit [MFC], OnDrawOnList
- CMFCRibbonEdit [MFC], OnEnable
- CMFCRibbonEdit [MFC], OnHighlight
- CMFCRibbonEdit [MFC], OnKey
- CMFCRibbonEdit [MFC], OnLButtonDown
- CMFCRibbonEdit [MFC], OnLButtonUp
- CMFCRibbonEdit [MFC], OnRTLChanged
- CMFCRibbonEdit [MFC], OnShow
- CMFCRibbonEdit [MFC], Redraw
- CMFCRibbonEdit [MFC], SetACCData
- CMFCRibbonEdit [MFC], SetEditText
- CMFCRibbonEdit [MFC], SetTextAlign
- CMFCRibbonEdit [MFC], SetWidth
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 43a497b3eeec48c22d688f4974efcb3d2f511446
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonedit-class"></a>Klasa CMFCRibbonEdit
Implementuje kontrolki edycji, który znajduje się na pasku wstążki.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonEdit : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Konstruuje `CMFCRibbonEdit` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Wskazuje, czy wysokość `CMFCRibbonEdit` kontroli wzrasta w pionie wysokość wiersza wstążki.|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Konstruuje `CMFCRibbonEdit` obiektu.|  
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Kopiuje określony stan `CMFCRibbonEdit` obiektu do bieżącego `CMFCRibbonEdit` obiektu.|  
|[CMFCRibbonEdit::CreateEdit](#createedit)|Tworzy nowe pole tekstowe dla `CMFCRibbonEdit` obiektu.|  
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|Niszczy `CMFCRibbonEdit` obiektu.|  
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Rozwijana pola listy.|  
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Włącza i ustawia zakres pokrętła dla pola tekstowego.|  
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Pobiera rozmiar compact `CFMCRibbonEdit` obiektu.|  
|[CMFCRibbonEdit::GetEditText](#getedittext)|Pobiera tekst w polu tekstowym.|  
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Pobiera rozmiar pośredniego `CMFCRibbonEdit` obiektu.|  
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|Pobiera wyrównanie tekstu w polu tekstowym.|  
|[CMFCRibbonEdit::GetWidth](#getwidth)|Pobiera szerokość w pikselach, o `CMFCRibbonEdit` formantu.|  
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Wskazuje, czy rozmiar wyświetlania `CMFCRibbonEdit` formant może być compact.|  
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Wskazuje, czy `CMFCRIbbonEdit` formant ma fokus.|  
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Wskazuje, czy rozmiar wyświetlania `CMFCRibbonEdit` formant może być duży.|  
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Wskazuje, czy pole ma pokrętła.|  
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|Wskazuje, czy `CMFCRibbonEdit` formantu zostanie wyróżniona.|  
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Wywoływane przez platformę, gdy wymiary prostokątny obszar wyświetlania dla `CMFCRibbonEdit` kontroli zmian.|  
|[CMFCRibbonEdit::OnDraw](#ondraw)|Wywoływane przez platformę, by narysować `CMFCRibbonEdit` formantu.|  
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Wywoływane przez platformę, by narysować etykiety i obraz dla `CMFCRibbonEdit` formantu.|  
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|Wywoływane przez platformę, by narysować `CMFCRibbonEdit` kontroli w polu listy poleceń.|  
|[CMFCRibbonEdit::OnEnable](#onenable)|Wywoływane przez platformę, aby włączyć lub wyłączyć `CMFCRibbonEdit` formantu.|  
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|Wywoływane przez platformę, gdy wskaźnik wchodzi lub opuszczeniu granic `CMFCRibbonEdit` formantu.|  
|[CMFCRibbonEdit::OnKey](#onkey)|Wywoływane przez platformę, gdy użytkownik naciśnie właściwości keytip i `CMFCRibbonEdit` formant ma fokus.|  
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Wywoływane przez platformę, aby zaktualizować `CMFCRibbonEdit` kontroli, gdy użytkownik naciśnie lewego przycisku myszy w formancie.|  
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Wywoływane przez platformę, gdy użytkownik zwalnia lewego przycisku myszy.|  
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Wywoływane przez platformę, aby zaktualizować `CMFCRibbonEdit` kontrolować zmianie kierunku układu.|  
|[CMFCRibbonEdit::OnShow](#onshow)|Wywoływane przez platformę, by pokazać lub ukryć `CMFCRibbonEdit` formantu.|  
|[CMFCRibbonEdit::Redraw](#redraw)|Aktualizuje wyświetlanie `CMFCRibbonEdit` formantu.|  
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Ustawia dane ułatwień dostępu dla `CMFCRibbonEdit` obiektu.|  
|[CMFCRibbonEdit::SetEditText](#setedittext)|Ustawia tekst w polu tekstowym.|  
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Określa wyrównanie tekstu w polu tekstowym.|  
|[CMFCRibbonEdit::SetWidth](#setwidth)|Ustawia szerokość pola tekstowego do `CMFCRibbonEdit` formantu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCRibbonEdit` obiektów, wyświetlanie przycisków pokręteł obok kontrolki edycji i Ustaw tekst formantu edycyjnego. Następujący fragment kodu jest częścią [próbka MS Office 2007 Demo](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxRibbonEdit.h  
  
##  <a name="canbestretched"></a>CMFCRibbonEdit::CanBeStretched  
 Wskazuje, czy wysokość [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli wzrasta w pionie wysokość wiersza wstążki.  
  
```  
virtual BOOL CanBeStretched();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="cmfcribbonedit"></a>CMFCRibbonEdit::CMFCRibbonEdit  
 Konstruuje [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu.  
  
```  
CMFCRibbonEdit(
    UINT nID,  
    int nWidth,  
    LPCTSTR lpszLabel = NULL,  
    int nImage = -1);

CMFCRibbonEdit();
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nID`  
 Identyfikator dla polecenia `CMFCRibbonEdit` formantu.  
  
 [in]`nWidth`  
 Szerokość w pikselach pole tekstowe `CMFCRibbonEdit` formantu.  
  
 [in]`lpszLabel`  
 Etykieta dla `CMFCRibbonEdit` formantu.  
  
 [in]`nImage`  
 Indeks mały obraz do użycia na potrzeby `CMFCRibbonEdit` formantu. Kolekcja małe obrazy są obsługiwane przez kategoria wstążki nadrzędnego.  
  
### <a name="remarks"></a>Uwagi  
 `CMFCRibbonEdit` Formantu nie używa duży obraz.  
  
##  <a name="copyfrom"></a>CMFCRibbonEdit::CopyFrom  
 Kopiuje określony stan [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu do bieżącego [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu.  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`src`  
 Źródło `CMFCRibbonEdit` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `src` Parametr musi być typu `CMFCRibbonEdit`.  
  
##  <a name="createedit"></a>CMFCRibbonEdit::CreateEdit  
 Tworzy nowe pole tekstowe dla [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu.  
  
```  
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWndParent`  
 Wskaźnik do okna nadrzędnego `CMFCRibbonEdit` obiektu.  
  
 [in]`dwEditStyle`  
 Określa styl pola tekstowego. Style okna wymienione w sekcji uwag z można łączyć [style formantu edycji](http://msdn.microsoft.com/library/windows/desktop/bb775464) opisano w zestawie SDK systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowego pola tekstowego, jeśli metoda zakończyło się pomyślnie; w przeciwnym razie `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej, aby utworzyć niestandardowe pole tekstowe.  
  
 Należy zastosować następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) do pola tekstowego:  
  
- **WS_CHILD —**  
  
- **WS_VISIBLE —**  
  
- **WS_DISABLED —**  
  
- **WS_GROUP —**  
  
- **WS_TABSTOP —**  
  
##  <a name="destroyctrl"></a>CMFCRibbonEdit::DestroyCtrl  
 Niszczy [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu.  
  
```  
virtual void DestroyCtrl();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="dropdownlist"></a>CMFCRibbonEdit::DropDownList  
 Rozwijana pola listy.  
  
```  
virtual void DropDownList();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda nie działa. Zastępuje tę metodę do listy rozwijanej pola listy.  
  
##  <a name="enablespinbuttons"></a>CMFCRibbonEdit::EnableSpinButtons  
 Włącza i ustawia zakres pokrętła dla pola tekstowego.  
  
```  
void EnableSpinButtons(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nMin`  
 Wartość minimalna przycisku pokrętła.  
  
 [in]`nMax`  
 Maksymalna wartość przycisku pokrętła.  
  
### <a name="remarks"></a>Uwagi  
 Przycisków pokręteł Wyświetl w górę i Strzałka w dół i umożliwić użytkownikom przechodzenie między ustalony zbiór wartości.  
  
##  <a name="getcompactsize"></a>CMFCRibbonEdit::GetCompactSize  
 Pobiera rozmiar compact [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu.  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia dla `CMFCRibbonEdit` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar compact `CMFCRibbonEdit` obiektu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getedittext"></a>CMFCRibbonEdit::GetEditText  
 Pobiera tekst w polu tekstowym.  
  
```  
CString GetEditText() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Tekst w polu tekstowym.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getintermediatesize"></a>CMFCRibbonEdit::GetIntermediateSize  
 Pobiera rozmiar pośredniego [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia dla `CMFCRibbonEdit` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar pośredniego `CMFCRibbonEdit` obiektu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gettextalign"></a>CMFCRibbonEdit::GetTextAlign  
 Pobiera wyrównanie tekstu w polu tekstowym.  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wyrównanie tekstu wyliczyć wartość. W sekcji uwag możliwych wartości.  
  
### <a name="remarks"></a>Uwagi  
 Zwrócona wartość jest jednym z następujących stylów formantu edycji:  
  
- **Es_left —** dla wyrównania do lewej  
  
- **Es_center —** center wyrównania  
  
- **Es_right —** dla wyrównanie do prawej  
  
 Aby uzyskać więcej informacji o tych stylów, zobacz [edytowania stylów formantu](http://msdn.microsoft.com/library/windows/desktop/bb775464).  
  
##  <a name="getwidth"></a>CMFCRibbonEdit::GetWidth  
 Pobiera szerokość w pikselach, o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formantu.  
  
```  
int GetWidth(BOOL bInFloatyMode = FALSE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bInFloatyMode`  
 `TRUE`Jeśli `CMFCRibbonEdit` formant jest w trybie przestawne; w przeciwnym razie `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość w pikselach, o `CMFCRibbonEdit` formantu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="hascompactmode"></a>CMFCRibbonEdit::HasCompactMode  
 Wskazuje, czy rozmiar wyświetlania [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formant może być compact.  
  
```  
virtual BOOL HasCompactMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda zawsze zwraca wartość `TRUE`. Zastępuje tę metodę, aby wskazać, czy rozmiar wyświetlania można compact.  
  
##  <a name="hasfocus"></a>CMFCRibbonEdit::HasFocus  
 Wskazuje, czy [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formant ma fokus.  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli `CMFCRibbonEdit` formant ma fokus; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="haslargemode"></a>CMFCRibbonEdit::HasLargeMode  
 Wskazuje, czy rozmiar wyświetlania [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formant może być duży.  
  
```  
virtual BOOL HasLargeMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda zawsze zwraca wartość `FALSE`. Zastępuje tę metodę, aby wskazać, czy rozmiar wyświetlania może być duży.  
  
##  <a name="hasspinbuttons"></a>CMFCRibbonEdit::HasSpinButtons  
 Wskazuje, czy pole ma pokrętła.  
  
```  
virtual BOOL HasSpinButtons() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli pole ma pokrętła; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ishighlighted"></a>CMFCRibbonEdit::IsHighlighted  
 Wskazuje, czy [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formantu zostanie wyróżniona.  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli `CMFCRibbonEdit` formant jest zaznaczony, a w przeciwnym `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onafterchangerect"></a>CMFCRibbonEdit::OnAfterChangeRect  
 Wywoływane przez platformę, gdy wymiary prostokątny obszar wyświetlania dla [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli zmian.  
  
```  
virtual void OnAfterChangeRect(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia dla `CMFCRibbonEdit` formantu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ondraw"></a>CMFCRibbonEdit::OnDraw  
 Wywoływane przez platformę, by narysować [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formantu.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia dla `CMFCRibbonEdit` formantu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ondrawlabelandimage"></a>CMFCRibbonEdit::OnDrawLabelAndImage  
 Wywoływane przez platformę, by narysować etykiety i obrazów do [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formantu.  
  
```  
virtual void OnDrawLabelAndImage(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia dla `CMFCRibbonEdit` formantu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ondrawonlist"></a>CMFCRibbonEdit::OnDrawOnList  
 Wywoływane przez platformę, by narysować [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli w polu listy poleceń.  
  
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
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia dla `CMFCRibbonEdit` formantu.  
  
 [in]`strText`  
 Wyświetlany tekst [](../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit klasy").  
  
 [in]`nTextOffset`  
 Odległość w pikselach, po lewej stronie pola listy do wyświetlania tekstu.  
  
 [in]`rect`  
 Prostokątny obszar wyświetlania dla `CMFCRibbonEdit` formantu.  
  
 [in]`bIsSelected`  
 Ten parametr nie jest używany.  
  
 [in]`bHighlighted`  
 Ten parametr nie jest używany.  
  
### <a name="remarks"></a>Uwagi  
 Pole listy poleceń Wyświetla formantów wstążki, aby umożliwić użytkownikom Dostosuj pasek narzędzi Szybki dostęp.  
  
##  <a name="onenable"></a>CMFCRibbonEdit::OnEnable  
 Wywoływane przez platformę, aby włączyć lub wyłączyć [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formantu.  
  
```  
virtual void OnEnable(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 `TRUE`Aby włączyć kontrolę; `FALSE` wyłączyć formant.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onhighlight"></a>CMFCRibbonEdit::OnHighlight  
 Wywoływane przez platformę, gdy wskaźnik wchodzi lub opuszczeniu granic [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formantu.  
  
```  
virtual void OnHighlight(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bHighlight`  
 `TRUE`Jeśli wskaźnik jest w zakresie `CMFCRibbonEdit` kontrolować; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onkey"></a>CMFCRibbonEdit::OnKey  
 Wywoływane przez platformę, gdy użytkownik naciśnie właściwości keytip i [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formant ma fokus.  
  
```  
virtual BOOL OnKey(BOOL bIsMenuKey);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bIsMenuKey`  
 `TRUE`Jeśli właściwości keytip Wyświetla menu podręczne; w przeciwnym razie `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli zdarzenie zostało obsłużone; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onlbuttondown"></a>CMFCRibbonEdit::OnLButtonDown  
 Wywoływane przez platformę, aby zaktualizować [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli, gdy użytkownik naciśnie lewego przycisku myszy w formancie.  
  
```  
virtual void OnLButtonDown(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`point`  
 Ten parametr nie jest używany.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onlbuttonup"></a>CMFCRibbonEdit::OnLButtonUp  
 Wywoływane przez platformę, gdy użytkownik zwalnia lewego przycisku myszy.  
  
```  
virtual void OnLButtonUp(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`point`  
 Ten parametr nie jest używany.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onrtlchanged"></a>CMFCRibbonEdit::OnRTLChanged  
 Wywoływane przez platformę, aby zaktualizować [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontrolować zmianie kierunku układu.  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bIsRTL`  
 `TRUE`w przypadku układu od prawej do lewej; `FALSE` Jeśli układ jest od lewej do prawej.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onshow"></a>CMFCRibbonEdit::OnShow  
 Wywoływane przez platformę, by pokazać lub ukryć [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formantu.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bShow`  
 `TRUE`Aby wyświetlić kontroli. `FALSE` Aby ukryć kontrolki.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="redraw"></a>CMFCRibbonEdit::Redraw  
 Aktualizuje wyświetlanie [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formantu.  
  
```  
virtual void Redraw();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ponownie rysuje prostokąt wyświetlania dla `CMFCRibbonEdit` obiektu pośrednio wywołując [CWnd::RedrawWindow](http://msdn.microsoft.com/library/windows/desktop/dd162911) z `RDW_INVALIDATE`, `RDW_ERASE`, i `RDW_UPDATENOW` flagi zestawu.  
  
##  <a name="setaccdata"></a>CMFCRibbonEdit::SetACCData  
 Ustawia dane ułatwień dostępu dla [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
 `pParent`  
 Wskaźnik do okna nadrzędnego `CMFCRibbonEdit` obiektu.  
  
 `data`  
 Dane dostępności `CMFCRibbonEdit` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setedittext"></a>CMFCRibbonEdit::SetEditText  
 Ustawia tekst w polu tekstowym.  
  
```  
void SetEditText(CString strText);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`strText`  
 Tekst dla pola tekstowego.  
  
##  <a name="settextalign"></a>CMFCRibbonEdit::SetTextAlign  
 Określa wyrównanie tekstu w polu tekstowym.  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nAlign`  
 Wyrównanie tekstu wyliczyć wartość. W sekcji uwag możliwych wartości.  
  
### <a name="remarks"></a>Uwagi  
 Parametr `nAlign` jest jednym z następujących edycji stylów formantu:  
  
- **Es_left —** dla wyrównania do lewej  
  
- **Es_center —** center wyrównania  
  
- **Es_right —** dla wyrównanie do prawej  
  
 Aby uzyskać więcej informacji o tych stylów, zobacz [edytowania stylów formantu](http://msdn.microsoft.com/library/windows/desktop/bb775464).  
  
##  <a name="setwidth"></a>CMFCRibbonEdit::SetWidth  
 Ustawia szerokość pola tekstowego do [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formantu.  
  
```  
void SetWidth(
    int nWidth,  
    BOOL bInFloatyMode = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nWidth`  
 Szerokość w pikselach, pola tekstowego.  
  
 `bInFloatyMode`  
 `TRUE`Aby ustawić szerokość przestawne trybu; `FALSE` można ustawić szerokość regularne trybu.  
  
### <a name="remarks"></a>Uwagi  
 `CMFCRibbonEdit` Formant ma dwa szerokości, w zależności od trybu wyświetlania: zmiennoprzecinkową trybu ani regularne.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)   
 [Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)