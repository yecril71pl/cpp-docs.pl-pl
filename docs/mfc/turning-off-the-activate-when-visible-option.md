---
title: "Wyłączanie aktywacji podczas widoczna opcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], activate options
- Activate When Visible option [MFC]
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 25521d75921b377730a7f9afac71f2a60c055216
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="turning-off-the-activate-when-visible-option"></a>Wyłączanie opcji aktywacji w przypadku widoczności
Formant ma dwa stany podstawowe: aktywnych i nieaktywnych. Zazwyczaj te stany zostały rozróżnianych na podstawie tego, czy formant miał okna. Aktywny formant miał okna; nie kontrolkę, która jest nieaktywne. Ta różnica nie jest już uniwersalnych wraz z wprowadzeniem aktywacji niepowiązanej z oknami, ale nadal mają zastosowanie wielu formantów.  
  
 W porównaniu z resztą inicjowania najczęściej wykonywane przez formant ActiveX, tworzenie okna jest bardzo kosztowna operacja. Najlepiej, jeśli formant może odroczyć tworzenia okna, dopóki nie jest to bezwzględnie konieczne.  
  
 Wiele formantów zbędna, nie będzie aktywny, są one widoczne w kontenerze przez cały czas. Często formant może pozostawać w stan nieaktywny, dopóki użytkownik wykonuje operację wymagającą staje się aktywny (na przykład kliknięcie myszą lub naciśnięcie klawisza TAB). Aby spowodować, że formant do nieaktywnego, dopóki kontenera musi aktywować go, Usuń **OLEMISC_ACTIVATEWHENVISIBLE** flagę z formantu dodatkowych flag:  
  
 [!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]  
  
 **OLEMISC_ACTIVATEWHENVISIBLE** flagi automatycznie zostanie pominięty, Jeśli wyłączysz **aktywacji, gdy widoczny** opcji [ustawienia kontroli](../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony MFC ActiveX Kreator formantów podczas tworzenia formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC: optymalizacja](../mfc/mfc-activex-controls-optimization.md)

