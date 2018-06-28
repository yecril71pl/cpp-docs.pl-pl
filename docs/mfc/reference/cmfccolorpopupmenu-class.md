---
title: Klasa CMFCColorPopupMenu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54999252af2ec55c67e1afc69c2788f96cfc640e
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037307"
---
# <a name="cmfccolorpopupmenu-class"></a>Klasa CMFCColorPopupMenu
Reprezentuje menu podręczne, które użytkownicy umożliwia wybór kolorów w dokumentu lub aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCColorPopupMenu : public CMFCPopupMenu  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|Konstruuje `CMFCColorPopupMenu` obiektu.|  
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|Tworzy dokującego oderwania pasek koloru. (Przesłania [CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|  
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|Zwraca [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) który jest osadzony w menu podręcznym. (Przesłania [CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar).)|  
|`CMFCColorPopupMenu::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCColorPopupMenu::SetPropList](#setproplist)|Ustawia właściwości siatki kontroli obiektu osadzonego `CMFCColorBar` obiektu.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`m_bEnabledInCustomizeMode`|Wartość logiczna określająca, czy mają być wyświetlane na pasku kolorów.|  
|`m_wndColorBar`|`CMFCColorBar` Obiekt, który umożliwia wybór kolorów.|  
  
### <a name="remarks"></a>Uwagi  
 Ta klasa dziedziczy funkcjonalność menu podręczne `CMFCPopupMenu` klasy i zarządza `CMFCColorBar` obiekt, który umożliwia wybór kolorów. Gdy framework narzędzi działają w trybie dostosowania i `m_bEnabledInCustomizeMode` ma ustawioną wartość elementu członkowskiego `FALSE`, nie ma obiektu pasek koloru. Aby uzyskać więcej informacji dotyczących trybu dostosowania, zobacz [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)  
  
 Aby uzyskać więcej informacji na temat `CMFCColorBar`, zobacz [CMFCColorBar klasy](../../mfc/reference/cmfccolorbar-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cframewnd —](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 [CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcolorpopupmenu.h  
  
##  <a name="cmfccolorpopupmenu"></a>  CMFCColorPopupMenu::CMFCColorPopupMenu  
 Konstruuje `CMFCColorPopupMenu` obiektu.  
  
```  
CMFCColorPopupMenu(
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    int nHorzDockRows,  
    int nVertDockColumns,  
    COLORREF colorAutomatic,  
    UINT uiCommandID,  
    BOOL bStdColorDlg = FALSE);

 
CMFCColorPopupMenu(
    CMFCColorButton* pParentBtn,  
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic);

 
CMFCColorPopupMenu(
    CMFCRibbonColorButton* pParentBtn,  
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *kolorów*  
 Tablica kolorów, które Wyświetla platformę w menu podręcznym.  
  
 [in] *kolorów*  
 Domyślnie wybrany kolor.  
  
 [in] *lpszAutoColor*  
 Etykieta tekstowa elementu *automatyczne* przycisk koloru (ustawienie domyślne), lub `NULL`.  
  
 Standardowa etykieta przycisku automatycznego **automatyczne**.  
  
 [in] *lpszOtherColor*  
 Etykieta tekstowa elementu *innych* przycisku, który wyświetla więcej kolorów, lub `NULL`.  
  
 Standardowe Etykieta przycisku innych **więcej kolorów...** .  
  
 [in] *lpszDocColors*  
 Etykieta tekstowa przycisk kolory dokumentu. Palety kolorów dokumentu zawiera listę wszystkich kolorów, które obecnie używane.  
  
 [in] *lstDocColors*  
 Lista kolorów, które są obecnie używane.  
  
 [in] *nColumns*  
 Liczba kolumn, które ma tablicę kolorów.  
  
 [in] *nHorzDockRows*  
 Liczba wierszy, które pasek koloru ma, gdy jest zadokowany poziomo.  
  
 [in] *nVertDockColumns*  
 Liczba kolumn, które pasek koloru ma, gdy jest zadokowany w pionie.  
  
 [in] *colorAutomatic*  
 Domyślny kolor platformę stosuje się po kliknięciu przycisku automatycznego.  
  
 [in] *uiCommandID*  
 Identyfikator polecenia sterowania pasek koloru.  
  
 [in] *bStdColorDlg*  
 Wartość logiczna wskazująca, czy wyświetlać okno dialogowe kolorów standardowych systemowych lub [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) okno dialogowe.  
  
 [in] *pParentBtn*  
 Wskaźnik do nadrzędnego przycisku.  
  
 [in] *nID*  
 Identyfikator polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Każdy przeciążony ustawia konstruktora `m_bEnabledInCustomizeMode` członka `FALSE`.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCColorPopupMenu` obiektu.  
  
 [!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]  
  
##  <a name="createtearoffbar"></a>  CMFCColorPopupMenu::CreateTearOffBar  
 Tworzy dokującego oderwania pasek koloru.  
  
```  
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,  
    UINT uiID,  
    LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in] *pWndMain*|Wskaźnik do okna nadrzędnego z paskiem oderwania.|  
|[in] *uiID*|Identyfikator polecenia paskiem oderwania.|  
|[in] *lpszName*|Tekst okna paskiem oderwania.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowego obiektu formantu oderwania w pasku.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda tworzy [klasy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) obiektu i rzutuje do [klasy CPane](../../mfc/reference/cpane-class.md) wskaźnika. Tę wartość można rzutować do [klasy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) wskaźnika za pomocą jednego z makra rzutowanie opisanego w [typu rzutowania dla obiektów klas MFC](../../mfc/reference/type-casting-of-mfc-class-objects.md).  
  
##  <a name="getmenubar"></a>  CMFCColorPopupMenu::GetMenuBar  
 Zwraca [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) który jest osadzony w menu podręcznym.  
  
```  
virtual CMFCPopupMenuBar* GetMenuBar();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do osadzonego `CMFCPopupMenuBar`.  
  
### <a name="remarks"></a>Uwagi  
 Menu podręczne kolorów ma osadzonych [klasy CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) obiektu. Należy przesłonić tę metodę w klasie pochodnej, jeśli aplikacja korzysta z innego typu osadzonego.  
  
##  <a name="setproplist"></a>  CMFCColorPopupMenu::SetPropList  
 Ustawia właściwości siatki kontroli obiektu osadzonego `CMFCColorBar` obiektu.  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pWndList*  
 Wskaźnik do obiektu formantu siatki właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
