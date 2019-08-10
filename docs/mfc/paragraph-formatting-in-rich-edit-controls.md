---
title: Formatowanie akapitu w formantach edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: 0988e7940c8d8947b86e97a35d71586f8f5c316a
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916374"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formatowanie akapitu w formantach edycji wzbogaconej

Możesz użyć funkcji składowych kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)), aby sformatować akapity i pobrać informacje o formatowaniu. Atrybuty formatowania akapitu obejmują wyrównanie, tabulatory, wcięcia i numerowanie.

Formatowanie akapitu można zastosować przy użyciu funkcji składowej [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) . Aby określić bieżące formatowanie akapitu dla zaznaczonego tekstu, użyj funkcji składowej [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) . Struktura [PARAFORMAT](/windows/desktop/api/richedit/ns-richedit-paraformat) jest używana z tymi funkcjami składowymi, aby określić atrybuty akapitu. Jednym z ważnych elementów członkowskich **PARAFORMAT** jest *dwMask*. W `SetParaFormat`programie *dwMask* określa, które atrybuty akapitu będą ustawiane przez to wywołanie funkcji. `GetParaFormat`raportuje atrybuty pierwszego akapitu w zaznaczeniu; *dwMask* określa atrybuty, które są spójne w zaznaczeniu.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
