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
ms.openlocfilehash: 0ef9b4917dc834eb8335690f9b0d171245f5c170
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502150"
---
# <a name="cwindowdc-class"></a>Klasa CWindowDC

Pochodny `CDC`od.

## <a name="syntax"></a>Składnia

```
class CWindowDC : public CDC
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|Konstruuje `CWindowDC` obiekt.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CWindowDC::m_hWnd](#m_hwnd)|Właściwość HWND, do której `CWindowDC` jest dołączony.|

## <a name="remarks"></a>Uwagi

Wywołuje funkcję systemu Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc)w czasie konstruowania i [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) w czasie niszczenia. Oznacza to, że `CWindowDC` obiekt uzyskuje dostęp do całego obszaru ekranu [CWnd](../../mfc/reference/cwnd-class.md) (obszary klienta i nieklienckie).

Aby uzyskać więcej informacji na `CWindowDC`temat korzystania z programu, zobacz [konteksty urządzeń](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>Wymagania

Nagłówek: afxwin. h

##  <a name="cwindowdc"></a>CWindowDC::CWindowDC

Konstruuje `CWnd` obiekt, który uzyskuje dostęp do całego obszaru ekranu (zarówno klienta, jak i nieklienckiego) obiektu wskazywanego przez *pWnd.* `CWindowDC`

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Okno, którego obszar klienta ma dostęp do obiektu kontekstu urządzenia.

### <a name="remarks"></a>Uwagi

Konstruktor wywołuje funkcję systemu Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc).

Wyjątek (typu `CResourceException`) jest zgłaszany w przypadku niepowodzenia `GetWindowDC` wywołania systemu Windows. Kontekst urządzenia może nie być dostępny, jeśli system Windows już przydzielił wszystkie dostępne konteksty urządzenia. Twoja aplikacja konkuruje dla pięciu wspólnych kontekstów wyświetlania dostępnych w danym momencie w systemie Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd

Właściwość HWND `CWnd` wskaźnika służy do `CWindowDC` konstruowania obiektu.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Uwagi

`m_hWnd`jest chronioną zmienną typu HWND.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CWindowDC:: CWindowDC](#cwindowdc).

## <a name="see-also"></a>Zobacz także

[Klasa CDC](../../mfc/reference/cdc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)
