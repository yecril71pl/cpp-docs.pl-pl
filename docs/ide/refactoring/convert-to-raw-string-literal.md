---
title: Konwertuj na literał nieprzetworzonego ciągu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75037ea542a5bd2160d9a89138b12f82867002a5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388449"
---
# <a name="convert-to-raw-string-literal"></a>Konwertuj na literał nieprzetworzonego ciągu
**Co:** pozwala włączyć dowolny ciąg w języku C++ nieprzetworzonego ciągu literału.

**Kiedy:** ma ciągu znakami o zmienionym znaczeniu, które nie powinny być przetwarzane jako znaki ucieczki.

**Dlaczego:** możesz znaki ucieczki double poza tym często prowadzi do ciągów mylące i nie można go odczytać.  Za pomocą surowe Literały ciągu sprawia, że ciągi znacznie łatwiejsze do odczytania.

**Jak:**

1. Ustaw kursor tekstu lub myszy nad o zmienionym znaczeniu ciąg do przekonwertowania.

   ![Wyróżniony kod](images/stringliteral_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl +.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Konwertuj na nieprzetworzony literał ciągu** z menu kontekstowego.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy ten kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Konwertuj na nieprzetworzony literał ciągu** z menu kontekstowego.
     * Kliknij przycisk ![żarówki](images/bulb.png) ikonę, która pojawia się na lewym marginesie, a następnie wybierz pozycję **Konwertuj na nieprzetworzony literał ciągu** z menu kontekstowego.

1. Ten ciąg zostanie natychmiast przekonwertowany na nieprzetworzony literał ciągu.

   ![Wynik literał ciągu surowego](images/stringliteral_result.png)