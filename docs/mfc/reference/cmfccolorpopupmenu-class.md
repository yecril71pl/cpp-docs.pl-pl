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
ms.openlocfilehash: b32317f4fd67a627a272ea8eefcc949d1b0e63c8
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852997"
---
# <a name="cmfccolorpopupmenu-class"></a>Klasa CMFCColorPopupMenu
Reprezentuje menu podręczne, które użytkownicy Użyj, aby wybrać kolory w dokumencie lub aplikacji.  
  
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
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|Tworzy dokowalne odrywania pasek koloru. (Przesłania [CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|  
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|Zwraca [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) , jest osadzony w menu podręcznym. (Przesłania [CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar).)|  
|`CMFCColorPopupMenu::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|  
|[CMFCColorPopupMenu::SetPropList](#setproplist)|Ustawia obiekt formantu siatki właściwości Embedded `CMFCColorBar` obiektu.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`m_bEnabledInCustomizeMode`|Wartość logiczna określająca, czy ma być wyświetlana na pasku kolorów.|  
|`m_wndColorBar`|`CMFCColorBar` Obiekt, który zapewnia wybór koloru.|  
  
### <a name="remarks"></a>Uwagi  
 Ta klasa dziedziczy funkcje menu podręcznego `CMFCPopupMenu` klasy i zarządza nimi `CMFCColorBar` obiekt, który zapewnia wybór koloru. Gdy framework narzędzi jest w trybie dostosowywania i `m_bEnabledInCustomizeMode` element członkowski jest ustawiany na wartość FALSE, obiekt paska kolorów nie jest wyświetlany. Aby uzyskać więcej informacji na temat trybu dostosowania, zobacz [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)  
  
 Aby uzyskać więcej informacji na temat `CMFCColorBar`, zobacz [klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
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
 Tablica kolorów wyświetlanych w menu podręcznym.  
  
 [in] *kolorów*  
 Kolor domyślnie wybrana.  
  
 [in] *lpszAutoColor*  
 Etykieta tekstowa elementu *automatyczne* przycisk koloru (ustawienie domyślne) lub wartość NULL.  
  
 Standardowa etykieta przycisku automatycznego **automatyczne**.  
  
 [in] *lpszOtherColor*  
 Etykieta tekstowa elementu *innych* przycisk wyświetlający więcej opcji koloru, lub wartość NULL.  
  
 Standardowa etykieta dla innych przycisku **więcej kolorów...** .  
  
 [in] *lpszDocColors*  
 Etykieta tekstowa przycisku kolory dokumentu. Paleta kolorów dokumentu zawiera listę kolorów używanych obecnie dokumentu.  
  
 [in] *lstDocColors*  
 Lista kolorów, które są obecnie używane.  
  
 [in] *nColumns*  
 Liczba kolumn, które zawiera tablicę kolorów.  
  
 [in] *nHorzDockRows*  
 Liczba wierszy, które ma pasek koloru, gdy jest zadokowany w poziomie.  
  
 [in] *nVertDockColumns*  
 Liczba kolumn, które ma pasek koloru, gdy jest zadokowany w pionie.  
  
 [in] *colorAutomatic*  
 Domyślny kolor struktura ma zastosowanie, gdy klikniesz przycisk Automatyczny.  
  
 [in] *uiCommandID*  
 Identyfikator polecenia sterowania paska kolorów.  
  
 [in] *bStdColorDlg*  
 Wartość logiczna wskazująca, czy mają być wyświetlane okno dialogowe kolorów standardowych systemowych lub [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) okno dialogowe.  
  
 [in] *pParentBtn*  
 Wskaźnik do przycisku nadrzędnej.  
  
 [in] *nID*  
 Identyfikator polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Każdego przeciążonego konstruktora zestawy `m_bEnabledInCustomizeMode` elementu członkowskiego na wartość FALSE.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCColorPopupMenu` obiektu.  
  
 [!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]  
  
##  <a name="createtearoffbar"></a>  CMFCColorPopupMenu::CreateTearOffBar  
 Tworzy dokowalne odrywania pasek koloru.  
  
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
 Wskaźnik do nowego obiektu pasek sterowania odrywania.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda tworzy [klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) obiektu i rzutuje je na [klasa CPane](../../mfc/reference/cpane-class.md) wskaźnika. Można rzutować tę wartość do [klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) wskaźnik przy użyciu jednej z makr rzutowania opisanego w [typu rzutowania z obiektów klas MFC](../../mfc/reference/type-casting-of-mfc-class-objects.md).  
  
##  <a name="getmenubar"></a>  CMFCColorPopupMenu::GetMenuBar  
 Zwraca [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) , jest osadzony w menu podręcznym.  
  
```  
virtual CMFCPopupMenuBar* GetMenuBar();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do osadzonego `CMFCPopupMenuBar`.  
  
### <a name="remarks"></a>Uwagi  
 Menu podręczne kolorów ma osadzony [klasa CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) obiektu. Przesłonić tę metodę w klasie pochodnej, jeśli aplikacja korzysta z innego typu osadzonego.  
  
##  <a name="setproplist"></a>  CMFCColorPopupMenu::SetPropList  
 Ustawia obiekt formantu siatki właściwości Embedded `CMFCColorBar` obiektu.  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pWndList*  
 Wskaźnik do obiektu formantu siatki właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
