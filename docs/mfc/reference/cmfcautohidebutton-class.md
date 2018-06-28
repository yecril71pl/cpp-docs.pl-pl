---
title: Klasa CMFCAutoHideButton | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::BringToTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Create
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAlignment
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAutoHideWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetParentToolBar
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetRect
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetTextSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::HighlightButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsActive
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHighlighted
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHorizontal
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsVisible
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Move
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDraw
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDrawBorder
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnFillBackground
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ReplacePane
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowAttachedWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::UnSetAutoHideMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCAutoHideButton [MFC], BringToTop
- CMFCAutoHideButton [MFC], Create
- CMFCAutoHideButton [MFC], GetAlignment
- CMFCAutoHideButton [MFC], GetAutoHideWindow
- CMFCAutoHideButton [MFC], GetParentToolBar
- CMFCAutoHideButton [MFC], GetRect
- CMFCAutoHideButton [MFC], GetSize
- CMFCAutoHideButton [MFC], GetTextSize
- CMFCAutoHideButton [MFC], HighlightButton
- CMFCAutoHideButton [MFC], IsActive
- CMFCAutoHideButton [MFC], IsHighlighted
- CMFCAutoHideButton [MFC], IsHorizontal
- CMFCAutoHideButton [MFC], IsTop
- CMFCAutoHideButton [MFC], IsVisible
- CMFCAutoHideButton [MFC], Move
- CMFCAutoHideButton [MFC], OnDraw
- CMFCAutoHideButton [MFC], OnDrawBorder
- CMFCAutoHideButton [MFC], OnFillBackground
- CMFCAutoHideButton [MFC], ReplacePane
- CMFCAutoHideButton [MFC], ShowAttachedWindow
- CMFCAutoHideButton [MFC], ShowButton
- CMFCAutoHideButton [MFC], UnSetAutoHideMode
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a62dcb52c6e50897c3ae4a518b1cd8f2b704c7a1
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038302"
---
# <a name="cmfcautohidebutton-class"></a>Klasa CMFCAutoHideButton
Przycisk, który wyświetla lub ukrywa [klasy CDockablePane](../../mfc/reference/cdockablepane-class.md) skonfigurowanego do ukrycia.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>Składnia  
  
