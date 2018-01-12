---
title: Klasa CCtrlView | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCtrlView
- AFXWIN/CCtrlView
- AFXWIN/CCtrlView::CCtrlView
- AFXWIN/CCtrlView::OnDraw
- AFXWIN/CCtrlView::PreCreateWindow
- AFXWIN/CCtrlView::m_dwDefaultStyle
- AFXWIN/CCtrlView::m_strClass
dev_langs: C++
helpviewer_keywords:
- CCtrlView [MFC], CCtrlView
- CCtrlView [MFC], OnDraw
- CCtrlView [MFC], PreCreateWindow
- CCtrlView [MFC], m_dwDefaultStyle
- CCtrlView [MFC], m_strClass
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 484abaf5344400e03b53038d2c137497c202345f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cctrlview-class"></a>Klasa CCtrlView
Dostosowuje widok dokumentu architektury formanty standardowe obsługiwane przez wersje systemu Windows 98 i Windows NT 3.51 lub nowszy.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CCtrlView : public CView  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCtrlView::CCtrlView](#cctrlview)|Konstruuje `CCtrlView` obiektu.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCtrlView::OnDraw](#ondraw)|Wywoływane przez platformę, by narysować przy użyciu kontekstu określonego urządzenia.|  
|[CCtrlView::PreCreateWindow](#precreatewindow)|Wywołuje się przed tworzeniem okna systemu Windows dołączona do tego `CCtrlView` obiektu.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Zawiera styl domyślny dla widoku klasy.|  
|[CCtrlView::m_strClass](#m_strclass)|Zawiera nazwę klasy systemu Windows w klasie widoku.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa `CCtrlView` i jego pochodne [CEditView](../../mfc/reference/ceditview-class.md), [clistview —](../../mfc/reference/clistview-class.md), [CTreeView —](../../mfc/reference/ctreeview-class.md), i [cricheditview —](../../mfc/reference/cricheditview-class.md), dostosowania architektury widok dokumentu na nowe formanty wspólne obsługiwane przez Windows 95/98 i systemu Windows NT w wersji 3.51 lub nowszej. Aby uzyskać więcej informacji na komputerze o architekturze dokument widok, zobacz [architektury dokument/widok](../../mfc/document-view-architecture.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cview —](../../mfc/reference/cview-class.md)  
  
 `CCtrlView`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cctrlview"></a>CCtrlView::CCtrlView  
 Konstruuje `CCtrlView` obiektu.  
  
```  
CCtrlView(
    LPCTSTR lpszClass,  
    DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszClass`  
 Nazwa klasy Windows klasy widoku.  
  
 `dwStyle`  
 Styl klasy widoku.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje konstruktor, gdy zostanie utworzone nowe okno ramowe lub okna jest podzielona. Zastąpienie [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) zainicjować widoku po dołączeniu dokumentu. Wywołanie [CWnd::Create](../../mfc/reference/cwnd-class.md#create) lub [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex) można utworzyć obiektu systemu Windows.  
  
##  <a name="m_strclass"></a>CCtrlView::m_strClass  
 Zawiera nazwę klasy systemu Windows w klasie widoku.  
  
```  
CString m_strClass;  
```  
  
##  <a name="m_dwdefaultstyle"></a>CCtrlView::m_dwDefaultStyle  
 Zawiera styl domyślny dla widoku klasy.  
  
```  
DWORD m_dwDefaultStyle;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten styl jest stosowana, gdy tworzone jest okno.  
  
##  <a name="ondraw"></a>CCtrlView::OnDraw  
 Wywoływane przez platformę, by narysować zawartość `CCtrlView` przy użyciu kontekstu określonego urządzenia.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskaźnik do kontekstu urządzenia, w którym występuje rysunku.  
  
### <a name="remarks"></a>Uwagi  
 `OnDraw`nazywa się zwykle do wyświetlania na ekranie, przekazywanie ekranu kontekstu urządzenia określonego przez `pDC`.  
  
##  <a name="precreatewindow"></a>CCtrlView::PreCreateWindow  
 Wywołuje się przed tworzeniem okna systemu Windows dołączona do tego `CWnd` obiektu.  
  
```  
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```  
  
### <a name="parameters"></a>Parametry  
 *CS*  
 A [CREATESTRUCT](http://msdn.microsoft.com/library/windows/desktop/ms632603) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli tworzenie okien powinno być kontynuowane; 0, aby wskazać błąd podczas tworzenia.  
  
### <a name="remarks"></a>Uwagi  
 Nigdy nie bezpośrednio wywoływać tej funkcji.  
  
 Domyślna implementacja ta funkcja sprawdza, czy **NULL** Nazwa klasy okna i zastępuje domyślnego. Przesłonić tę funkcję elementu członkowskiego, aby zmodyfikować `CREATESTRUCT` struktury przed utworzeniem okna.  
  
 Każda klasa pochodzi od `CCtrlView` dodaje jego zastąpienia z własnych funkcji `PreCreateWindow`. Zgodnie z projektem, te pochodne z `PreCreateWindow` nie są udokumentowane. Aby ustalić style właściwe dla każdej klasy i zależności między style, należy zbadać kod źródłowy MFC dla klasy podstawowej aplikacji. Jeśli chcesz przesłonić `PreCreateWindow`, można określić, czy styl używany w klasie podstawowej aplikacji zapewniać funkcje, korzystając z informacji zebranych z kodu źródłowego MFC.  
  
 Aby uzyskać więcej informacji na temat zmieniania Style okna, zobacz [Zmienianie stylów okna utworzonego przez MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Cview — klasa](../../mfc/reference/cview-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [CTreeView — klasa](../../mfc/reference/ctreeview-class.md)   
 [Clistview — klasa](../../mfc/reference/clistview-class.md)   
 [Klasa CRichEditView](../../mfc/reference/cricheditview-class.md)
