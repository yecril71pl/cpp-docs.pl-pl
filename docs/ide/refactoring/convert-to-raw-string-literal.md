---
title: Konwertuj na literał nieprzetworzonego ciągu
ms.date: 11/16/2016
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
ms.openlocfilehash: bf492e6796b9d2342b5952abb093bddd5ede114b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349429"
---
# <a name="convert-to-raw-string-literal"></a>Konwertuj na literał nieprzetworzonego ciągu

**Co:** Umożliwia włączenie dowolnego ciągu do C++ nieprzetworzony literał ciągu.

**Kiedy:** Masz ciąg zawierający znaki ucieczki, które nie powinny być przetwarzane jako znaki ucieczki.

**Dlaczego:** Możesz znaki ucieczki double poza tym często prowadzi do ciągów mylące i nie można go odczytać.  Za pomocą surowe Literały ciągu sprawia, że ciągi znacznie łatwiejsze do odczytania.

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