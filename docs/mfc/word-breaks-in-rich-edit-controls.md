---
title: Dzielenie wyrazów w formantach edycji wzbogaconej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 373a30ed4a327cff99cb3cfce873707314608b57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="word-breaks-in-rich-edit-controls"></a>Podziały wyrazów w formantach edycji wzbogaconej
Kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) wywołuje funkcję o nazwie "word podziału procedury" Aby znaleźć przerw między wyrazami i określić, gdzie może spowodować nieprawidłowe wierszy. Formant używa tych informacji podczas wykonywania operacji zawijania słów oraz podczas przetwarzania kombinacji klawiszy CTRL + Strzałka w lewo i CTRL + Strzałka w prawo. Aplikacja może wysyłać wiadomości do kontrolki edycji wzbogaconej zastąpić procedury dzielenia wyrazów domyślne, można pobrać informacji o dzielenie wyrazów i określić, co wiersz danego znaku znajduje się.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

