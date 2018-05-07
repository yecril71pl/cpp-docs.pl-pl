---
title: Ustawienia formantu postępu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26afdcb58a64f2d2042596349acc4496aa530468
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="settings-for-the-progress-control"></a>Ustawienia formantu postępu
Podstawowe ustawienia formantu postępu ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) są zakresu i bieżącego położenia. Zakres reprezentuje cały czas trwania operacji. Bieżąca pozycja reprezentuje postępu, który wprowadził aplikacji ukończenia operacji. Zmiany wprowadzone w zakresie lub pozycji spowodować formantu postępu ponownego narysowania.  
  
 Domyślnie ustawiono zakres 0 - 100 i początkowe położenie jest równa 0. Aby uzyskać bieżące ustawienia zakresu formantu postępu, użyj [GetRange](../mfc/reference/cprogressctrl-class.md#getrange) funkcję elementu członkowskiego. Aby zmienić zakres, należy użyć [SetRange](../mfc/reference/cprogressctrl-class.md#setrange) funkcję elementu członkowskiego.  
  
 Aby ustawić pozycji, użyj [SetPos](../mfc/reference/cprogressctrl-class.md#setpos). Aby pobrać bieżącą pozycję bez określenia nowej wartości, należy użyć [GetPos](../mfc/reference/cprogressctrl-class.md#getpos). Na przykład możesz po prostu kwerendy stanu bieżącej operacji.  
  
 Do wykonania kroków bieżącej pozycji formantu postępu, użyj [StepIt](../mfc/reference/cprogressctrl-class.md#stepit). Aby ustawić wartość każdego kroku, należy użyć [SetStep](../mfc/reference/cprogressctrl-class.md#setstep)  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

