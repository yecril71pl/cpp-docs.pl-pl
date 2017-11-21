---
title: "Dzielenie wyrazów w formantach edycji wzbogaconej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c438a6c3e1891a7ffa85445355d5b08a3f79f2a8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="word-breaks-in-rich-edit-controls"></a>Podziały wyrazów w formantach edycji wzbogaconej
Kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) wywołuje funkcję o nazwie "word podziału procedury" Aby znaleźć przerw między wyrazami i określić, gdzie może spowodować nieprawidłowe wierszy. Formant używa tych informacji podczas wykonywania operacji zawijania słów oraz podczas przetwarzania kombinacji klawiszy CTRL + Strzałka w lewo i CTRL + Strzałka w prawo. Aplikacja może wysyłać wiadomości do kontrolki edycji wzbogaconej zastąpić procedury dzielenia wyrazów domyślne, można pobrać informacji o dzielenie wyrazów i określić, co wiersz danego znaku znajduje się.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

