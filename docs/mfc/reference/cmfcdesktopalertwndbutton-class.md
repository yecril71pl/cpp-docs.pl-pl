---
title: Klasa CMFCDesktopAlertWndButton
ms.date: 11/04/2016
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
ms.openlocfilehash: 2a9ade332c87f293719872e426fb459b011d2d35
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270267"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>Klasa CMFCDesktopAlertWndButton

Umożliwia przycisków, które mają zostać dodane do dialogowego alertu pulpitu.

## <a name="syntax"></a>Składnia

```
class CMFCDesktopAlertWndButton : public CMFCButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Domyślny konstruktor.|
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|Określa, czy przycisk jest wyświetlany w obszarze Podpis okna dialogowego alertu.|
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|Określa, czy przycisk powoduje zamknięcie okna dialogowego alertu.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|Nazwa|Opis|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Wartość logiczna określająca, czy przycisk jest wyświetlany w obszarze Podpis okna dialogowego alertu.|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Wartość logiczna określająca, czy przycisk powoduje zamknięcie okna dialogowego alertu.|

### <a name="remarks"></a>Uwagi

Domyślnie ustawia konstruktora `m_bIsCaptionButton` i `m_bIsCloseButton` elementy członkowskie danych na wartość FALSE. Element nadrzędny `CMFCDesktopAlertDialog` obiektu zestawy `m_bIsCaptionButton` na wartość TRUE, jeśli przycisk znajduje się w obszarze Podpis okna dialogowego alertu. `CMFCDesktopAlertDialog` Tworzy klasę `CMFCDesktopAlertWndButton` obiekt, który służy jako przycisk, który powoduje zamknięcie okna dialogowego alertu pole, a także ustawia `m_bIsCloseButton` na wartość TRUE.

Dodaj `CMFCDesktopAlertWndButton` obiekty do `CMFCDesktopAlertDialog` obiektu, jak dowolnego przycisku. Aby uzyskać więcej informacji na temat `CMFCDesktopAlertDialog`, zobacz [klasa CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `SetImage` method in Class metoda `CMFCDesktopAlertWndButton` klasy. Ten fragment kodu jest częścią [próbka Demo alertu pulpitu](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdesktopalertwnd.h

##  <a name="iscaptionbutton"></a>  CMFCDesktopAlertWndButton::IsCaptionButton

Określa, czy przycisk jest wyświetlany w obszarze Podpis okna dialogowego alertu.

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli ten przycisk jest wyświetlany w obszarze Podpis okna dialogowego alertu; w przeciwnym razie 0.

##  <a name="isclosebutton"></a>  CMFCDesktopAlertWndButton::IsCloseButton

Określa, czy przycisk powoduje zamknięcie okna dialogowego alertu.

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli przycisk zamknięcie okna dialogowego alertu; w przeciwnym razie 0.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)
