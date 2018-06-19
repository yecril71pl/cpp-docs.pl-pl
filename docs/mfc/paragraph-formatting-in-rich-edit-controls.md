---
title: Formatowanie akapitu w formantach edycji wzbogaconej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 113d47a88f0de7ddd12f474678705688569ad50d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348120"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formatowanie akapitu w formantach edycji wzbogaconej
Możesz użyć funkcji Członkowskich formantu edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) do formatowania akapitów oraz do pobierania informacji o formatowaniu. Atrybuty formatowania akapitu obejmują wyrównanie, tabulatory, wcięcia i numerowanie.  
  
 Możesz zastosować formatowanie przy użyciu akapitu [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) funkcję elementu członkowskiego. Aby określić bieżącego formatowania zaznaczonego tekstu akapitu, użyj [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) funkcję elementu członkowskiego. [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940) struktura jest używana z tych funkcji Członkowskich, aby określić atrybuty akapitu. Jeden z członków ważne **PARAFORMAT** jest **dwMask**. W `SetParaFormat`, **dwMask** określa atrybuty akapitu zostanie ustawiony przez wywołanie tej funkcji. `GetParaFormat` Raporty atrybuty akapitu w wyboru; **dwMask** określa atrybuty, które są spójne w całym zaznaczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

