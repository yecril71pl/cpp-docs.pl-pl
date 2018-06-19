---
title: Crebar — klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 94fc1e0ccad8980e0ed5a1cc0f8c0262502e1398
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371149"
---
# <a name="crebar-class"></a>Crebar — klasa
Pasek sterowania oferuje układu, trwałości i informacje o formantach paska pomocniczego stanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CReBar : public CControlBar  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CReBar::AddBar](#addbar)|Dodaje grupy do paska pomocniczego.|  
|[CReBar::Create](#create)|Tworzy kontrolkę paska pomocniczego i dołącza go do `CReBar` obiektu.|  
|[CReBar::GetReBarCtrl](#getrebarctrl)|Umożliwia bezpośredni dostęp do podstawowych formant.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt paska pomocniczego może zawierać wiele podrzędnych systemu Windows, zazwyczaj inne formanty, w tym pola edycji, paski narzędzi i pola listy. Obiekt paska pomocniczego można wyświetlić jego okno podrzędne za pośrednictwem Podana mapa bitowa. Aplikacja może automatycznie zmienić rozmiar paska pomocniczego, lub użytkownik może ręcznie zmienić rozmiar paska pomocniczego przez kliknięcie lub przeciągnięcie paska uchwytu.  
  
 ![Przykład RebarMenu](../../mfc/reference/media/vc4sc61.gif "vc4sc61")  
  
## <a name="rebar-control"></a>Paska pomocniczego kontrolki  
 Obiekt paska pomocniczego działa podobnie do obiektu paska narzędzi. Paska pomocniczego używa mechanizmu kliknij i przeciągnij zmiany rozmiaru jego pasma. Formantu paska pomocniczego może zawierać jeden lub więcej grup, z każdej grupy o dowolnej kombinacji pasek uchwytu, mapy bitowej etykietę tekstową i okna podrzędnego. Jednak pasma nie może zawierać więcej niż jedno okno podrzędne.  
  
 **Crebar —** używa [crebarctrl —](../../mfc/reference/crebarctrl-class.md) klasy, aby zapewnić jego wykonania. Dostęp można uzyskać za pomocą formantu paska pomocniczego [getrebarctrl —](#getrebarctrl) Aby skorzystać z opcji dostosowywania formantu. Aby uzyskać informacje o formantach paska pomocniczego, zobacz `CReBarCtrl`. Aby uzyskać więcej informacji o używaniu formanty paska pomocniczego, zobacz [crebarctrl przy użyciu —](../../mfc/using-crebarctrl.md).  
  
> [!CAUTION]
>  Paska pomocniczego i obiektów formantu paska pomocniczego nie obsługują formantu MFC paska dokowania. Jeśli **CRebar::EnableDocking** jest wywoływana, aplikacja będzie potwierdzenia.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Ccontrolbar —](../../mfc/reference/ccontrolbar-class.md)  
  
 `CReBar`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxext.h  
  
##  <a name="addbar"></a>  CReBar::AddBar  
 Wywołanie tej funkcji Członkowskich, aby dodać grupy do paska pomocniczego.  
  
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
 `pBar`  
 Wskaźnik do `CWnd` obiektu, który ma zostać wstawiony do paska pomocniczego okna podrzędnego. Odwołuje się do obiektu musi mieć **ws_child —**.  
  
 `lpszText`  
 Wskaźnik do ciąg zawierający tekst do wyświetlenia na paska pomocniczego. **Wartość NULL** domyślnie. Tekst wyświetlany w `lpszText` nie jest częścią okna podrzędnego; znajduje się na paska pomocniczego, do samej siebie.  
  
 `pbmp`  
 Wskaźnik do `CBitmap` obiektu, który będzie wyświetlany na tła paska pomocniczego. **Wartość NULL** domyślnie.  
  
 `dwStyle`  
 A `DWORD` zawierający styl paska pomocniczego. Zobacz **fStyle** funkcja opis w strukturze Win32 [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) pełną listę stylów poza pasmem.  
  
 *clrFore*  
 A **COLORREF** wartość, która reprezentuje kolor pierwszego planu paska pomocniczego.  
  
 *clrBack*  
 A **COLORREF** wartość, która reprezentuje kolor tła paska pomocniczego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]  
  
##  <a name="create"></a>  CReBar::Create  
 Wywołanie tej funkcji członkowskich można utworzyć paska pomocniczego.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = RBS_BANDBORDERS,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,  
    UINT nID = AFX_IDW_REBAR);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Wskaźnik do `CWnd` obiektu, którego okna systemu Windows jest nadrzędny paska stanu. Zwykle okna ramki.  
  
 `dwCtrlStyle`  
 Styl formantu paska pomocniczego. Domyślnie **RBS_BANDBORDERS**, która wyświetla zawęzić wierszy w celu rozdzielenia sąsiadujących paskami w formancie paska pomocniczego. Zobacz [stylów formantu paska pomocniczego](http://msdn.microsoft.com/library/windows/desktop/bb774377) w zestawie SDK systemu Windows lista style.  
  
 `dwStyle`  
 Style okna paska pomocniczego.  
  
 `nID`  
 Identyfikator paska pomocniczego okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CReBar::AddBar](#addbar).  
  
##  <a name="getrebarctrl"></a>  CReBar::GetReBarCtrl  
 Ta funkcja członkowska umożliwia bezpośredni dostęp do podstawowych formant.  
  
```  
CReBarCtrl& GetReBarCtrl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do [crebarctrl —](../../mfc/reference/crebarctrl-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji Członkowskich, aby skorzystać z funkcji systemu Windows formantu wspólnego paska pomocniczego w Dostosowywanie z paska pomocniczego. Podczas wywoływania `GetReBarCtrl`, zwraca obiekt odwołania do `CReBarCtrl` obiektów, dzięki czemu można użyć albo zestaw funkcji elementów członkowskich.  
  
 Aby uzyskać więcej informacji o korzystaniu z `CReBarCtrl` Aby dostosować z paska pomocniczego, zobacz [crebarctrl przy użyciu —](../../mfc/using-crebarctrl.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC MFCIE](../../visual-cpp-samples.md)   
 [Ccontrolbar — klasa](../../mfc/reference/ccontrolbar-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



