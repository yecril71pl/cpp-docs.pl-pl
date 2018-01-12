---
title: Klasa CMFCShellTreeCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::EnableShellContextMenu
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetItemPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetRelatedList
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnChildNotify
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemIcon
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemText
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::Refresh
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SelectPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetRelatedList
dev_langs: C++
helpviewer_keywords:
- CMFCShellTreeCtrl [MFC], EnableShellContextMenu
- CMFCShellTreeCtrl [MFC], GetFlags
- CMFCShellTreeCtrl [MFC], GetItemPath
- CMFCShellTreeCtrl [MFC], GetRelatedList
- CMFCShellTreeCtrl [MFC], OnChildNotify
- CMFCShellTreeCtrl [MFC], OnGetItemIcon
- CMFCShellTreeCtrl [MFC], OnGetItemText
- CMFCShellTreeCtrl [MFC], Refresh
- CMFCShellTreeCtrl [MFC], SelectPath
- CMFCShellTreeCtrl [MFC], SetFlags
- CMFCShellTreeCtrl [MFC], SetRelatedList
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 727b0032687ed22692f07f9b5e9e5fe8b2813071
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcshelltreectrl-class"></a>Klasa CMFCShellTreeCtrl
`CMFCShellTreeCtrl` Rozszerza klasy [ctreectrl — klasa](../../mfc/reference/ctreectrl-class.md) funkcji Wyświetlając hierarchię elementów powłoki.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>Składnia  
  
```  
class CMFCShellTreeCtrl : public CTreeCtrl  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Włącza lub wyłącza menu skrótów.|  
|[CMFCShellTreeCtrl::GetFlags](#getflags)|Zwraca kombinacją flag, które są przekazywane do [IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066).|  
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Pobiera ścieżkę do elementu.|  
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|Zwraca wskaźnik do [klasy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiekt, który jest używany razem z tym `CMFCShellTreeCtrl` obiektu w celu utworzenia okna Eksploratora podobne.|  
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|Funkcji członkowskiej jest wywoływana przez okno nadrzędne tego okna, gdy odbierze powiadomienie, która ma zastosowanie do tego okna. (Przesłania [CWnd::OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|  
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||  
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||  
|[CMFCShellTreeCtrl::Refresh](#refresh)|Odświeża i Odświeża bieżącą `CMFCShellTreeCtrl` obiektu.|  
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Wybiera elementu formantu drzewa odpowiednie na podstawie podanej PIDL lub ciąg ścieżki.|  
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Ustawia flagi do filtrowania kontekście drzewa (podobnie jak flagi używane przez `IShellFolder::EnumObjects`).|  
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Ustawia relacji między bieżącą `CMFCShellTreeCtrl` obiektu i `CMFCShellListCtrl` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa rozszerza `CTreeCtrl` klasy przez włączenie programu do uwzględnienia w drzewie elementów powłoki systemu Windows. Ta klasa może być skojarzone z `CMFCShellListCtrl` obiekt, aby utworzyć pełną okno Eksploratora. Następnie wybraniu elementu w drzewie wyświetli listę elementów powłoki systemu Windows w skojarzonej listy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CTreeCtrl](../../mfc/reference/ctreectrl-class.md)  
  
 `CMFCShellTreeCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxshelltreeCtrl.h  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia obiektu `CMFCShellTreeCtrl` klasy. Następujący fragment kodu jest częścią [przykładowy Eksplorator](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]  
  
##  <a name="enableshellcontextmenu"></a>CMFCShellTreeCtrl::EnableShellContextMenu  
 Umożliwia menu skrótów.  
  
```  
void EnableShellContextMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 Wartość logiczna określająca, czy włączyć menu skrótów.  
  
##  <a name="getflags"></a>CMFCShellTreeCtrl::GetFlags  
 Zwraca flag ustawionych dla [klasy CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) obiektu.  
  
```  
DWORD GetFlags() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `DWORD` ustawić wartość, która określa aktualnie kombinacją flag.  
  
