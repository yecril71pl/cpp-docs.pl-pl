---
title: CWindowDC Class
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
ms.openlocfilehash: 55a9ccfc496c95c9e7410cbd5645135ee555ff26
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289354"
---
# <a name="cwindowdc-class"></a>CWindowDC Class

Pochodną `CDC`.

## <a name="syntax"></a>Składnia

```
class CWindowDC : public CDC
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|Konstruuje `CWindowDC` obiektu.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CWindowDC::m_hWnd](#m_hwnd)|HWND, do którego należy to `CWindowDC` jest dołączony.|

## <a name="remarks"></a>Uwagi

Wywołuje funkcję Windows [GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc)podczas konstruowania i [ReleaseDC](/windows/desktop/api/winuser/nf-winuser-releasedc) w trakcie niszczenia. Oznacza to, że `CWindowDC` obiekt uzyskuje dostęp do całego obszaru ekranu [CWnd](../../mfc/reference/cwnd-class.md) (obszary zarówno klient, jak i nieklienckie).

Aby uzyskać więcej informacji na temat korzystania z `CWindowDC`, zobacz [konteksty urządzenia](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>Wymagania

Nagłówek: afxwin.h

##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC

Konstruuje `CWindowDC` obiektu, który uzyskuje dostęp do całego obszaru ekranu (zarówno klient, jak i nieklienckie) `CWnd` obiekt wskazywany przez *pWnd*.

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Okno obszaru klienta, którego obiekt kontekstu urządzenia będą miały dostęp.

### <a name="remarks"></a>Uwagi

Konstruktor wywołuje funkcję Windows [GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc).

Wyjątek (typu `CResourceException`) jest generowany, jeśli Windows `GetWindowDC` wywołanie zakończy się niepowodzeniem. Kontekst urządzenia może nie być dostępne w przypadku Windows został już przydzielony wszystkie jego kontekstów dostępnego urządzenia. Aplikacja konkuruje dla pięciu typowych kontekstach wyświetlania dostępnych w danym momencie w obszarze Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd

HWND z `CWnd` wskaźnik jest używany do tworzenia `CWindowDC` obiektu.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Uwagi

`m_hWnd` jest chronione zmienną typu HWND.

### <a name="example"></a>Przykład

  Zobacz przykład [CWindowDC::CWindowDC](#cwindowdc).

## <a name="see-also"></a>Zobacz także

[Klasa CDC](../../mfc/reference/cdc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)
