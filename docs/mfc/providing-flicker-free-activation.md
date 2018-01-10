---
title: Zapewnianie aktywacji pozbawionej migotania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1f14998ce663e5a8e53901acf9192719fa41e724
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="providing-flicker-free-activation"></a>Zapewnianie aktywacji pozbawionej migotania
Jeśli formantu rysuje się tak samo w Stanach stanem nieaktywnym i aktywnym (i nie używa aktywacji niepowiązanej z oknami), można wyeliminować operacje rysowania i towarzyszące im migotanie, które normalnie występuje podczas wykonywania przejścia między nieaktywnych i aktywne stany. Aby to zrobić, należy uwzględnić **noFlickerActivate** flagi w zestawie flagi zwrócony przez [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Na przykład:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]  
  
 Kod, aby dołączyć ta flaga jest automatycznie generowany w przypadku wybrania **aktywacji pozbawionej migotania** opcja [ustawienia kontroli](../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony podczas tworzenia formantu przy użyciu Kreator formantów MFC ActiveX.  
  
 Jeśli korzystasz z aktywacji niepowiązanej z oknami, optymalizacja nie ma znaczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC: optymalizacja](../mfc/mfc-activex-controls-optimization.md)

