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
ms.openlocfilehash: 9417fe9bab9b1fca8ec8292e27efc02afec5511c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929150"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formatowanie akapitu w formantach edycji wzbogaconej
Możesz użyć funkcji Członkowskich formantu edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) do formatowania akapitów oraz do pobierania informacji o formatowaniu. Atrybuty formatowania akapitu obejmują wyrównanie, tabulatory, wcięcia i numerowanie.  
  
 Możesz zastosować formatowanie przy użyciu akapitu [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) funkcję elementu członkowskiego. Aby określić bieżącego formatowania zaznaczonego tekstu akapitu, użyj [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) funkcję elementu członkowskiego. [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940) struktura jest używana z tych funkcji Członkowskich, aby określić atrybuty akapitu. Jeden z członków ważne **PARAFORMAT** jest *dwMask*. W `SetParaFormat`, *dwMask* określa atrybuty akapitu zostanie ustawiony przez wywołanie tej funkcji. `GetParaFormat` Raporty atrybuty akapitu w wyboru; *dwMask* określa atrybuty, które są spójne w całym zaznaczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

