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
ms.openlocfilehash: 5b18a15f8bfd98396acae0558d121b32bc4127c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367624"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>Klasa CMFCDesktopAlertWndButton

Umożliwia dodawanie przycisków do okna dialogowego alertów na pulpicie.

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
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|Określa, czy przycisk jest wyświetlany w obszarze podpisu okna dialogowego alertu.|
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|Określa, czy przycisk zamyka okno dialogowe alertu.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|Nazwa|Opis|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Wartość logiczna określająca, czy przycisk jest wyświetlany w obszarze podpisu okna dialogowego alertu.|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Wartość logiczna określająca, czy przycisk zamyka okno dialogowe alertu.|

### <a name="remarks"></a>Uwagi

Domyślnie konstruktor ustawia `m_bIsCaptionButton` `m_bIsCloseButton` elementy członkowskie i danych na FALSE. Obiekt `CMFCDesktopAlertDialog` nadrzędny `m_bIsCaptionButton` ustawia wartość PRAWDA, jeśli przycisk znajduje się w obszarze podpisu okna dialogowego alertu. Klasa `CMFCDesktopAlertDialog` tworzy `CMFCDesktopAlertWndButton` obiekt, który służy jako przycisk, który zamyka `m_bIsCloseButton` okno dialogowe alertu i ustawia wartość TRUE.

Dodaj `CMFCDesktopAlertWndButton` obiekty `CMFCDesktopAlertDialog` do obiektu w taki sposób, aby dodać dowolny przycisk. Aby uzyskać `CMFCDesktopAlertDialog`więcej informacji na temat , zobacz [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `SetImage` metody w `CMFCDesktopAlertWndButton` klasie. Ten fragment kodu jest częścią [przykładu demo alertów pulpitu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cbutton](../../mfc/reference/cbutton-class.md)

[Cmfcbutton](../../mfc/reference/cmfcbutton-class.md)

[CMFCDesktopAlertWbutton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdesktopalertwnd.h

## <a name="cmfcdesktopalertwndbuttoniscaptionbutton"></a><a name="iscaptionbutton"></a>CMFCDesktopAlertWndButton::IsCaptionButton

Określa, czy przycisk jest wyświetlany w obszarze podpisu okna dialogowego alertu.

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli przycisk jest wyświetlany w obszarze podpisu okna dialogowego alertu; w przeciwnym razie 0.

## <a name="cmfcdesktopalertwndbuttonisclosebutton"></a><a name="isclosebutton"></a>CMFCDesktopAlertWndButton::IsCloseButton

Określa, czy przycisk zamyka okno dialogowe alertu.

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli przycisk zamyka okno dialogowe alertu; w przeciwnym razie 0.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)
