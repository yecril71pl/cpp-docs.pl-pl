---
title: "ONIDLE — funkcja członkowska | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OnIdle
dev_langs:
- C++
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4dfbc0a1f20cb6cc01143ed6f07a63e84b53be6b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="onidle-member-function"></a>OnIdle — Funkcja członkowska
Gdy nie komunikaty systemu Windows są przetwarzane, struktura wywołuje [CWinApp](../mfc/reference/cwinapp-class.md) funkcji członkowskiej [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (opisanej w odwołanie do biblioteki MFC).  
  
 Zastąpienie `OnIdle` do wykonania zadania w tle. Domyślna wersja aktualizuje stan obiektów interfejsu użytkownika, takich jak przyciski paska narzędzi i wykonuje oczyszczania tymczasowe obiekty utworzone przez platformę w trakcie jego działania. Na poniższej ilustracji pokazano, jak wywołuje pętli komunikatów `OnIdle` gdy nie ma żadnych komunikatów w kolejce.  
  
 ![Przetwarzanie pętli komunikatów](../mfc/media/vc387c1.gif "vc387c1")  
Pętla wiadomości  
  
 Aby uzyskać więcej informacji na temat działania w pętli bezczynności, zobacz [przetwarzanie pętli bezczynności](../mfc/idle-loop-processing.md).  
  
## <a name="see-also"></a>Zobacz też  
 [CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
