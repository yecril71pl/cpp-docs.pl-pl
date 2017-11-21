---
title: "ONIDLE — funkcja członkowska | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OnIdle
dev_langs: C++
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d601ac8da59e4b980c4f1a5bd85bc1b347e8e11e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="onidle-member-function"></a>OnIdle — Funkcja członkowska
Gdy nie komunikaty systemu Windows są przetwarzane, struktura wywołuje [CWinApp](../mfc/reference/cwinapp-class.md) funkcji członkowskiej [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (opisanej w odwołanie do biblioteki MFC).  
  
 Zastąpienie `OnIdle` do wykonania zadania w tle. Domyślna wersja aktualizuje stan obiektów interfejsu użytkownika, takich jak przyciski paska narzędzi i wykonuje oczyszczania tymczasowe obiekty utworzone przez platformę w trakcie jego działania. Na poniższej ilustracji pokazano, jak wywołuje pętli komunikatów `OnIdle` gdy nie ma żadnych komunikatów w kolejce.  
  
 ![Przetwarzanie pętli komunikatów](../mfc/media/vc387c1.gif "vc387c1")  
Pętla wiadomości  
  
 Aby uzyskać więcej informacji na temat działania w pętli bezczynności, zobacz [przetwarzanie pętli bezczynności](../mfc/idle-loop-processing.md).  
  
## <a name="see-also"></a>Zobacz też  
 [CWinApp: Klasa aplikacji](../mfc/cwinapp-the-application-class.md)
