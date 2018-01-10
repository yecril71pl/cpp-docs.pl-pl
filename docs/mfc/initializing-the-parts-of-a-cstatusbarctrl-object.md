---
title: "Inicjowanie części obiektu CStatusBarCtrl | Dokumentacja firmy Microsoft"
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
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b713a46db13508df5ba80b21e3dfe938261eec65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>Inicjowanie części obiektu CStatusBarCtrl
Domyślnie pasek stanu wyświetla informacje o stanie przy użyciu osobnych okienka. Te okienka (określane również jako części) może zawierać ciąg tekstowy, ikony lub obu.  
  
 Użyj [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) określenie, ile części i długość, będzie miał na pasku stanu. Po utworzeniu części paska stanu wykonywania wywołań do [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) i [SetIcon](../mfc/reference/cstatusbarctrl-class.md#seticon) można ustawić tekstu lub ikony dla określonej części paska stanu. Po pomyślnym ustawieniu części kontrolki automatycznie narysowany ponownie.  
  
 W poniższym przykładzie inicjowane istniejące `CStatusBarCtrl` obiektu (`m_StatusBarCtrl`) z okienka cztery, a następnie ustawia ikonę (IDI_ICON1) i tekst w drugiej części.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]  
  
 Aby uzyskać więcej informacji na temat ustawiania trybu `CStatusBarCtrl` obiektu prosty, zobacz [Ustawianie trybu obiektu CStatusBarCtrl](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

