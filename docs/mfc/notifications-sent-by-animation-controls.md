---
title: Powiadomienia wysyłane przez formanty animacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1696389ce3dc40c5d02ec660ebaeb6bf3e6c3ec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345252"
---
# <a name="notifications-sent-by-animation-controls"></a>Powiadomienia wysyłane przez formanty animacji
Formantu animacji ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) wysyła dwa różne typy powiadomień. Powiadomienia są wysyłane w postaci [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) wiadomości.  
  
 [ACN_START](http://msdn.microsoft.com/library/windows/desktop/bb761891) komunikat jest wysyłany, gdy formant animacja się rozpoczęła klipem. [ACN_STOP](http://msdn.microsoft.com/library/windows/desktop/bb761893) komunikat jest wysyłany, gdy formantu animacji ma zostało zakończone lub zatrzymać odtwarzanie klipu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

