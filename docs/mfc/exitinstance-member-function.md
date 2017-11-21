---
title: "Exitinstance — funkcja członkowska | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: 
dev_langs: C++
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0dc1710bbb6efd5bc48aa0b640c8e05747dce2e9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="exitinstance-member-function"></a>ExitInstance — Funkcja członkowska
[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) funkcji członkowskiej klasy [CWinApp](../mfc/reference/cwinapp-class.md) jest wywoływana za każdym razem kopii aplikacji kończy zazwyczaj w wyniku użytkownika Kończenie działania aplikacji.  
  
 Zastąpienie `ExitInstance` konieczne będzie przetwarzania oczyszczania specjalnych, takich jak zwolnić grafiki urządzenia (GDI) interfejsu zasobów lub cofanie przydziału pamięci używane podczas wykonywania programu. Oczyszczanie standardowych elementów, takich jak dokumenty i widoki, jednak są udostępniane przez platformy, z innymi funkcjami możliwym do zastąpienia dla podczas oczyszczania specjalne specyficzne dla tych obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 [CWinApp: Klasa aplikacji](../mfc/cwinapp-the-application-class.md)
