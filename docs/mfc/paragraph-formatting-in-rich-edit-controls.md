---
title: Formatowanie akapitu w formantach edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: f2ac69838bf39afb636c3d41c97adc1378463d1b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507978"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formatowanie akapitu w formantach edycji wzbogaconej

Możesz użyć funkcji składowych kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)), aby sformatować akapity i pobrać informacje o formatowaniu. Atrybuty formatowania akapitu obejmują wyrównanie, tabulatory, wcięcia i numerowanie.

Formatowanie akapitu można zastosować przy użyciu funkcji składowej [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) . Aby określić bieżące formatowanie akapitu dla zaznaczonego tekstu, użyj funkcji składowej [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) . Struktura [PARAFORMAT](/windows/win32/api/richedit/ns-richedit-paraformat) jest używana z tymi funkcjami składowymi, aby określić atrybuty akapitu. Jednym z ważnych elementów członkowskich **PARAFORMAT** jest *dwMask*. W `SetParaFormat`programie *dwMask* określa, które atrybuty akapitu będą ustawiane przez to wywołanie funkcji. `GetParaFormat`raportuje atrybuty pierwszego akapitu w zaznaczeniu; *dwMask* określa atrybuty, które są spójne w zaznaczeniu.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
