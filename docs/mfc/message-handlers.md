---
title: "Programy obsługi komunikatów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d1b906a49d7da7ed8505252a1759d7ea00fcda1f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="message-handlers"></a>Programy obsługi komunikatów
W MFC dedykowana *obsługi* funkcja przetwarza każdy komunikat osobne. Funkcje elementów członkowskich klasy są funkcje obsługi wiadomości. Ta dokumentacja używa warunki *funkcji członkowskiej obsługi wiadomości*, *funkcji obsługi wiadomości*, *obsługi wiadomości*, i *obsługi*zamiennie. Niektóre rodzaje programów obsługi wiadomości są również nazywane "programy obsługi poleceń."  
  
 Zapisywanie konta programy obsługi komunikatów dla znaczną część pracy w pisanie aplikacji framework. Rodzina tego artykułu opisano, jak działa mechanizm przetwarzania komunikatów.  
  
 Działania programu obsługi wiadomości to robić jest dowolne w odpowiedzi na tę wiadomość. Można utworzyć obsługi przy użyciu okna właściwości klasy, a następnie wypełnij programu obsługi kodu za pomocą edytora kodu źródłowego.  
  
 Możliwość używania wszystkich obiektów programu Microsoft Visual C++ i MFC do zapisania programu obsługi. Aby uzyskać listę wszystkich klas, zobacz [Przegląd biblioteki klas](../mfc/class-library-overview.md) w *odwołania MFC*.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)

