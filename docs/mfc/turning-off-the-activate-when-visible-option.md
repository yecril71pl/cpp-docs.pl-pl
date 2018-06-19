---
title: Wyłączanie aktywacji podczas widoczna opcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], activate options
- Activate When Visible option [MFC]
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5625e7d05ea09188aaa2ea50ca629204a4bacc07
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384784"
---
# <a name="turning-off-the-activate-when-visible-option"></a>Wyłączanie opcji aktywacji w przypadku widoczności
Formant ma dwa stany podstawowe: aktywnych i nieaktywnych. Zazwyczaj te stany zostały rozróżnianych na podstawie tego, czy formant miał okna. Aktywny formant miał okna; nie kontrolkę, która jest nieaktywne. Ta różnica nie jest już uniwersalnych wraz z wprowadzeniem aktywacji niepowiązanej z oknami, ale nadal mają zastosowanie wielu formantów.  
  
 W porównaniu z resztą inicjowania najczęściej wykonywane przez formant ActiveX, tworzenie okna jest bardzo kosztowna operacja. Najlepiej, jeśli formant może odroczyć tworzenia okna, dopóki nie jest to bezwzględnie konieczne.  
  
 Wiele formantów zbędna, nie będzie aktywny, są one widoczne w kontenerze przez cały czas. Często formant może pozostawać w stan nieaktywny, dopóki użytkownik wykonuje operację wymagającą staje się aktywny (na przykład kliknięcie myszą lub naciśnięcie klawisza TAB). Aby spowodować, że formant do nieaktywnego, dopóki kontenera musi aktywować go, Usuń **OLEMISC_ACTIVATEWHENVISIBLE** flagę z formantu dodatkowych flag:  
  
 [!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]  
  
 **OLEMISC_ACTIVATEWHENVISIBLE** flagi automatycznie zostanie pominięty, Jeśli wyłączysz **aktywacji, gdy widoczny** opcji [ustawienia kontroli](../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony MFC ActiveX Kreator formantów podczas tworzenia formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC: optymalizacja](../mfc/mfc-activex-controls-optimization.md)

