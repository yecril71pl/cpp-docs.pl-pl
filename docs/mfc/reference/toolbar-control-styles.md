---
title: Style formantu ToolBar
ms.date: 11/04/2016
helpviewer_keywords:
- ToolBar control styles [MFC]
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
ms.openlocfilehash: eab4dbde68fcebdb0afd0d058b4678c464874c81
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837128"
---
# <a name="toolbar-control-styles"></a>Style formantu ToolBar

[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) ma zestaw flag stylu, które określają wygląd i zachowanie przycisku. Można ustawić kombinację tych flag przez wywołanie [CMFCToolBarButton:: SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle). W tym temacie wymieniono wartości flag stylu i ich znaczenie.

## <a name="property-values"></a>Wartości właściwości

Następujące wartości określają typ przycisku reprezentowanego przez formant:

|Nazwa|Opis|
|-|-|
|TBBS_BUTTON|Standardowy przycisk (domyślnie).  |
|TBBS_CHECKBOX|Pole wyboru.  |
|TBBS_CHECKGROUP|Początek grupy pól wyboru.  |
|TBBS_GROUP|Początek grupy przycisków.  |
|TBBS_SEPARATOR|Rozdzielając.  |

Następujące wartości reprezentują bieżący stan formantu:

|Nazwa|Opis|
|-|-|
|TBBS_CHECKED|Pole wyboru jest zaznaczone.  |
|TBBS_DISABLED|Kontrolka jest wyłączona.  |
|TBBS_INDETERMINATE|Pole wyboru jest w nieokreślonym stanie.  |
|TBBS_PRESSED|Przycisk został naciśnięty.  |

Poniższa wartość zmienia układ przycisku na pasku narzędzi:

|Nazwa|Opis|
|-|-|
|TBBS_BREAK|Umieszcza element w nowym wierszu lub w nowej kolumnie bez rozdzielania kolumn.  |

## <a name="remarks"></a>Uwagi

Bieżący styl jest przechowywany w [CMFCToolBarButton:: m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle). Nie ustawiaj nowej wartości                 `m_nStyle` bezpośrednio, ponieważ niektóre klasy pochodne wykonują dodatkowe przetwarzanie podczas wywoływania `SetStyles` .

Program Visual Manager określa wygląd przycisków w poszczególnych Stanach. Aby uzyskać więcej informacji, zobacz [Menedżer wizualizacji](../../mfc/visualization-manager.md) .

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbarbutton. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Menedżer wizualizacji](../../mfc/visualization-manager.md)
