---
title: Cclientdc — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3aa255552156fe0bbcb671f39afdcb966e7157ea
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422184"
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

[PRZECHWYTYWANIE ZMIAN DANYCH](../../mfc/reference/cdc-class.md)

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

## <a name="see-also"></a>Zobacz też

[Próbki MFC MDI](../../visual-cpp-samples.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)
