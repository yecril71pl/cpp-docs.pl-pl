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
ms.openlocfilehash: d587f1cfa6ec38dd564da196da8130bffac11302
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503137"
---
# <a name="cpaintdc-class"></a>Klasa CPaintDC

Klasa kontekstu urządzenia pochodna w funkcji [przechwytywania](../../mfc/reference/cdc-class.md)zmian danych.

## <a name="syntax"></a>Składnia

```
class CPaintDC : public CDC
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|Tworzy połączenie z określonym CWnd. [](../../mfc/reference/cwnd-class.md) `CPaintDC`|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|Zawiera [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct) używany do malowania obszaru klienckiego.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|Właściwość HWND, do której `CPaintDC` jest dołączony ten obiekt.|

## <a name="remarks"></a>Uwagi

Wykonuje [CWnd:: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) w czasie konstruowania i [CWnd:: EndPaint](../../mfc/reference/cwnd-class.md#endpaint) w czasie niszczenia.

Obiektu można użyć tylko w odpowiedzi na komunikat `OnPaint` WM_PAINT, zwykle w funkcji składowej programu obsługi komunikatów. [](/windows/win32/gdi/wm-paint) `CPaintDC`

Aby uzyskać więcej informacji na `CPaintDC`temat korzystania z programu, zobacz [konteksty urządzeń](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="cpaintdc"></a>CPaintDC::CPaintDC

Konstruuje [](/windows/win32/api/winuser/ns-winuser-paintstruct) obiekt, przygotowuje okno aplikacji do malowania i przechowuje strukturę PAINTSTRUCT w zmiennej składowej [m_ps.](#m_ps) `CPaintDC`

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje obiekt, do którego należy `CPaintDC` obiekt. `CWnd`

### <a name="remarks"></a>Uwagi

Wyjątek (typu `CResourceException`) jest zgłaszany w przypadku niepowodzenia wywołania [GetDC —](/windows/win32/api/winuser/nf-winuser-getdc) systemu Windows. Kontekst urządzenia może nie być dostępny, jeśli system Windows już przydzielił wszystkie dostępne konteksty urządzenia. Twoja aplikacja konkuruje dla pięciu wspólnych kontekstów wyświetlania dostępnych w danym momencie w systemie Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

##  <a name="m_hwnd"></a>CPaintDC::m_hWnd

Do którego jest dołączony `CPaintDC` ten obiekt. `HWND`

```
HWND m_hWnd;
```

### <a name="remarks"></a>Uwagi

*m_hWnd* jest chronioną ZMIENNĄ typu HWND.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

##  <a name="m_ps"></a>  CPaintDC::m_ps

`m_ps`jest publiczną zmienną członkowską typu [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct).

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>Uwagi

Jest `PAINTSTRUCT` ona przenoszona do i wypełniana przez [CWnd:: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).

Zawiera informacje używane przez aplikację do malowania obszaru klienta okna skojarzonego `CPaintDC` z obiektem. `PAINTSTRUCT`

Należy pamiętać, że można uzyskać dostęp do uchwytu kontekstu urządzenia `PAINTSTRUCT`za pomocą. Można jednak bezpośrednio uzyskać dostęp do dojścia za pośrednictwem `m_hDC` zmiennej członkowskiej `CPaintDC` , która dziedziczy z przechwytywania zmian.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPaintDC:: m_hWnd](#m_hwnd).

## <a name="see-also"></a>Zobacz także

[Przykładowy interfejs MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
