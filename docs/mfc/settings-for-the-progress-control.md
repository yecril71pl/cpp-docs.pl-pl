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
ms.workload: cplusplus
ms.openlocfilehash: 1ad62f3a60c8fe4fcd7efdde7f69f5c5e9450d14
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="settings-for-the-progress-control"></a>Ustawienia formantu postępu
Podstawowe ustawienia formantu postępu ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) są zakresu i bieżącego położenia. Zakres reprezentuje cały czas trwania operacji. Bieżąca pozycja reprezentuje postępu, który wprowadził aplikacji ukończenia operacji. Zmiany wprowadzone w zakresie lub pozycji spowodować formantu postępu ponownego narysowania.  
  
 Domyślnie ustawiono zakres 0 - 100 i początkowe położenie jest równa 0. Aby uzyskać bieżące ustawienia zakresu formantu postępu, użyj [GetRange](../mfc/reference/cprogressctrl-class.md#getrange) funkcję elementu członkowskiego. Aby zmienić zakres, należy użyć [SetRange](../mfc/reference/cprogressctrl-class.md#setrange) funkcję elementu członkowskiego.  
  
 Aby ustawić pozycji, użyj [SetPos](../mfc/reference/cprogressctrl-class.md#setpos). Aby pobrać bieżącą pozycję bez określenia nowej wartości, należy użyć [GetPos](../mfc/reference/cprogressctrl-class.md#getpos). Na przykład możesz po prostu kwerendy stanu bieżącej operacji.  
  
 Do wykonania kroków bieżącej pozycji formantu postępu, użyj [StepIt](../mfc/reference/cprogressctrl-class.md#stepit). Aby ustawić wartość każdego kroku, należy użyć [SetStep](../mfc/reference/cprogressctrl-class.md#setstep)  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