```  
class CMFCAutoHideButton : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCAutoHideButton::BringToTop](#bringtotop)||  
|[CMFCAutoHideButton::Create](#create)|Tworzy i inicjuje automatyczne ukrywanie przycisku.|  
|[CMFCAutoHideButton::GetAlignment](#getalignment)|Pobiera Wyrównanie automatyczne ukrywanie przycisku.|  
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|Zwraca [CDockablePane](../../mfc/reference/cdockablepane-class.md) obiekt skojarzony z przyciskiem autoukrywania.|  
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||  
|[CMFCAutoHideButton::GetRect](#getrect)||  
|[CMFCAutoHideButton::GetSize](#getsize)|Określa rozmiar przycisku autoukrywania.|  
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|Zwraca rozmiar etykiety tekst dla przycisku autoukrywania.|  
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|Najważniejsze funkcje automatycznie Ukryj przycisk.|  
|[CMFCAutoHideButton::IsActive](#isactive)|Wskazuje, czy automatycznie Ukryj przycisk jest aktywny.|  
|[CMFCAutoHideButton::IsHighlighted](#ishighlighted)|Zwraca Wyróżnij stan przycisku Ukryj automatycznie.|  
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|Określa, czy przycisk autoukrywania jest pozioma lub pionowa.|  
|[CMFCAutoHideButton::IsTop](#istop)||  
|[CMFCAutoHideButton::IsVisible](#isvisible)|Wskazuje, czy przycisk jest widoczny.|  
|[CMFCAutoHideButton::Move](#move)||  
|[CMFCAutoHideButton::OnDraw](#ondraw)|Platformę wywołuje tę metodę, gdy go rysuje automatyczne ukrywanie przycisku.|  
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|Struktura wywołuje tę metodę po go rysuje obramowanie przycisku autoukrywania.|  
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|Struktura wywołuje tę metodę po zapełnieniu tła automatyczne ukrywanie przycisku.|  
|[CMFCAutoHideButton::ReplacePane](#replacepane)||  
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|Pokazuje lub ukrywa skojarzony [CDockablePane klasy](../../mfc/reference/cdockablepane-class.md).|  
|[CMFCAutoHideButton::ShowButton](#showbutton)|Pokazuje lub ukrywa automatyczne ukrywanie przycisku.|  
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||  
  
## <a name="remarks"></a>Uwagi  
 Po utworzeniu `CMFCAutoHideButton` obiekt jest dołączony do [CDockablePane klasy](../../mfc/reference/cdockablepane-class.md). `CDockablePane` Ukryte lub wyświetlane w postaci użytkownik wchodzi w interakcję z obiektu `CMFCAutoHideButton` obiektu.  
  
 Domyślnie automatycznie tworzy platformę `CMFCAutoHideButton` gdy użytkownik włącza autoukrywania. Platformę można utworzyć elementu niestandardowego klasy interfejsu użytkownika zamiast `CMFCAutoHideButton` klasy. Aby określić, które niestandardowej klasy interfejsu użytkownika, należy użyć w ramach, ustaw zmienną statyczny element członkowski `CMFCAutoHideBar::m_pAutoHideButtonRTS` równa niestandardowej klasy interfejsu użytkownika. Domyślnie ta zmienna jest ustawiona `CMFCAutoHideButton`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCAutoHideButton` obiektu i korzystać z różnych metod w `CMFCAutoHideButton` klasy. W przykładzie pokazano, jak zainicjować `CMFCAutoHideButton` obiektu przy użyciu jego `Create` metody, Pokaż skojarzony `CDockablePane` klasy, a następnie automatycznie Ukryj przycisk Pokaż.  
  
 [!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCAutoHideButton`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxautohidebutton.h  
  
##  <a name="bringtotop"></a>  CMFCAutoHideButton::BringToTop  

  
```  
void BringToTop();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="create"></a>  CMFCAutoHideButton::Create  
 Tworzy i inicjuje automatyczne ukrywanie przycisku.  
  
```  
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,  
    CDockablePane* pAutoHideWnd,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pParentBar*  
 Wskaźnik do narzędzi nadrzędnej.  
  
 [in] *pAutoHideWnd*  
 Wskaźnik do [CDockablePane](../../mfc/reference/cdockablepane-class.md) obiektu. Ten przycisk autoukrywania ukrywa i wskazuje, że `CDockablePane`.  
  
 [in] *dwAlignment*  
 Wartość, która określa sposób wyrównania przycisku z głównego okna ramowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Po utworzeniu `CMFCAutoHideButton` obiektu, przycisk autoukrywania należy skojarzyć z określonym `CDockablePane`. Użytkownik może użyć przycisku autoukrywania, aby ukryć i pokazać skojarzony `CDockablePane`.  
  
 *DwAlignment* parametr wskazuje, gdzie znajduje się przycisk autoukrywania w aplikacji. Parametr może być jednym z następujących wartości:  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CBRS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
##  <a name="getalignment"></a>  CMFCAutoHideButton::GetAlignment  
 Pobiera Wyrównanie automatyczne ukrywanie przycisku.  
  
```  
DWORD GetAlignment() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `DWORD` wartości, która zawiera bieżące wyrównanie automatyczne ukrywanie przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Wyrównanie przycisk autoukrywania wskazuje, gdzie znajduje się przycisk w aplikacji. Może być jeden z następujących wartości:  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CRBS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
##  <a name="getautohidewindow"></a>  CMFCAutoHideButton::GetAutoHideWindow  
 Zwraca [CDockablePane](../../mfc/reference/cdockablepane-class.md) obiekt skojarzony z przyciskiem autoukrywania.  
  
```  
CDockablePane* GetAutoHideWindow() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do skojarzonego `CDockablePane` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Aby skojarzyć przycisk autoukrywania z `CDockablePane`, przekazać `CDockablePane` jako parametr [CMFCAutoHideButton::Create](#create) metody.  
  
##  <a name="getparenttoolbar"></a>  CMFCAutoHideButton::GetParentToolBar  

  
```  
CMFCAutoHideBar* GetParentToolBar();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getrect"></a>  CMFCAutoHideButton::GetRect  

  
```  
CRect GetRect() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getsize"></a>  CMFCAutoHideButton::GetSize  
 Określa rozmiar przycisku autoukrywania.  
  
```  
CSize GetSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CSize` obiekt, który zawiera rozmiar przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Obliczony rozmiar obejmuje rozmiar obramowania przycisku autoukrywania.  
  
##  <a name="gettextsize"></a>  CMFCAutoHideButton::GetTextSize  
 Zwraca rozmiar etykiety tekst dla przycisku autoukrywania.  
  
```  
virtual CSize GetTextSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) obiekt, który zawiera rozmiar tekst dla przycisku autoukrywania.  
  
##  <a name="isactive"></a>  CMFCAutoHideButton::IsActive  
 Wskazuje, czy automatycznie Ukryj przycisk jest aktywny.  
  
