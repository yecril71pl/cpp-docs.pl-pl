---
title: Style formantu ToolBar
ms.date: 11/04/2016
helpviewer_keywords:
- ToolBar control styles [MFC]
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
ms.openlocfilehash: f26edc6c0ce4a19528a9a8754428411318e9b9d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648997"
---
# <a name="toolbar-control-styles"></a>Style formantu ToolBar

[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) ma zestaw flag style, które określają wygląd i zachowanie przycisku. Można ustawić kombinację tych flag, wywołując [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle). Ten temat zawiera listę wartości flagi styl i ich znaczenie.

## <a name="property-values"></a>Wartości właściwości

Następujące wartości określają typ przycisku, który reprezentuje kontrolkę:

|||
|-|-|
|TBBS_BUTTON|Przycisk standardowe (domyślne).  |
|TBBS_CHECKBOX|Pole wyboru.  |
|TBBS_CHECKGROUP|Początek grupy pól wyboru.  |
|TBBS_GROUP|Początek grupy przycisków.  |
|TBBS_SEPARATOR|Separator.  |

Następujące wartości reprezentują bieżący stan kontrolki:

|||
|-|-|
|TBBS_CHECKED|Pole wyboru jest zaznaczone.  |
|TBBS_DISABLED|Kontrolka jest wyłączona.  |
|TBBS_INDETERMINATE|Pole wyboru jest w stanie nieokreślonym.  |
|TBBS_PRESSED|Naciśnięciu przycisku.  |

Następująca wartość zmienia układ przycisk na pasku narzędzi:

|||
|-|-|
|TBBS_BREAK|Umieszcza elementu w nowym wierszu lub w nowej kolumnie bez oddzielenie kolumn.  |

## <a name="remarks"></a>Uwagi

Bieżący styl są przechowywane w [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle). Nie należy ustawiać nową wartość w `m_nStyle` bezpośrednio, ponieważ niektóre klasy pochodne wykonywać dodatkowego przetwarzania podczas wywoływania `SetStyles`.

Wizualne manager określa wygląd przycisków w każdym stanie. Zobacz [Menedżer wizualizacji](../../mfc/visualization-manager.md) Aby uzyskać więcej informacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbarbutton.h

## <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Menedżer wizualizacji](../../mfc/visualization-manager.md)

