---
title: ONIDLE — funkcja członkowska | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bbe912db448e424f18b6d72f6e148312c5940687
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350370"
---
# <a name="onidle-member-function"></a>OnIdle — Funkcja członkowska
Gdy nie komunikaty systemu Windows są przetwarzane, struktura wywołuje [CWinApp](../mfc/reference/cwinapp-class.md) funkcji członkowskiej [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (opisanej w odwołanie do biblioteki MFC).  
  
 Zastąpienie `OnIdle` do wykonania zadania w tle. Domyślna wersja aktualizuje stan obiektów interfejsu użytkownika, takich jak przyciski paska narzędzi i wykonuje oczyszczania tymczasowe obiekty utworzone przez platformę w trakcie jego działania. Na poniższej ilustracji pokazano, jak wywołuje pętli komunikatów `OnIdle` gdy nie ma żadnych komunikatów w kolejce.  
  
 ![Przetwarzanie pętli komunikatów](../mfc/media/vc387c1.gif "vc387c1")  
Pętla wiadomości  
  
 Aby uzyskać więcej informacji na temat działania w pętli bezczynności, zobacz [przetwarzanie pętli bezczynności](../mfc/idle-loop-processing.md).  
  
## <a name="see-also"></a>Zobacz też  
 [CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