```  
BOOL IsActive() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli automatycznie Ukryj przycisk jest aktywny; `FALSE` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Automatycznie Ukryj przycisk jest aktywny, gdy skojarzony [klasy CDockablePane](../../mfc/reference/cdockablepane-class.md) pokazaniem okna.  
  
##  <a name="ishorizontal"></a>  CMFCAutoHideButton::IsHorizontal  
 Określa, czy przycisk autoukrywania jest pozioma lub pionowa.  
  
```  
BOOL IsHorizontal() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ten przycisk jest poziomy; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Platformę Ustawia orientację przestrzenną [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) obiektu po jego utworzeniu.  Orientacja można kontrolować przy użyciu `dwAlignment` parametru w [CMFCAutoHideButton::Create](#create) metody.  
  
##  <a name="istop"></a>  CMFCAutoHideButton::IsTop  

  
```  
BOOL IsTop() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isvisible"></a>  CMFCAutoHideButton::IsVisible  
 Wskazuje, czy przycisk autoukrywania jest widoczny.  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli przycisk jest widoczna; `FALSE` inaczej.  
  
##  <a name="ondraw"></a>  CMFCAutoHideButton::OnDraw  
 Platformę wywołuje tę metodę, gdy go rysuje automatyczne ukrywanie przycisku.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz dostosować wygląd przycisków autoukrywania w aplikacji, Utwórz nową klasę pochodną `CMFCAutoHideButton`. W klasie pochodnej przesłonić tę metodę.  
  
##  <a name="ondrawborder"></a>  CMFCAutoHideButton::OnDrawBorder  
 Struktura wywołuje tę metodę po go rysuje obramowanie przycisku autoukrywania.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rectBounds,  
    CRect rectBorderSize);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *rectBounds*  
 Prostokąt ograniczający automatyczne ukrywanie przycisku.  
  
 [in] *rectBorderSize*  
 Grubość obramowania dla każdej strony automatyczne ukrywanie przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz dostosować obramowania przycisku autoukrywania w aplikacji, Utwórz nową klasę pochodną `CMFCAutoHideButton`. W klasie pochodnej przesłonić tę metodę.  
  
##  <a name="onfillbackground"></a>  CMFCAutoHideButton::OnFillBackground  
 Struktura wywołuje tę metodę po zapełnieniu tła automatyczne ukrywanie przycisku.  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *rect*  
 Prostokąt ograniczający automatyczne ukrywanie przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz dostosować tła przycisków autoukrywania w aplikacji, Utwórz nową klasę pochodną `CMFCAutoHideButton`. W klasie pochodnej przesłonić tę metodę.  
  
##  <a name="showattachedwindow"></a>  CMFCAutoHideButton::ShowAttachedWindow  
 Pokazuje lub ukrywa skojarzony [CDockablePane klasy](../../mfc/reference/cdockablepane-class.md).  
  
```  
void ShowAttachedWindow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bShow*  
 Wartość logiczna określająca, czy ta metoda, pokazuje dołączonego `CDockablePane`.  
  
##  <a name="showbutton"></a>  CMFCAutoHideButton::ShowButton  
 Pokazuje lub ukrywa automatyczne ukrywanie przycisku.  
  
```  
virtual void ShowButton(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bShow*  
 Wartość logiczna określająca, czy wyświetlać przycisk autoukrywania.  
  
##  <a name="move"></a>  CMFCAutoHideButton::Move  

  
```  
void Move(int nOffset);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nOffset*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="replacepane"></a>  CMFCAutoHideButton::ReplacePane  

  
```  
void ReplacePane(CDockablePane* pNewBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pNewBar*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="unsetautohidemode"></a>  CMFCAutoHideButton::UnSetAutoHideMode  
 Wyłącz tryb autoukrywania.  
  
```  
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pFirstBarInGroup*  
 Wskaźnik do pierwszego paska w grupie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="highlightbutton"></a>  CMFCAutoHideButton::HighlightButton  
 Przedstawia przycisk Ukryj automatycznie.  
  
```  
virtual void HighlightButton(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Parametry  
 *bHighlight*  
 Określa nowe automatyczne ukrywanie stanu przycisku. `TRUE` Wskazuje przycisk zostanie wyróżniona, `FALSE` wskazuje przycisku nie są wyróżnione.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ishighlighted"></a>  CMFCAutoHideButton::IsHighlighted  
 Zwraca stan wyróżnienia przycisk Ukryj automatycznie.  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` Jeśli automatycznie Ukryj przycisk jest zaznaczony, a w przeciwnym `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)   
 [Klasa CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)
