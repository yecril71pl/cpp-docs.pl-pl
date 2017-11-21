---
title: "Przy użyciu Nieobcinanego kontekstu urządzenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: MFC ActiveX controls [MFC], unclipped device context
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0b3a64db489865463f914fa94c096605f8c9c56b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-an-unclipped-device-context"></a>Używanie nieobcinanego kontekstu urządzenia
Jeśli masz pewność, że formantu nie można malować poza obszarem prostokąta jego klienta, można zrealizować korzyści szybkości mały, ale wykrywalny przez wyłączenie wywołanie `IntersectClipRect` który dokonuje `COleControl`. Aby to zrobić, należy usunąć **clipPaintDC** flagi z zestawu flagi zwrócony przez [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Na przykład:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]  
  
 Kod, aby usunąć ta flaga jest automatycznie generowany w przypadku wybrania **Nieobcinanego kontekstu urządzenia** opcja [ustawienia kontroli](../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony, podczas tworzenia formantu przy użyciu Kreator formantów MFC ActiveX.  
  
 Jeśli korzystasz z aktywacji niepowiązanej z oknami, optymalizacja nie ma znaczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty MFC ActiveX: Optymalizacja](../mfc/mfc-activex-controls-optimization.md)

