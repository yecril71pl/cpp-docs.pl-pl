---
title: "Ustawienia formantu postępu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e6a00dcf03fed03d46fef8fb2f17f9e182e2d75d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="settings-for-the-progress-control"></a>Ustawienia formantu postępu
Podstawowe ustawienia formantu postępu ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) są zakresu i bieżącego położenia. Zakres reprezentuje cały czas trwania operacji. Bieżąca pozycja reprezentuje postępu, który wprowadził aplikacji ukończenia operacji. Zmiany wprowadzone w zakresie lub pozycji spowodować formantu postępu ponownego narysowania.  
  
 Domyślnie ustawiono zakres 0 - 100 i początkowe położenie jest równa 0. Aby uzyskać bieżące ustawienia zakresu formantu postępu, użyj [GetRange](../mfc/reference/cprogressctrl-class.md#getrange) funkcję elementu członkowskiego. Aby zmienić zakres, należy użyć [SetRange](../mfc/reference/cprogressctrl-class.md#setrange) funkcję elementu członkowskiego.  
  
 Aby ustawić pozycji, użyj [SetPos](../mfc/reference/cprogressctrl-class.md#setpos). Aby pobrać bieżącą pozycję bez określenia nowej wartości, należy użyć [GetPos](../mfc/reference/cprogressctrl-class.md#getpos). Na przykład możesz po prostu kwerendy stanu bieżącej operacji.  
  
 Do wykonania kroków bieżącej pozycji formantu postępu, użyj [StepIt](../mfc/reference/cprogressctrl-class.md#stepit). Aby ustawić wartość każdego kroku, należy użyć [SetStep](../mfc/reference/cprogressctrl-class.md#setstep)  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

