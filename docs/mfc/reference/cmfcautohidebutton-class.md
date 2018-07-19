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
ms.openlocfilehash: 3135c95ddc32c198bb7abc6ddea4ef5aea5a1d8a
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338022"
---
# <a name="cmfcautohidebutton-class"></a>Klasa CMFCAutoHideButton
Przycisk, który wyświetla lub ukrywa [klasa CDockablePane](../../mfc/reference/cdockablepane-class.md) skonfigurowanego do ukrycia.  

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
|[CMFCAutoHideButton::Create](#create)|Tworzy i inicjuje przycisk Autoukrywanie.|  
|[CMFCAutoHideButton::GetAlignment](#getalignment)|Pobiera wyrównanie przycisk Autoukrywanie.|  
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|Zwraca [CDockablePane](../../mfc/reference/cdockablepane-class.md) obiekt skojarzony z przycisku automatycznego ukrywania.|  
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||  
|[CMFCAutoHideButton::GetRect](#getrect)||  
|[CMFCAutoHideButton::GetSize](#getsize)|Określa rozmiar przycisku automatycznego ukrywania.|  
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|Zwraca rozmiar etykiety tekst dla przycisku automatycznego ukrywania.|  
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|Najważniejsze funkcje automatyczne ukrywanie przycisku.|  
|[CMFCAutoHideButton::IsActive](#isactive)|Wskazuje, czy przycisk autoukrywanie jest aktywny.|  
|[CMFCAutoHideButton::IsHighlighted](#ishighlighted)|Zwraca Wyróżnij stan automatyczne ukrywanie przycisku.|  
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|Określa, czy przycisk automatycznego ukrywania jest pozioma lub pionowa.|  
|[CMFCAutoHideButton::IsTop](#istop)||  
|[CMFCAutoHideButton::IsVisible](#isvisible)|Wskazuje, czy przycisk jest widoczny.|  
|[CMFCAutoHideButton::Move](#move)||  
|[CMFCAutoHideButton::OnDraw](#ondraw)|Struktura wywołuje tę metodę, gdy go rysuje przycisk Autoukrywanie.|  
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|Struktura wywołuje tę metodę, gdy jej rysuje obramowanie przycisku automatycznego ukrywania.|  
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|Struktura wywołuje tę metodę podczas jego wypełniania tła przycisku automatycznego ukrywania.|  
|[CMFCAutoHideButton::ReplacePane](#replacepane)||  
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|Pokazuje lub ukrywa skojarzonego [klasa CDockablePane](../../mfc/reference/cdockablepane-class.md).|  
|[CMFCAutoHideButton::ShowButton](#showbutton)|Pokazuje lub ukrywa przycisk Autoukrywanie.|  
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||  
  
## <a name="remarks"></a>Uwagi  
 Po utworzeniu `CMFCAutoHideButton` obiekt jest dołączony do [klasa CDockablePane](../../mfc/reference/cdockablepane-class.md). `CDockablePane` Ukrywane lub wyświetlane w przypadku interakcji użytkownika z obiektu `CMFCAutoHideButton` obiektu.  
  
 Domyślnie automatycznie tworzą platformę `CMFCAutoHideButton` po użytkownik włączy automatyczne ukrywanie. Struktura można utworzyć elementu niestandardowego klasy interfejsu użytkownika zamiast `CMFCAutoHideButton` klasy. Aby określić które niestandardowej klasy interfejsu użytkownika, należy użyć w ramach, ustaw zmienną statycznej składowej `CMFCAutoHideBar::m_pAutoHideButtonRTS` równa niestandardowej klasy interfejsu użytkownika. Domyślnie ta zmienna jest ustawiona `CMFCAutoHideButton`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCAutoHideButton` obiektu i korzystać z różnych metod w `CMFCAutoHideButton` klasy. W przykładzie pokazano, jak inicjować `CMFCAutoHideButton` obiektu za pomocą jego `Create` metody, Pokaż skojarzonego `CDockablePane` klasy i Pokaż przycisk automatycznego ukrywania.  
  
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
 Tworzy i inicjuje przycisk Autoukrywanie.  
  
```  
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,  
    CDockablePane* pAutoHideWnd,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pParentBar*  
 Wskaźnik do paska narzędzi nadrzędnej.  
  
 [in] *pAutoHideWnd*  
 Wskaźnik do [CDockablePane](../../mfc/reference/cdockablepane-class.md) obiektu. Ten przycisk automatycznego ukrywania polega na schowaniu i pokazuje, że `CDockablePane`.  
  
 [in] *dwAlignment*  
 Wartość, która określa wyrównanie przycisku z ramką głównego okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Po utworzeniu `CMFCAutoHideButton` obiektu przycisku automatycznego ukrywania należy skojarzyć z określonym `CDockablePane`. Użytkownik może użyć przycisku automatycznego ukrywania, aby ukryć i pokazać skojarzonego `CDockablePane`.  
  
 *DwAlignment* parametr wskazuje, której przycisk Autoukrywanie znajduje się w aplikacji. Parametr może być jednym z następujących wartości:  
  
- CBRS_ALIGN_LEFT  
  
- CBRS_ALIGN_RIGHT  
  
- CBRS_ALIGN_TOP  
  
- CBRS_ALIGN_BOTTOM  
  
##  <a name="getalignment"></a>  CMFCAutoHideButton::GetAlignment  
 Pobiera wyrównanie przycisk Autoukrywanie.  
  
```  
DWORD GetAlignment() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość DWORD, która zawiera bieżące wyrównanie przycisk Autoukrywanie.  
  
### <a name="remarks"></a>Uwagi  
 Wyrównanie przycisku automatycznego ukrywania wskazuje, której przycisk znajduje się w aplikacji. Może być jednym z następujących wartości:  
  
- CBRS_ALIGN_LEFT  
  
- CBRS_ALIGN_RIGHT  
  
- CRBS_ALIGN_TOP  
  
- CBRS_ALIGN_BOTTOM  
  
##  <a name="getautohidewindow"></a>  CMFCAutoHideButton::GetAutoHideWindow  
 Zwraca [CDockablePane](../../mfc/reference/cdockablepane-class.md) obiekt skojarzony z przycisku automatycznego ukrywania.  
  
```  
CDockablePane* GetAutoHideWindow() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do powiązanych `CDockablePane` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Do skojarzenia przycisk Autoukrywanie z `CDockablePane`, przekazać `CDockablePane` jako parametr do [CMFCAutoHideButton::Create](#create) metody.  
  
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
 Określa rozmiar przycisku automatycznego ukrywania.  
  
```  
CSize GetSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CSize` obiekt, który zawiera rozmiar przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Obliczony rozmiar obejmuje rozmiar obramowania przycisku automatycznego ukrywania.  
  
##  <a name="gettextsize"></a>  CMFCAutoHideButton::GetTextSize  
 Zwraca rozmiar etykiety tekst dla przycisku automatycznego ukrywania.  
  
```  
virtual CSize GetTextSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) obiekt, który zawiera rozmiar tekstu przycisku automatycznego ukrywania.  
  
##  <a name="isactive"></a>  CMFCAutoHideButton::IsActive  
 Wskazuje, czy przycisk autoukrywanie jest aktywny.  
  
```  
BOOL IsActive() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przycisk automatycznego ukrywania jest aktywny; Wartość FALSE w przeciwnym razie.  
  
### <a name="remarks"></a>Uwagi  
 Przycisk autoukrywanie jest aktywna, gdy skojarzony [klasa CDockablePane](../../mfc/reference/cdockablepane-class.md) wyświetlane jest okno.  
  
##  <a name="ishorizontal"></a>  CMFCAutoHideButton::IsHorizontal  
 Określa, czy przycisk automatycznego ukrywania jest pozioma lub pionowa.  
  
```  
BOOL IsHorizontal() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli przycisk znajduje się poziomy; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Struktura Ustawia orientację przestrzenną [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) obiektu podczas jego tworzenia.  Orientacja można kontrolować za pomocą *dwAlignment* parametru w [CMFCAutoHideButton::Create](#create) metody.  
  
##  <a name="istop"></a>  CMFCAutoHideButton::IsTop  

  
```  
BOOL IsTop() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isvisible"></a>  CMFCAutoHideButton::IsVisible  
 Wskazuje, czy przycisk autoukrywanie jest widoczny.  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ten przycisk jest widoczny; Wartość FALSE w przeciwnym razie.  
  
##  <a name="ondraw"></a>  CMFCAutoHideButton::OnDraw  
 Struktura wywołuje tę metodę, gdy go rysuje przycisk Autoukrywanie.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz dostosować wygląd przycisków automatycznego ukrywania w aplikacji, Utwórz nową klasę pochodną `CMFCAutoHideButton`. W klasie pochodnej należy przesłonić tę metodę.  
  
##  <a name="ondrawborder"></a>  CMFCAutoHideButton::OnDrawBorder  
 Struktura wywołuje tę metodę, gdy jej rysuje obramowanie przycisku automatycznego ukrywania.  
  
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
 Prostokąt otaczający przycisk Autoukrywanie.  
  
 [in] *rectBorderSize*  
 Grubość obramowania z każdej strony przycisk Autoukrywanie.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz dostosować obramowania przycisku automatycznego ukrywania w aplikacji, Utwórz nową klasę pochodną `CMFCAutoHideButton`. W klasie pochodnej należy przesłonić tę metodę.  
  
##  <a name="onfillbackground"></a>  CMFCAutoHideButton::OnFillBackground  
 Struktura wywołuje tę metodę podczas jego wypełniania tła przycisku automatycznego ukrywania.  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *rect*  
 Prostokąt otaczający przycisk Autoukrywanie.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz dostosować tło Autoukrywanie przycisków w aplikacji, Utwórz nową klasę pochodną `CMFCAutoHideButton`. W klasie pochodnej należy przesłonić tę metodę.  
  
##  <a name="showattachedwindow"></a>  CMFCAutoHideButton::ShowAttachedWindow  
 Pokazuje lub ukrywa skojarzonego [klasa CDockablePane](../../mfc/reference/cdockablepane-class.md).  
  
```  
void ShowAttachedWindow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bShow*  
 Wartość logiczna określająca, czy ta metoda ma pokazać dołączonego `CDockablePane`.  
  
##  <a name="showbutton"></a>  CMFCAutoHideButton::ShowButton  
 Pokazuje lub ukrywa przycisk Autoukrywanie.  
  
```  
virtual void ShowButton(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bShow*  
 Wartość logiczna określająca, czy wyświetlać przycisk automatycznego ukrywania.  
  
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
 Wyłącz tryb automatycznego ukrywania.  
  
```  
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pFirstBarInGroup*  
 Wskaźnik do pierwszego paska w grupie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="highlightbutton"></a>  CMFCAutoHideButton::HighlightButton  
 Wyróżnia przycisk Ukryj automatycznie.  
  
```  
virtual void HighlightButton(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Parametry  
 *bHighlight*  
 Określa nowe automatycznego ukrywania stanu przycisku. Wartość TRUE wskazuje, że przycisk zostanie wyróżniona, wartość FALSE wskazuje, że przycisk nie jest wyróżniona.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ishighlighted"></a>  CMFCAutoHideButton::IsHighlighted  
 Zwraca stan Wyróżnienie przycisku automatycznego ukrywania.  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość TRUE, jeśli automatyczne ukrywanie przycisku zostanie wyróżniony; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)   
 [Klasa CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)
