---
title: Zastępowanie standardowego routingu poleceń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13f6c8f262061477da95a4863965c04e9d75c49a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="overriding-the-standard-command-routing"></a>Zastępowanie standardowego routingu poleceń
W rzadkich przypadkach, gdy musi implementować różnice standardowych ramy routingu można je zastąpić. Koncepcja jest zmiana routingu w co najmniej jednej klasy przez zastąpienie `OnCmdMsg` tych klas. To zrobić:  
  
-   W klasie, która dzieli kolejności do przekazania do obiektu innych niż domyślne.  
  
-   Nowy obiekt inny niż domyślny lub obiekty docelowe poleceń z kolei może przekazać co polecenia.  
  
 Po wstawieniu niektóre nowy obiekt do routingu jej klasa musi być klasą docelowym polecenia. W Twojej wersji zastępowanie `OnCmdMsg`, należy wywołać wersję, która jest zastępowanie. Zobacz [OnCmdMsg](../mfc/reference/ccmdtarget-class.md#oncmdmsg) funkcji członkowskiej klasy `CCmdTarget` w *odwołania MFC* i wersji w tych grupach jako `CView` i **CDocument** w Podane przykłady kodu źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)

