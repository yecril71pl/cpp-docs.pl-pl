---
title: Exitinstance — funkcja członkowska | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords: []
dev_langs:
- C++
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 954d2248061ec571d9d2ba8804c1f7c97275cbfc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343502"
---
# <a name="exitinstance-member-function"></a>ExitInstance — Funkcja członkowska
[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) funkcji członkowskiej klasy [CWinApp](../mfc/reference/cwinapp-class.md) jest wywoływana za każdym razem kopii aplikacji kończy zazwyczaj w wyniku użytkownika Kończenie działania aplikacji.  
  
 Zastąpienie `ExitInstance` konieczne będzie przetwarzania oczyszczania specjalnych, takich jak zwolnić grafiki urządzenia (GDI) interfejsu zasobów lub cofanie przydziału pamięci używane podczas wykonywania programu. Oczyszczanie standardowych elementów, takich jak dokumenty i widoki, jednak są udostępniane przez platformy, z innymi funkcjami możliwym do zastąpienia dla podczas oczyszczania specjalne specyficzne dla tych obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 [CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
