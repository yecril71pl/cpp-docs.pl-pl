---
title: Cpaintdc — klasa
ms.date: 11/04/2016
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
helpviewer_keywords:
- CPaintDC [MFC], CPaintDC
- CPaintDC [MFC], m_ps
- CPaintDC [MFC], m_hWnd
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
ms.openlocfilehash: e4e6ded945bac15b6584eadc21d8648f1a0f9ab3
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178333"
---
# <a name="cpaintdc-class"></a>Cpaintdc — klasa

Kontekst urządzenia klasą pochodną [CDC](../../mfc/reference/cdc-class.md).

## <a name="syntax"></a>Składnia

```
class CPaintDC : public CDC
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|Konstruuje `CPaintDC` podłączone do określonego [CWnd](../../mfc/reference/cwnd-class.md).|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|Zawiera [PAINTSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagpaintstruct) używany do rysowania obszaru klienta.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|HWND, do którego należy to `CPaintDC` obiekt jest dołączony.|

## <a name="remarks"></a>Uwagi

Wykonuje [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) podczas konstruowania i [CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint) w trakcie niszczenia.

A `CPaintDC` obiekt może być używany tylko w przypadku reagowania na [WM_PAINT](/windows/desktop/gdi/wm-paint) komunikatu, zazwyczaj w swojej `OnPaint` funkcja elementu członkowskiego program obsługi komunikatów.

Aby uzyskać więcej informacji na temat korzystania z `CPaintDC`, zobacz [konteksty urządzenia](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[PRZECHWYTYWANIE ZMIAN DANYCH](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="cpaintdc"></a>  CPaintDC::CPaintDC

Konstruuje `CPaintDC` przygotowuje okna aplikacji rysowania obiektu i przechowuje [PAINTSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagpaintstruct) struktury w [m_ps](#m_ps) zmiennej składowej.

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje `CWnd` obiekt, do którego `CPaintDC` należy obiekt.

### <a name="remarks"></a>Uwagi

Wyjątek (typu `CResourceException`) jest generowany, jeśli Windows [getdc —](/windows/desktop/api/winuser/nf-winuser-getdc) wywołanie zakończy się niepowodzeniem. Kontekst urządzenia może nie być dostępne w przypadku Windows został już przydzielony wszystkie jego kontekstów dostępnego urządzenia. Aplikacja konkuruje dla pięciu typowych kontekstach wyświetlania dostępnych w danym momencie w obszarze Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CPaintDC::m_hWnd

`HWND` Do którego należy to `CPaintDC` obiekt jest dołączony.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Uwagi

*m_hWnd* jest chroniony zmienną typu HWND.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

##  <a name="m_ps"></a>  CPaintDC::m_ps

`m_ps` jest to zmienna członka publicznego typu [PAINTSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagpaintstruct).

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>Uwagi

Jest `PAINTSTRUCT` który jest przekazywany do i wypełnione przez [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).

`PAINTSTRUCT` Zawiera informacje, którego używa aplikacja do malowania obszaru klienckiego okna skojarzony `CPaintDC` obiektu.

Należy pamiętać, dostęp uchwyt kontekstu urządzenia za pośrednictwem `PAINTSTRUCT`. Można jednak uzyskać dostępu uchwyt bardziej bezpośrednio za pośrednictwem `m_hDC` zmiennej składowej, `CPaintDC` dziedziczy przechwytywania zmian danych.

### <a name="example"></a>Przykład

  Zobacz przykład [CPaintDC::m_hWnd](#m_hwnd).

## <a name="see-also"></a>Zobacz też

[Próbki MFC MDI](../../visual-cpp-samples.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)

