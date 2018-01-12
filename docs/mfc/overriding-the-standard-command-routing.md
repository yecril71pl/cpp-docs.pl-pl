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
ms.workload: cplusplus
ms.openlocfilehash: 6a8f926a2aa9ed48dac24f75850876bbd1e04ef4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="overriding-the-standard-command-routing"></a>Zastępowanie standardowego routingu poleceń
W rzadkich przypadkach, gdy musi implementować różnice standardowych ramy routingu można je zastąpić. Koncepcja jest zmiana routingu w co najmniej jednej klasy przez zastąpienie `OnCmdMsg` tych klas. To zrobić:  
  
-   W klasie, która dzieli kolejności do przekazania do obiektu innych niż domyślne.  
  
-   Nowy obiekt inny niż domyślny lub obiekty docelowe poleceń z kolei może przekazać co polecenia.  
  
 Po wstawieniu niektóre nowy obiekt do routingu jej klasa musi być klasą docelowym polecenia. W Twojej wersji zastępowanie `OnCmdMsg`, należy wywołać wersję, która jest zastępowanie. Zobacz [OnCmdMsg](../mfc/reference/ccmdtarget-class.md#oncmdmsg) funkcji członkowskiej klasy `CCmdTarget` w *odwołania MFC* i wersji w tych grupach jako `CView` i **CDocument** w Podane przykłady kodu źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)

