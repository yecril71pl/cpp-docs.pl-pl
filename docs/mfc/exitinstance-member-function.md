---
title: "Exitinstance — funkcja członkowska | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
dev_langs:
- C++
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 99898a5e80c3f487c7f53fe81d13d3d1eb55ebd5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="exitinstance-member-function"></a>ExitInstance — Funkcja członkowska
[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) funkcji członkowskiej klasy [CWinApp](../mfc/reference/cwinapp-class.md) jest wywoływana za każdym razem kopii aplikacji kończy zazwyczaj w wyniku użytkownika Kończenie działania aplikacji.  
  
 Zastąpienie `ExitInstance` konieczne będzie przetwarzania oczyszczania specjalnych, takich jak zwolnić grafiki urządzenia (GDI) interfejsu zasobów lub cofanie przydziału pamięci używane podczas wykonywania programu. Oczyszczanie standardowych elementów, takich jak dokumenty i widoki, jednak są udostępniane przez platformy, z innymi funkcjami możliwym do zastąpienia dla podczas oczyszczania specjalne specyficzne dla tych obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 [CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
