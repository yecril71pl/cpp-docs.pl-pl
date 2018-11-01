---
title: Klasa CDockablePaneAdapter
ms.date: 11/04/2016
f1_keywords:
- CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::GetWrappedWnd
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::LoadState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SaveState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SetWrappedWnd
helpviewer_keywords:
- CDockablePaneAdapter [MFC], GetWrappedWnd
- CDockablePaneAdapter [MFC], LoadState
- CDockablePaneAdapter [MFC], SaveState
- CDockablePaneAdapter [MFC], SetWrappedWnd
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
ms.openlocfilehash: 6088d7ed9f4d8f54bfe5ea7f7b77cdabfd11768f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522957"
---
# <a name="cdockablepaneadapter-class"></a>Klasa CDockablePaneAdapter

Dodano obsługę dokującej `CWnd`-pochodnych okienek.

## <a name="syntax"></a>Składnia

```
class CDockablePaneAdapter : public CDockablePane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|Zwraca okno opakowana.|
|[CDockablePaneAdapter::LoadState](#loadstate)|(Przesłania [CDockablePane::LoadState](cdockablepane-class.md#loadstate).)|
|[CDockablePaneAdapter::SaveState](#savestate)|(Przesłania [CDockablePane::SaveState](cdockablepane-class.md).)|
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||

## <a name="remarks"></a>Uwagi

Zazwyczaj ramach tworzy obiekty tej klasy, gdy używasz [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) lub [CMFCBaseTabCtrl::InsertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) metody.

Jeśli chcesz dostosować `CDockablePaneAdapter` zachowanie, po prostu dziedziczyć po nim nową klasę i ustaw informacje o klasie czasu wykonywania do okna z kartami za pomocą [CMFCBaseTabCtrl::SetDockingBarWrapperRTC](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxDockablePaneAdapter.h

##  <a name="getwrappedwnd"></a>  CDockablePaneAdapter::GetWrappedWnd

Zwraca okna bazowego dla karty dokowalne okienka.

```
virtual CWnd* GetWrappedWnd() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna opakowana.

### <a name="remarks"></a>Uwagi

Aby uzyskać dostęp do okna opakowana, należy użyć tej funkcji.

##  <a name="loadstate"></a>  CDockablePaneAdapter::LoadState

Ładuje stan okienka z rejestru.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Nazwa profilu.

*nIndex*<br/>
[in] Indeks profilu.

*uiID*<br/>
[in] Identyfikator okienka.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="savestate"></a>  CDockablePaneAdapter::SaveState

Zapisuje stan okienka w rejestrze.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Nazwa profilu.

*nIndex*<br/>
[in] Indeks profilu (wartość domyślna to identyfikator formantu okna).

*uiID*<br/>
[in] Identyfikator okienka.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="setwrappedwnd"></a>  CDockablePaneAdapter::SetWrappedWnd

Ustawia okno podstawowej karty dokowalne okienka.

```
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Wskaźnik do okna karty okienko do opakowania.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)
