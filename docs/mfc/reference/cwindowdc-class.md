---
title: Klasa CWindowDC
ms.date: 11/04/2016
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
ms.openlocfilehash: 89a822280ddebca942016f9a3a334a7128d8456a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371981"
---
# <a name="cwindowdc-class"></a>Klasa CWindowDC

Pochodzi z `CDC`.

## <a name="syntax"></a>Składnia

```
class CWindowDC : public CDC
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|Konstruuje `CWindowDC` obiekt.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CWindowDC::m_hWnd](#m_hwnd)|HWND, do `CWindowDC` którego jest dołączony.|

## <a name="remarks"></a>Uwagi

Wywołuje funkcję Systemu Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc)w czasie budowy i [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) w czasie zniszczenia. Oznacza to, `CWindowDC` że obiekt uzyskuje dostęp do całego obszaru ekranu [CWnd](../../mfc/reference/cwnd-class.md) (zarówno klienta, jak i obszarów nieklientów).

Aby uzyskać więcej `CWindowDC`informacji na temat korzystania z programu , zobacz [Konteksty urządzeń](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>Wymagania

Nagłówek: afxwin.h

## <a name="cwindowdccwindowdc"></a><a name="cwindowdc"></a>CWindowDC::CWindowDC

Konstruuje `CWindowDC` obiekt, który uzyskuje dostęp do całego obszaru ekranu `CWnd` (zarówno klienta, jak i nieklienta) obiektu wskazywany przez *pWnd*.

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Okno, do którego obszaru klienta będzie uzyskać dostęp obiekt kontekstu urządzenia.

### <a name="remarks"></a>Uwagi

Konstruktor wywołuje funkcję systemu Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc).

Wyjątek (typu) `CResourceException`jest zgłaszany, jeśli wywołanie systemu Windows `GetWindowDC` nie powiedzie się. Kontekst urządzenia może być niedostępny, jeśli system Windows przydzielił już wszystkie dostępne konteksty urządzeń. Aplikacja konkuruje o pięć typowych kontekstów wyświetlania dostępnych w danym momencie w systemie Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

## <a name="cwindowdcm_hwnd"></a><a name="m_hwnd"></a>CWindowDC::m_hWnd

HWND wskaźnika `CWnd` służy do konstruowania `CWindowDC` obiektu.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Uwagi

`m_hWnd`jest chroniona zmienna typu HWND.

### <a name="example"></a>Przykład

  Zobacz przykład [CWindowDC::CWindowDC](#cwindowdc).

## <a name="see-also"></a>Zobacz też

[Klasa CDC](../../mfc/reference/cdc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)
