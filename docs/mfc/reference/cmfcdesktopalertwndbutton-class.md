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
ms.openlocfilehash: 6d296966001dcbc2279a298bdd1d9c21195d61fd
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840782"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>Klasa CMFCDesktopAlertWndButton

Zezwala na dodawanie przycisków do okna dialogowego alertu pulpitu.

## <a name="syntax"></a>Składnia

```
class CMFCDesktopAlertWndButton : public CMFCButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|-|-|
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Konstruktor domyślny.|
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|-|-|
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|Określa, czy przycisk jest wyświetlany w obszarze podpisu okna dialogowego alertu.|
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|Określa, czy przycisk powoduje zamknięcie okna dialogowego alertu.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|-|-|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Wartość logiczna określająca, czy przycisk jest wyświetlany w obszarze podpisu okna dialogowego alertu.|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Wartość logiczna określająca, czy przycisk powoduje zamknięcie okna dialogowego alertu.|

### <a name="remarks"></a>Uwagi

Domyślnie Konstruktor ustawia `m_bIsCaptionButton` i `m_bIsCloseButton` składowe danych na wartość false. Obiekt nadrzędny `CMFCDesktopAlertDialog` `m_bIsCaptionButton` ma wartość true, jeśli przycisk jest umieszczony w obszarze podpisu okna dialogowego alertu. `CMFCDesktopAlertDialog`Klasa tworzy `CMFCDesktopAlertWndButton` obiekt, który służy jako przycisk, który zamyka okno dialogowe alertu i ustawia `m_bIsCloseButton` wartość true.

Dodaj `CMFCDesktopAlertWndButton` obiekty do `CMFCDesktopAlertDialog` obiektu, tak jak dodasz dowolny przycisk. Aby uzyskać więcej informacji na temat `CMFCDesktopAlertDialog` , zobacz [Klasa CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia `SetImage` metody w `CMFCDesktopAlertWndButton` klasie. Ten fragment kodu jest częścią [przykładu pokazu alertu na pulpicie](../../overview/visual-cpp-samples.md).

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

**Nagłówek:** afxdesktopalertwnd. h

## <a name="cmfcdesktopalertwndbuttoniscaptionbutton"></a><a name="iscaptionbutton"></a> CMFCDesktopAlertWndButton::IsCaptionButton

Określa, czy przycisk jest wyświetlany w obszarze podpisu okna dialogowego alertu.

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli przycisk jest wyświetlany w obszarze podpisu okna dialogowego alertu; w przeciwnym razie 0.

## <a name="cmfcdesktopalertwndbuttonisclosebutton"></a><a name="isclosebutton"></a> CMFCDesktopAlertWndButton::IsCloseButton

Określa, czy przycisk powoduje zamknięcie okna dialogowego alertu.

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli przycisk powoduje zamknięcie okna dialogowego alertu; w przeciwnym razie 0.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)
