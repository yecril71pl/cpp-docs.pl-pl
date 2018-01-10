---
title: Formatowanie akapitu w formantach edycji wzbogaconej | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f0dc12d923f6f424fe84768b0d934d8dd7ff20b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formatowanie akapitu w formantach edycji wzbogaconej
Możesz użyć funkcji Członkowskich formantu edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) do formatowania akapitów oraz do pobierania informacji o formatowaniu. Atrybuty formatowania akapitu obejmują wyrównanie, tabulatory, wcięcia i numerowanie.  
  
 Możesz zastosować formatowanie przy użyciu akapitu [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) funkcję elementu członkowskiego. Aby określić bieżącego formatowania zaznaczonego tekstu akapitu, użyj [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) funkcję elementu członkowskiego. [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940) struktura jest używana z tych funkcji Członkowskich, aby określić atrybuty akapitu. Jeden z członków ważne **PARAFORMAT** jest **dwMask**. W `SetParaFormat`, **dwMask** określa atrybuty akapitu zostanie ustawiony przez wywołanie tej funkcji. `GetParaFormat`Raporty atrybuty akapitu w wyboru; **dwMask** określa atrybuty, które są spójne w całym zaznaczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

