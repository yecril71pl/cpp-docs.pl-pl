---
title: Zamykanie okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e4c311a8d09ac3e1329b495fc321028e9f674993
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="closing-the-dialog-box"></a>Zamykanie okna dialogowego
Modalne okno dialogowe zostanie zamknięte, jeśli użytkownik wybierze jeden z jej przyciski, zwykle przycisk OK lub przycisk Anuluj. Wybierając przycisk OK lub Anuluj spowoduje, że system Windows do wysyłania obiektu okna dialogowego **BN_CLICKED** komunikatów powiadomień dotyczących formantu przy użyciu przycisku przez identyfikator, albo **IDOK** lub **IDCANCEL**. `CDialog`udostępnia domyślne funkcje programu obsługi dla tych wiadomości: `OnOK` i `OnCancel`. Wywołanie procedury obsługi domyślne `EndDialog` funkcji członkowskiej, aby zamknąć okno dialogowe. Możesz także wywołać `EndDialog` z własnego kodu. Aby uzyskać więcej informacji, zobacz [EndDialog](../mfc/reference/cdialog-class.md#enddialog) funkcji członkowskiej klasy `CDialog` w *odwołania MFC*.  
  
 Przygotowanie zamykania i usuwanie niemodalne okno dialogowe, należy zastąpić `PostNcDestroy` i wywoływać **usunąć** operator na **to** wskaźnika. [Niszczenie okna dialogowego](../mfc/destroying-the-dialog-box.md) opisano, co dalej.  
  
## <a name="see-also"></a>Zobacz też  
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