### <a name="remarks"></a>Uwagi  
 Ustaw flagi `CMFCShellTreeCtrl` są wysyłane do metody [IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066) zawsze, gdy obiekt zostanie odświeżony. Można zmienić flagi z [CMFCShellTreeCtrl::SetFlags](#setflags) metody.  
  
##  <a name="getitempath"></a>CMFCShellTreeCtrl::GetItemPath  
 Pobiera ścieżkę elementu [klasy CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) obiektu.  
  
```  
BOOL GetItemPath(
    CString& strPath,  
    HTREEITEM htreeItem = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`strPath`  
 Odwołanie do parametr typu string. Metoda zapisuje ścieżka elementu tego parametru.  
  
 [in]`htreeItem`  
 Metoda pobiera ścieżkę dla tego elementu formantu drzewa.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta metoda zawiedzie, `strPath` zawiera pusty ciąg.  
  
 Jeśli nie określisz `hTreeItem`, ta metoda próbuje uzyskać ciąg dla aktualnie wybranego elementu. Jeśli nie wybrano elementów i `hTreeItem` jest `NULL`, ta metoda zakończy się niepowodzeniem.  
  
##  <a name="getrelatedlist"></a>CMFCShellTreeCtrl::GetRelatedList  
 Zwraca wskaźnik do [klasy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiekt, który jest skojarzony z tym [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) obiektu.  
  
```  
CMFCShellListCtrl* GetRelatedList() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CMFCShellListCtrl` obiekt, który jest skojarzony z tym obiektem formantu drzewa.  
  
### <a name="remarks"></a>Uwagi  
 Za pomocą `CMFCShellListCtrl` obiekt razem z `CMFCShellTreeCtrl` obiektu, można utworzyć okna Eksploratora podobne. Użyj metody [CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist) do skojarzenia z dwóch klas. Po ich skojarzonych platformę automatycznie aktualizuje `CMFCShellListCtrl` Jeśli zaznaczenie w `CMFCShellTreeCtrl` zmiany.  
  
##  <a name="onchildnotify"></a>CMFCShellTreeCtrl::OnChildNotify  

  
```  
virtual BOOL OnChildNotify(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam,  
    LRESULT* pLResult);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`message`  
 [in]`wParam`  
 [in]`lParam`  
 [in]`pLResult`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ongetitemicon"></a>CMFCShellTreeCtrl::OnGetItemIcon  

  
```  
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pItem`  
 [in]`bSelected`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ongetitemtext"></a>CMFCShellTreeCtrl::OnGetItemText  

  
```  
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pItem`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="refresh"></a>CMFCShellTreeCtrl::Refresh  
 Odświeża i odświeża [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md).  
  
```  
void Refresh();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby odświeżyć hierarchię elementów wyświetlanych w `CMFCShellTreeCtrl`.  
  
##  <a name="selectpath"></a>CMFCShellTreeCtrl::SelectPath  
 Wybiera element [klasy CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) na podstawie podanej ścieżki.  
  
```  
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszPath`  
 Ciąg, który określa ścieżkę elementu.  
  
 [in]`lpidl`  
 PIDL, która określa, że element  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`w przypadku powodzenia; `E_FAIL` inaczej.  
  
##  <a name="setflags"></a>CMFCShellTreeCtrl::SetFlags  
 Ustawia flagi do filtrowania kontekście drzewa.  
  
```  
void SetFlags(
    DWORD dwFlags,  
    BOOL bRefresh = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`dwFlags`  
 Flagi do ustawienia.  
  
 [in]`bRefresh`  
 Wartość logiczna określająca, czy `CMFCShellTreeCtrl` należy odświeżyć natychmiast.  
  
### <a name="remarks"></a>Uwagi  
 `CMFCShellTreeCtrl` Przekazuje wszystkie ustawione flagi na [IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066). Aby uzyskać więcej informacji na temat wartości flag różnych zobacz [IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066).  
  
##  <a name="setrelatedlist"></a>CMFCShellTreeCtrl::SetRelatedList  
 Kojarzy [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiekt z [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) obiektu.  
  
```  
void SetRelatedList(CMFCShellListCtrl* pShellList);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pShellList`  
 Wskaźnik do `CMFCShellListCtrl` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda kojarzy `CMFCShellListCtrl` z `CMFCShellTreeCtrl`. Te obiekty mogą być wyświetlane jako okno Eksploratora przypominającej: Jeśli użytkownik wybierze obiekt w `CMFCShellTreeCtrl`, skojarzone elementy `CMFCShellListCtrl` zostanie automatycznie zaktualizowana.  
  
 Użyj metody [CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist) można pobrać `CMFCShellListCtrl` skojarzone z `CMFCShellTreeCtrl`.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Ctreectrl — klasa](../../mfc/reference/ctreectrl-class.md)   
 [Klasa CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)
