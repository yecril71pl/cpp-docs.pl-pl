---
title: Klasa CReBar | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CReBar
- AFXEXT/CReBar
- AFXEXT/CReBar::AddBar
- AFXEXT/CReBar::Create
- AFXEXT/CReBar::GetReBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CReBar [MFC], AddBar
- CReBar [MFC], Create
- CReBar [MFC], GetReBarCtrl
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61601baca7a91d76f473281184c335cc5277f815
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201857"
---
# <a name="crebar-class"></a>Crebar — klasa
Pasek sterowania, który zawiera układ, trwałość i informacje o stanie dla formantów rebar.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CReBar : public CControlBar  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CReBar::AddBar](#addbar)|Dodaje obiekt band do paska pomocniczego.|  
|[CReBar::Create](#create)|Tworzy kontrolkę paska pomocniczego i dołącza je do `CReBar` obiektu.|  
|[CReBar::GetReBarCtrl](#getrebarctrl)|Umożliwia bezpośredni dostęp do podstawowych wspólnej kontroli.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt paska pomocniczego może zawierać wiele okien podrzędnych, zazwyczaj inne kontrolki, w tym pola tekstowe, paski narzędzi i pól listy. Obiekt paska pomocniczego, można wyświetlić jego okien podrzędnych za pośrednictwem określonego mapy bitowej. Aplikacja może automatycznie zmieniać rozmiar paska pomocniczego lub użytkownik może ręcznie zmienić rozmiar paska pomocniczego, klikając lub przeciągnij jej pasek uchwytu.  
  
 ![Przykład RebarMenu](../../mfc/reference/media/vc4sc61.gif "vc4sc61")  
  
## <a name="rebar-control"></a>Paska pomocniczego kontrolki  
 Obiekt paska pomocniczego działa podobnie jak obiekt paska narzędzi. Paska pomocniczego używa mechanizmu kliknij i przeciągnij, aby zmienić rozmiar jego paski. Kontrolki paska pomocniczego może zawierać jeden lub więcej grup, z każdego pasma o dowolnej kombinacji pasek uchwytu, mapy bitowej, etykietę tekstową i okna podrzędnego. Jednak grupy nie może zawierać więcej niż jedno okno podrzędne.  
  
 `CReBar` używa [z CReBarCtrl](../../mfc/reference/crebarctrl-class.md) klasy, aby zapewnić jego wykonania. Możesz uzyskać dostęp za pomocą kontrolki paska pomocniczego [getrebarctrl —](#getrebarctrl) Aby skorzystać z opcji dostosowywania formantu. Aby uzyskać więcej informacji na temat formantów rebar, zobacz `CReBarCtrl`. Aby uzyskać więcej informacji o używaniu kontrolki paska pomocniczego, zobacz [korzystanie z CReBarCtrl](../../mfc/using-crebarctrl.md).  
  
> [!CAUTION]
>  Paska pomocniczego i obiekty kontrolki paska pomocniczego nie obsługują kontrolka MFC na pasku dokowania. Jeśli `CRebar::EnableDocking` jest wywoływana, aplikacja będzie potwierdzenia.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CReBar`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxext.h  
  
##  <a name="addbar"></a>  CReBar::AddBar  
 Wywołaj tę funkcję elementu członkowskiego, aby dodać grupy do paska pomocniczego.  
  
```  
BOOL AddBar(
    CWnd* pBar,  
    LPCTSTR pszText = NULL,  
    CBitmap* pbmp = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

 
BOOL AddBar(
    CWnd* pBar,  
    COLORREF clrFore,  
    COLORREF clrBack,  
    LPCTSTR pszText = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```  
  
### <a name="parameters"></a>Parametry  
 *pBar*  
 Wskaźnik do `CWnd` obiekt okna podrzędnego, który ma zostać wstawiony do paska pomocniczego. Przywoływany obiekt musi mieć WS_CHILD.  
  
 *lpszText*  
 Wskaźnik do ciągu zawierającego tekst do wyświetlenia na paska pomocniczego. Wartość NULL, domyślnie. Tekst zawarty w *lpszText* nie jest częścią okna podrzędnego; nie znajduje się na paska pomocniczego, sam.  
  
 *pbmp*  
 Wskaźnik do `CBitmap` obiektu, który będzie wyświetlany w tle paska pomocniczego. Wartość NULL, domyślnie.  
  
 *dwStyle*  
 Wartość typu DWORD zawierającą styl do zastosowania do paska pomocniczego. Zobacz `fStyle` funkcja opis w strukturze Win32 [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) pełną listę style poza pasmem.  
  
 *clrFore*  
 Wartość COLORREF, która reprezentuje kolor pierwszego planu paska pomocniczego.  
  
 *clrBack*  
 Wartość COLORREF, która reprezentuje kolor tła paska pomocniczego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]  
  
##  <a name="create"></a>  CReBar::Create  
 Wywołaj tę funkcję elementu członkowskiego, aby utworzyć paska pomocniczego.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = RBS_BANDBORDERS,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,  
    UINT nID = AFX_IDW_REBAR);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentWnd*  
 Wskaźnik do `CWnd` obiekt, którego okno Windows ma element nadrzędny paska stanu. Zwykle okna ramki.  
  
 *dwCtrlStyle*  
 Styl kontrolki paska pomocniczego. Domyślnie RBS_BANDBORDERS, zawierające wąskie wierszy w celu rozdzielenia sąsiadujących paskami w formancie paska pomocniczego. Zobacz [style kontrolki paska pomocniczego](/windows/desktop/Controls/rebar-control-styles) w zestawie Windows SDK dla listy stylów.  
  
 *dwStyle*  
 Style okna ramowego paska pomocniczego.  
  
 *nID*  
 Identyfikator okna podrzędnego paska pomocniczego  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CReBar::AddBar](#addbar).  
  
##  <a name="getrebarctrl"></a>  CReBar::GetReBarCtrl  
 Ta funkcja elementu członkowskiego umożliwia bezpośredni dostęp do podstawowych wspólnej kontroli.  
  
```  
CReBarCtrl& GetReBarCtrl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do [z CReBarCtrl](../../mfc/reference/crebarctrl-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję elementu członkowskiego, aby wykorzystać funkcje formantu typowego paska pomocniczego Windows w dostosowywaniu swoje paska pomocniczego. Gdy wywołujesz `GetReBarCtrl`, zwraca obiekt odwołania do `CReBarCtrl` obiektu, aby można było używać któryś zbiór elementów członkowskich.  
  
 Aby uzyskać więcej informacji o korzystaniu z `CReBarCtrl` Aby dostosować swoje paska pomocniczego, zobacz [korzystanie z CReBarCtrl](../../mfc/using-crebarctrl.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Próbki MFC MFCIE](../../visual-cpp-samples.md)   
 [Ccontrolbar — klasa](../../mfc/reference/ccontrolbar-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



