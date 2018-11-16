---
title: Klasa CMFCShellTreeCtrl
ms.date: 11/04/2016
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
ms.openlocfilehash: cf7e5f9c9b44524491737b27098bc91bb472cb32
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694288"
---
# <a name="cmfcshelltreectrl-class"></a>Klasa CMFCShellTreeCtrl

`CMFCShellTreeCtrl` Klasa rozszerza [klasa CTreeCtrl](../../mfc/reference/ctreectrl-class.md) funkcji, wyświetlając hierarchię elementów powłoki.

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.
## <a name="syntax"></a>Składnia

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Włącza lub wyłącza menu skrótów.|
|[CMFCShellTreeCtrl::GetFlags](#getflags)|Zwraca kombinacja flag, które są przekazywane do [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Pobiera ścieżkę do elementu.|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|Zwraca wskaźnik do [klasa CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiekt, który jest używany razem z tym `CMFCShellTreeCtrl` obiekt do utworzenia okna Eksploratora podobne.|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|Ta funkcja członkowska jest wywoływana przez okno nadrzędne tego okna, po odebraniu komunikatu powiadomienia, która ma zastosowanie do tego okna. (Przesłania [CWnd::OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl::Refresh](#refresh)|Odświeża i Odświeża bieżący `CMFCShellTreeCtrl` obiektu.|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Wybiera odpowiedni element formantu drzewa na podstawie podanej PIDL lub ciąg ścieżki.|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Ustawia flagi, aby filtrować kontekście drzewa (podobnie jak flagi używane przez `IShellFolder::EnumObjects`).|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Określa relację między bieżącą `CMFCShellTreeCtrl` obiektu i `CMFCShellListCtrl` obiektu.|

## <a name="remarks"></a>Uwagi

Ta klasa rozszerza `CTreeCtrl` klasy, należy włączyć program, aby uwzględnić powłoki Windows elementy w drzewie. Ta klasa może być skojarzony z `CMFCShellListCtrl` obiekt, aby utworzyć pełną okno Eksploratora. Następnie wybranie elementu w drzewie spowoduje wyświetlenie listy elementów powłoki Windows na skojarzonej liście.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxshelltreeCtrl.h

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób tworzenia obiektu `CMFCShellTreeCtrl` klasy. Ten fragment kodu jest częścią [Eksplorator kondycji](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

##  <a name="enableshellcontextmenu"></a>  CMFCShellTreeCtrl::EnableShellContextMenu

Umożliwia menu skrótów.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Wartość logiczna określająca, czy włączyć menu skrótów.

##  <a name="getflags"></a>  CMFCShellTreeCtrl::GetFlags

Zwraca wartość flag ustawionych dla [klasa CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) obiektu.

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>Wartość zwracana

Ustaw wartość DWORD, który obecnie określa kombinacja flag.

### <a name="remarks"></a>Uwagi

Flagi ustawić w `CMFCShellTreeCtrl` są wysyłane do metody [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) zawsze, gdy obiekt jest odświeżany. Można zmienić flagi z [CMFCShellTreeCtrl::SetFlags](#setflags) metody.

##  <a name="getitempath"></a>  CMFCShellTreeCtrl::GetItemPath

Pobiera ścieżkę elementu [klasa CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) obiektu.

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>Parametry

*strPath*<br/>
[out] Odwołanie do parametru ciągu. Metoda zapisuje ścieżka elementu do tego parametru.

*htreeItem*<br/>
[in] Metoda pobiera ścieżki dla tego elementu kontrolki drzewa.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda nie powiedzie się, *strPath* zawiera pusty ciąg.

Jeśli nie określisz *hTreeItem*, ta metoda próbuje uzyskać ciąg dla aktualnie wybranego elementu. Jeśli nie wybrano elementu i *hTreeItem* ma wartość NULL, ta metoda nie powiedzie się.

##  <a name="getrelatedlist"></a>  CMFCShellTreeCtrl::GetRelatedList

Zwraca wskaźnik do [klasa CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiektu, który jest skojarzony z tym [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) obiektu.

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CMFCShellListCtrl` obiekt, który jest skojarzony z tym obiektem formantu drzewa.

### <a name="remarks"></a>Uwagi

Za pomocą `CMFCShellListCtrl` obiektu wraz z `CMFCShellTreeCtrl` obiektu, można utworzyć okna Eksploratora podobne. Użyj metody [CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist) do skojarzenia z dwóch klas. Po ich skojarzone zakresie automatycznie aktualizuje `CMFCShellListCtrl` Jeśli zaznaczenie w `CMFCShellTreeCtrl` zmiany.

##  <a name="onchildnotify"></a>  CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>Parametry

[in] *wiadomości*<br/>
[in] *wParam*<br/>
[in] *lParam*<br/>
[in] *pLResult*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ongetitemicon"></a>  CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

[in] *pItem*<br/>
[in] *bSelected*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ongetitemtext"></a>  CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

[in] *pItem*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="refresh"></a>  CMFCShellTreeCtrl::Refresh

Odświeża i odświeża [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md).

```
void Refresh();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby odświeżyć hierarchię elementów wyświetlanych w `CMFCShellTreeCtrl`.

##  <a name="selectpath"></a>  CMFCShellTreeCtrl::SelectPath

Wybiera element [klasa CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) na podstawie podanej ścieżki.

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
[in] Ciąg, który określa ścieżkę elementu.

*lpidl*<br/>
[in] PIDL, która określa, że element

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; W przeciwnym razie E_FAIL.

##  <a name="setflags"></a>  CMFCShellTreeCtrl::SetFlags

Ustawia flagi, aby filtrować kontekście drzewa.

```
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>Parametry

*Flagidw*<br/>
[in] Flagi, aby ustawić.

*bRefresh*<br/>
[in] Wartość logiczna określająca czy `CMFCShellTreeCtrl` powinny być natychmiast odświeżane.

### <a name="remarks"></a>Uwagi

`CMFCShellTreeCtrl` Przekazuje wszystkie ustawione flagi na [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects). Aby uzyskać więcej informacji na temat wartości różnych flag zobacz [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).

##  <a name="setrelatedlist"></a>  CMFCShellTreeCtrl::SetRelatedList

Kojarzy [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) obiekt z [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) obiektu.

```
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>Parametry

*pShellList*<br/>
[in] Wskaźnik do `CMFCShellListCtrl` obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda kojarzy `CMFCShellListCtrl` z `CMFCShellTreeCtrl`. Te obiekty mogą być wyświetlane jako okno Eksploratora przypominającej: Jeśli użytkownik wybierze obiekt w `CMFCShellTreeCtrl`, skojarzone elementy w `CMFCShellListCtrl` zostaną automatycznie zaktualizowane.

Użyj metody [CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist) można pobrać `CMFCShellListCtrl` skojarzone z `CMFCShellTreeCtrl`.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CTreeCtrl](../../mfc/reference/ctreectrl-class.md)<br/>
[Klasa CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)
