---
title: Konwertuj na literał nieprzetworzonego ciągu
ms.date: 11/16/2016
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
ms.openlocfilehash: 5636e00bfe8655d84fb2e4b64e0391324ab35d7d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171817"
---
# <a name="convert-to-raw-string-literal"></a>Konwertuj na literał nieprzetworzonego ciągu

**Co:** Umożliwia przekształcenie dowolnego ciągu w C++ nieprzetworzony literał ciągu.

**Kiedy:** Istnieje ciąg z znakami ucieczki, które nie powinny być przetwarzane jako znaki ucieczki.

**Dlaczego:** Można wypróbować znaki podwójnej precyzji, ale często prowadzi to do mylących i nieczytelnych ciągów.  Użycie nieprzetworzonych literałów ciągu sprawia, że ciągi są znacznie łatwiejsze do odczytu.

**Jaka**

1. Umieść kursor tekstowy lub wskaźnik myszy nad ciągiem ucieczki do przekonwertowania.

   ![Wyróżniony kod](images/stringliteral_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij **klawisze CTRL +.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** , a następnie wybierz polecenie **Konwertuj na nieprzetworzony literał ciągu** z menu kontekstowego.
   * **Wskaźnik**
     * Kliknij prawym przyciskiem myszy kod, wybierz menu **szybkie akcje i refaktoryzacje** i wybierz polecenie **Konwertuj na nieprzetworzony literał ciągu** z menu kontekstowego.
     * Kliknij ikonę ![żarówki](images/bulb.png), która pojawia się na lewym marginesie, a następnie wybierz pozycję **Konwertuj na nieprzetworzony literał ciągu** z menu kontekstowego.

1. Ciąg zostanie natychmiast przekonwertowany na nieprzetworzony literał ciągu.

   ![Wynik literału nieprzetworzonego ciągu](images/stringliteral_result.png)
