---
title: Klasa CPaintDC
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
ms.openlocfilehash: 55342b03454a6dba07bc10ea5f0464c34e0e8db3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374776"
---
# <a name="cpaintdc-class"></a>Klasa CPaintDC

Klasa kontekstu urządzenia pochodząca z [CDC](../../mfc/reference/cdc-class.md).

## <a name="syntax"></a>Składnia

```
class CPaintDC : public CDC
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|Konstruuje `CPaintDC` połączenie z określonym [CWnd](../../mfc/reference/cwnd-class.md).|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|Zawiera [paintstruct](/windows/win32/api/winuser/ns-winuser-paintstruct) używany do malowania obszaru klienta.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|HWND, do `CPaintDC` którego jest dołączony ten obiekt.|

## <a name="remarks"></a>Uwagi

Wykonuje [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) w czasie budowy i [CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint) w czasie zniszczenia.

Obiekt `CPaintDC` może być używany tylko podczas odpowiadania na wiadomość `OnPaint` [WM_PAINT,](/windows/win32/gdi/wm-paint) zwykle w funkcji elementu członkowskiego obsługi wiadomości.

Aby uzyskać więcej `CPaintDC`informacji na temat korzystania z programu , zobacz [Konteksty urządzeń](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cpaintdccpaintdc"></a><a name="cpaintdc"></a>CPaintDC::CPaintDC

Konstruuje `CPaintDC` obiekt, przygotowuje okno aplikacji do malowania i przechowuje strukturę [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct) w [zmiennej m_ps](#m_ps) element członkowski.

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskazuje obiekt, `CWnd` do `CPaintDC` którego należy obiekt.

### <a name="remarks"></a>Uwagi

Wyjątek (typu) `CResourceException`jest zgłaszany, jeśli wywołanie [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) systemu Windows nie powiedzie się. Kontekst urządzenia może być niedostępny, jeśli system Windows przydzielił już wszystkie dostępne konteksty urządzeń. Aplikacja konkuruje o pięć typowych kontekstów wyświetlania dostępnych w danym momencie w systemie Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

## <a name="cpaintdcm_hwnd"></a><a name="m_hwnd"></a>CPaintDC::m_hWnd

Do `HWND` którego `CPaintDC` dołączony jest ten obiekt.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Uwagi

*m_hWnd* jest chroniona zmienna typu HWND.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

## <a name="cpaintdcm_ps"></a><a name="m_ps"></a>CPaintDC::m_ps

`m_ps`jest publiczną zmienną członkowniczą typu [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct).

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>Uwagi

Jest `PAINTSTRUCT` to, który jest przekazywany i wypełniany przez [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).

Zawiera `PAINTSTRUCT` informacje, które aplikacja używa do malowania obszaru klienta `CPaintDC` okna skojarzonego z obiektem.

Należy zauważyć, że można uzyskać dostęp `PAINTSTRUCT`do uchwytu kontekstu urządzenia za pośrednictwem pliku . Jednak można uzyskać dostęp do dojścia bardziej bezpośrednio za pośrednictwem zmiennej członkowskiej, `m_hDC` która `CPaintDC` dziedziczy z CDC.

### <a name="example"></a>Przykład

  Zobacz przykład [CPaintDC::m_hWnd](#m_hwnd).

## <a name="see-also"></a>Zobacz też

[Przykładowy MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
