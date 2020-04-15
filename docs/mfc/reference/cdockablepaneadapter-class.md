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
ms.openlocfilehash: 2fbaf99e4cc9bcbecf1a94012713b34e986f7ecb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375595"
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
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|Zwraca okno zawinięte.|
|[CDockablePaneAdapter::LoadState](#loadstate)|(Zastępuje [CDockablePane::LoadState](cdockablepane-class.md#loadstate).)|
|[CDockablePaneAdapter::Zapisz stan](#savestate)|(Zastępuje [CDockablePane::SaveState](cdockablepane-class.md).)|
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||

## <a name="remarks"></a>Uwagi

Zazwyczaj framework wywołuje obiekty tej klasy podczas korzystania z [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) lub [CMFCBaseTabCtrl::InsertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) metody.

Jeśli chcesz dostosować `CDockablePaneAdapter` zachowanie, po prostu wydziel nową klasę z niego i ustaw informacje o klasie run do okna z kartami przy użyciu [CMFCBaseTabCtrl::SetDockingBarWrapperRTC](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)\
&nbsp;-[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-[CDockablePane](../../mfc/reference/cdockablepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxDockablePaneAdapter.h

## <a name="cdockablepaneadaptergetwrappedwnd"></a><a name="getwrappedwnd"></a>CDockablePaneAdapter::GetWrappedWnd

Zwraca okno bazowe karty okienka dokowania.

```
virtual CWnd* GetWrappedWnd() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do zawiniętego okna.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do uzyskiwania dostępu do zawiniętego okna.

## <a name="cdockablepaneadapterloadstate"></a><a name="loadstate"></a>CDockablePaneAdapter::LoadState

Ładuje stan okienka z rejestru.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[w] Nazwa profilu.

*Nindex*<br/>
[w] Indeks profilu.

*Uiid*<br/>
[w] Identyfikator okienka.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdockablepaneadaptersavestate"></a><a name="savestate"></a>CDockablePaneAdapter::Zapisz stan

Zapisuje stan okienka w rejestrze.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[w] Nazwa profilu.

*Nindex*<br/>
[w] Indeks profilu (domyślnie identyfikator formantu okna).

*Uiid*<br/>
[w] Identyfikator okienka.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdockablepaneadaptersetwrappedwnd"></a><a name="setwrappedwnd"></a>CDockablePaneAdapter::SetWrappedWnd

Ustawia okno bazowe dla karty okienka dokowania.

```
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
[w] Wskaźnik do okna karty okienka do zawijania.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)
