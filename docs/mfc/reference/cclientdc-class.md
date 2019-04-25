---
title: Cclientdc — klasa
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
ms.openlocfilehash: a67af5d7d82b8bd7d0490d4ae6f9535bf3283ea2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206627"
---
# <a name="cclientdc-class"></a>Cclientdc — klasa

Zajmuje się wywoływanie funkcji Windows [getdc —](/windows/desktop/api/winuser/nf-winuser-getdc) podczas konstruowania i [ReleaseDC](/windows/desktop/api/winuser/nf-winuser-releasedc) w trakcie niszczenia.

## <a name="syntax"></a>Składnia

```
class CClientDC : public CDC
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CClientDC::CClientDC](#cclientdc)|Konstruuje `CClientDC` obiekt połączony `CWnd`.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CClientDC::m_hWnd](#m_hwnd)|HWND okna, w których `CClientDC` jest prawidłowy.|

## <a name="remarks"></a>Uwagi

Oznacza to, że kontekst urządzenia skojarzone z `CClientDC` obiekt jest w klienckim obszarze okna.

Aby uzyskać więcej informacji na temat `CClientDC`, zobacz [konteksty urządzenia](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="cclientdc"></a>  CClientDC::CClientDC

Konstruuje `CClientDC` obiektu, który uzyskuje dostęp do obszaru klienckiego [CWnd](../../mfc/reference/cwnd-class.md) wskazywany przez *pWnd*.

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Okno obszaru klienta, którego obiekt kontekstu urządzenia będą miały dostęp.

### <a name="remarks"></a>Uwagi

Konstruktor wywołuje funkcję Windows [getdc —](/windows/desktop/api/winuser/nf-winuser-getdc).

Wyjątek (typu `CResourceException`) jest generowany, jeśli Windows `GetDC` wywołanie zakończy się niepowodzeniem. Kontekst urządzenia może nie być dostępne w przypadku Windows został już przydzielony wszystkie jego kontekstów dostępnego urządzenia. Aplikacja konkuruje dla pięciu typowych kontekstach wyświetlania dostępnych w danym momencie w obszarze Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CClientDC::m_hWnd

`HWND` z `CWnd` wskaźnik użytego do stworzenia `CClientDC` obiektu.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Uwagi

*m_hWnd* jest zmienną chronionych.

### <a name="example"></a>Przykład

  Zobacz przykład [CClientDC::CClientDC](#cclientdc).

## <a name="see-also"></a>Zobacz także

[Próbki MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)
