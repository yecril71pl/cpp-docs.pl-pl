---
title: Klasa CClientDC
ms.date: 11/04/2016
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
helpviewer_keywords:
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
ms.openlocfilehash: abe8a3220fd37a0375fcf37504c715edf4c6962e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352296"
---
# <a name="cclientdc-class"></a>Klasa CClientDC

Zajmuje się wywoływaniem funkcji systemu Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) w czasie budowy i [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) w czasie zniszczenia.

## <a name="syntax"></a>Składnia

```
class CClientDC : public CDC
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CClientDC::CClientDC](#cclientdc)|Konstruuje `CClientDC` obiekt połączony `CWnd`z obiektem .|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CClientDC::m_hWnd](#m_hwnd)|HWND okna, dla którego `CClientDC` jest to prawidłowe.|

## <a name="remarks"></a>Uwagi

Oznacza to, że kontekst urządzenia `CClientDC` skojarzony z obiektem jest obszarem klienta okna.

Aby uzyskać `CClientDC`więcej informacji na temat , zobacz [Konteksty urządzeń](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cclientdccclientdc"></a><a name="cclientdc"></a>CClientDC::CClientDC

Konstruuje `CClientDC` obiekt, który uzyskuje dostęp do obszaru klienta [CWnd](../../mfc/reference/cwnd-class.md) wskazywał przez *pWnd*.

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Okno, do którego obszaru klienta będzie dostępny obiekt kontekstu urządzenia.

### <a name="remarks"></a>Uwagi

Konstruktor wywołuje funkcję Systemu Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc).

Wyjątek (typu) `CResourceException`jest zgłaszany, jeśli wywołanie systemu Windows `GetDC` nie powiedzie się. Kontekst urządzenia może być niedostępny, jeśli system Windows przydzielił już wszystkie dostępne konteksty urządzeń. Aplikacja konkuruje o pięć typowych kontekstów wyświetlania dostępnych w danym momencie w systemie Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

## <a name="cclientdcm_hwnd"></a><a name="m_hwnd"></a>CClientDC::m_hWnd

Wskaźnik używany do konstruowania `CClientDC` obiektu. `HWND` `CWnd`

```
HWND m_hWnd;
```

### <a name="remarks"></a>Uwagi

*m_hWnd* jest zmienną chroniona.

### <a name="example"></a>Przykład

  Zobacz przykład [CClientDC::CClientDC](#cclientdc).

## <a name="see-also"></a>Zobacz też

[Przykładowy MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)
