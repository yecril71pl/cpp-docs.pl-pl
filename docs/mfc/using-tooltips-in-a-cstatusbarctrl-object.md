---
title: "Używanie etykietek narzędzi w obiekcie CStatusBarCtrl | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CStatusBarCtrl
dev_langs: C++
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3e2d7f2ee90b7389ad3602e808213c3803dd5ad1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Używanie etykietek narzędzi w obiekcie CStatusBarCtrl
Aby włączyć etykietki narzędzi dla formantu paska stanu, należy utworzyć `CStatusBarCtrl` obiekt z **SBT_TOOLTIPS** stylu.  
  
> [!NOTE]
>  Jeśli używasz `CStatusBar` obiekt do wdrożenia na pasku stanu, użyj `CStatusBar::CreateEx` funkcji. Umożliwia określenie dodatkowych style osadzonego **CStatusBarCtrl** obiektu.  
  
 Raz `CStatusBarCtrl` obiekt został pomyślnie utworzony, użyj [CStatusBarCtrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) i [CStatusBarCtrl::GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) ustawiania i pobierania tekst porady dla określonych okienka.  
  
 Po ustawieniu etykietka narzędzia, która jest wyświetlany tylko wtedy, gdy element ikony, jak i bez tekstu lub cały tekst nie będzie wyświetlany w części. Etykietki narzędzi nie są obsługiwane w trybie proste.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

