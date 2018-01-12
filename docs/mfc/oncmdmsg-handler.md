---
title: "Program obsługi OnCmdMsg | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OnCmdMsg
dev_langs: C++
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 173741ef73cd4bf6426787ef56e8334f504d7c0e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="oncmdmsg-handler"></a>Program obsługi OnCmdMsg
Aby osiągnąć routingu poleceń, wywołuje każdym obiekcie docelowym polecenia `OnCmdMsg` funkcji członkowskiej dalej docelowego polecenia w sekwencji. Polecenie celem użycia `OnCmdMsg` ustalenie, czy ich obsługi polecenia i przekazać go do innej docelowej polecenia, jeśli go nie obsługują.  
  
 Każdej klasy docelowej polecenia może zastąpić `OnCmdMsg` funkcję elementu członkowskiego. Zastąpienia umożliwiają każdej klasy poleceń trasy do określonego celu dalej. Okno ramowe na przykład zawsze kieruje poleceń do jego bieżące okno podrzędne lub widok, jak pokazano w tabeli [trasy standardowego polecenia](../mfc/command-routing.md).  
  
 Wartość domyślna `CCmdTarget` implementacja `OnCmdMsg` używa mapę komunikatów w wybranej klasy docelowej polecenia do wyszukiwania dla funkcji programu obsługi dla każdego komunikatu polecenia odbierze — w taki sam sposób, że są przeszukiwane standardowych komunikatów. Jeśli znajdzie dopasowanie wywołuje program obsługi. Mapy wiadomości wyszukiwanie zostało wyjaśnione w dokumencie [jak Framework wyszukuje mapy komunikatów](../mfc/how-the-framework-searches-message-maps.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)

