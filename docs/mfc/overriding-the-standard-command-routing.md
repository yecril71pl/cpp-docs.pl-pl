---
title: "Zastępowanie standardowego routingu poleceń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7168236ea315d42961f984a3c4f94845cd8398df
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="overriding-the-standard-command-routing"></a>Zastępowanie standardowego routingu poleceń
W rzadkich przypadkach, gdy musi implementować różnice standardowych ramy routingu można je zastąpić. Koncepcja jest zmiana routingu w co najmniej jednej klasy przez zastąpienie `OnCmdMsg` tych klas. To zrobić:  
  
-   W klasie, która dzieli kolejności do przekazania do obiektu innych niż domyślne.  
  
-   Nowy obiekt inny niż domyślny lub obiekty docelowe poleceń z kolei może przekazać co polecenia.  
  
 Po wstawieniu niektóre nowy obiekt do routingu jej klasa musi być klasą docelowym polecenia. W Twojej wersji zastępowanie `OnCmdMsg`, należy wywołać wersję, która jest zastępowanie. Zobacz [OnCmdMsg](../mfc/reference/ccmdtarget-class.md#oncmdmsg) funkcji członkowskiej klasy `CCmdTarget` w *odwołania MFC* i wersji w tych grupach jako `CView` i **CDocument** w Podane przykłady kodu źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak struktura wywołuje program obsługi](../mfc/how-the-framework-calls-a-handler.md)

