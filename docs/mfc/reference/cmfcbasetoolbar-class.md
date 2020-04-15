---
title: Klasa CMFCBaseToolBar
ms.date: 11/04/2016
f1_keywords:
- CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar::GetDockingMode
- AFXBASETOOLBAR/CMFCBaseToolBar::GetMinSize
- AFXBASETOOLBAR/CMFCBaseToolBar::OnAfterChangeParent
helpviewer_keywords:
- CMFCBaseToolBar [MFC], GetDockingMode
- CMFCBaseToolBar [MFC], GetMinSize
- CMFCBaseToolBar [MFC], OnAfterChangeParent
ms.assetid: 5d79206d-55e4-46f8-b1b8-042e34d7f9da
ms.openlocfilehash: 027fe8569ff133bb3f348c9d0607f19c6d778c4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367827"
---
# <a name="cmfcbasetoolbar-class"></a>Klasa CMFCBaseToolBar

Klasa podstawowa dla pasków narzędzi.

## <a name="syntax"></a>Składnia

```
class CMFCBaseToolBar : public CPane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCBaseToolBar::CMFCBaseToolBar`|Domyślny konstruktor.|
|`CMFCBaseToolBar::~CMFCBaseToolBar`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCBaseToolBar::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|[CMFCBaseToolBar::GetDockingMode](#getdockingmode)|Zwraca tryb dokowania. (Zastępuje [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).)|
|[CMFCBaseToolBar::GetMinSize](#getminsize)|Zwraca minimalny rozmiar paska narzędzi. (Zastępuje [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CMFCBaseToolBar::OnAfterChangeParent](#onafterchangeparent)|Wywoływane przez strukturę po zmianie nadrzędnego okienka. (Zastępuje [CBasePane::OnAfterChangeParent](../../mfc/reference/cbasepane-class.md#onafterchangeparent).)|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Panel CBasePane](../../mfc/reference/cbasepane-class.md)

[Cpane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxbasetoolbar.h

## <a name="cmfcbasetoolbargetdockingmode"></a><a name="getdockingmode"></a>CMFCBaseToolBar::GetDockingMode

Zwraca tryb dokowania.

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Tryb dokowania.

## <a name="cmfcbasetoolbargetminsize"></a><a name="getminsize"></a>CMFCBaseToolBar::GetMinSize

Zwraca minimalny rozmiar paska narzędzi.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
[na zewnątrz] Minimalny rozmiar paska narzędzi.

## <a name="cmfcbasetoolbaronafterchangeparent"></a><a name="onafterchangeparent"></a>CMFCBaseToolBar::OnAfterChangeParent

Wywoływane przez strukturę po zmianie nadrzędnego okienka.

```
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```

### <a name="parameters"></a>Parametry

*pWndOldParent*<br/>
[w] Wskaźnik do poprzedniego okna nadrzędnego.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
