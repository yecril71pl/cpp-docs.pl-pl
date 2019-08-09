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
ms.openlocfilehash: 88c125c63f9dbfe272f5d543e996366575fc533b
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866221"
---
# <a name="cdockablepaneadapter-class"></a>Klasa CDockablePaneAdapter

Zapewnia obsługę dokowania dla `CWnd`okienek pochodnych.

## <a name="syntax"></a>Składnia

```
class CDockablePaneAdapter : public CDockablePane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|Zwraca opakowane okno.|
|[CDockablePaneAdapter:: LoadState](#loadstate)|(Przesłania [CDockablePane:: LoadState](cdockablepane-class.md#loadstate).)|
|[CDockablePaneAdapter:: SaveState](#savestate)|(Przesłania [CDockablePane:: SaveState](cdockablepane-class.md).)|
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||

## <a name="remarks"></a>Uwagi

Zazwyczaj struktura tworzy wystąpienia obiektów tej klasy w przypadku używania metod [CMFCBaseTabCtrl:: AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) lub [CMFCBaseTabCtrl:: InsertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) .

Jeśli chcesz dostosować `CDockablePaneAdapter` zachowanie, po prostu Utwórz nową klasę od niej i Ustaw informacje o klasie środowiska uruchomieniowego w oknie z kartami przy użyciu [CMFCBaseTabCtrl:: SetDockingBarWrapperRTC](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CDockablePane](../../mfc/reference/cdockablepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxDockablePaneAdapter. h

##  <a name="getwrappedwnd"></a>CDockablePaneAdapter::GetWrappedWnd

Zwraca okno bazowe dla karty okienka było dokować.

```
virtual CWnd* GetWrappedWnd() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do zapakowanego okna.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji, aby uzyskać dostęp do opakowanego okna.

##  <a name="loadstate"></a>CDockablePaneAdapter:: LoadState

Ładuje stan okienka z rejestru.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
podczas Nazwa profilu.

*nIndex*<br/>
podczas Indeks profilu.

*uiID*<br/>
podczas Identyfikator okienka.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="savestate"></a>CDockablePaneAdapter:: SaveState

Zapisuje stan okienka w rejestrze.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
podczas Nazwa profilu.

*nIndex*<br/>
podczas Indeks profilu (domyślnie jest to identyfikator kontrolki okna).

*uiID*<br/>
podczas Identyfikator okienka.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="setwrappedwnd"></a>CDockablePaneAdapter::SetWrappedWnd

Ustawia okno bazowe dla karty okienka było dokować.

```
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
podczas Wskaźnik do okna dla karty okienka do zawinięcia.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)
