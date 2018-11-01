---
title: Formatowanie akapitu w formantach edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: f79d9a97554e2f73b42746c9e9094b07a37513d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581977"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formatowanie akapitu w formantach edycji wzbogaconej

Można użyć funkcji składowych kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) do formatowania akapitów i, aby pobrać informacje o formatowaniu. Atrybuty formatowania akapitu obejmują wyrównanie, karty, wcięcia i numerowania identyfikatorów.

Można zastosować formatowanie przy użyciu akapitów [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) funkcja elementu członkowskiego. Aby określić bieżący akapit formatowanie do zaznaczonego tekstu, należy użyć [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) funkcja elementu członkowskiego. [PARAFORMAT](/windows/desktop/api/richedit/ns-richedit-_paraformat) struktury jest używany z tych funkcji elementów członkowskich do określenia atrybuty akapitu. Jedną z ważnych elementów członkowskich **PARAFORMAT** jest *dwMask*. W `SetParaFormat`, *dwMask* Określa, jakie atrybuty akapitu zostanie ustawiona przez wywołanie tej funkcji. `GetParaFormat` Raporty atrybuty pierwszego akapitu w zaznaczeniu; *dwMask* określa atrybuty, które są spójne zaznaczenia.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

