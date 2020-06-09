---
title: Formatowanie akapitu w formantach edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: e23976e64b3c9a4a76e5b05c90d0ad033b62657a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615338"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formatowanie akapitu w formantach edycji wzbogaconej

Możesz użyć funkcji składowych kontrolki edycji wzbogaconej ([CRichEditCtrl](reference/cricheditctrl-class.md)), aby sformatować akapity i pobrać informacje o formatowaniu. Atrybuty formatowania akapitu obejmują wyrównanie, tabulatory, wcięcia i numerowanie.

Formatowanie akapitu można zastosować przy użyciu funkcji składowej [SetParaFormat](reference/cricheditctrl-class.md#setparaformat) . Aby określić bieżące formatowanie akapitu dla zaznaczonego tekstu, użyj funkcji składowej [GetParaFormat](reference/cricheditctrl-class.md#getparaformat) . Struktura [PARAFORMAT](/windows/win32/api/richedit/ns-richedit-paraformat) jest używana z tymi funkcjami składowymi, aby określić atrybuty akapitu. Jednym z ważnych elementów członkowskich **PARAFORMAT** jest *dwMask*. W `SetParaFormat` programie *dwMask* określa, które atrybuty akapitu będą ustawiane przez to wywołanie funkcji. `GetParaFormat`raportuje atrybuty pierwszego akapitu w zaznaczeniu; *dwMask* określa atrybuty, które są spójne w zaznaczeniu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CRichEditCtrl](using-cricheditctrl.md)<br/>
[Formanty](controls-mfc.md)
