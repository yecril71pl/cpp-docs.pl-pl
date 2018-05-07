---
title: Przy użyciu Nieobcinanego kontekstu urządzenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], unclipped device context
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c76dc44993615e17ea3d99f9ac018a748e24d0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-an-unclipped-device-context"></a>Używanie nieobcinanego kontekstu urządzenia
Jeśli masz pewność, że formantu nie można malować poza obszarem prostokąta jego klienta, można zrealizować korzyści szybkości mały, ale wykrywalny przez wyłączenie wywołanie `IntersectClipRect` który dokonuje `COleControl`. Aby to zrobić, należy usunąć **clipPaintDC** flagi z zestawu flagi zwrócony przez [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Na przykład:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]  
  
 Kod, aby usunąć ta flaga jest automatycznie generowany w przypadku wybrania **Nieobcinanego kontekstu urządzenia** opcja [ustawienia kontroli](../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony, podczas tworzenia formantu przy użyciu Kreator formantów MFC ActiveX.  
  
 Jeśli korzystasz z aktywacji niepowiązanej z oknami, optymalizacja nie ma znaczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC: optymalizacja](../mfc/mfc-activex-controls-optimization.md)

