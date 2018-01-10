---
title: "Konwertuj na nieprzetworzony literał ciągu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 12aa512270ecce4564561634f99be9cbf155448a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="convert-to-raw-string-literal"></a>Konwertuj na nieprzetworzony literał ciągu
**Co:** pozwala włączyć do nieprzetworzony ciąg C++ dowolny ciąg literału.

**Kiedy:** być ciągiem o zmienionym znaczeniu znaki, których nie można przetwarzać jako zmienionym znaków.

**Dlaczego:** można znaków podwójnego anulowania, ale często prowadzi do ciągów trudne i nie można go odczytać.  Za pomocą nieprzetworzonego ciągu literałów sprawia, że ciągi znacznie łatwiejsze do odczytu.

**Jak:**

1. Umieść kursor tekstu lub mysz nad zmienionym ciąg do przekonwertowania.

   ![Wyróżniony kod](images/stringliteral_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **przekonwertować surowego literału ciągu** z menu kontekstowego.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **przekonwertować surowego literału ciągu** z menu kontekstowego.
     * Kliknij przycisk ![żarówka](images/bulb.png) ikonę, która pojawia się w lewym marginesie i wybierz **przekonwertować surowego literału ciągu** z menu kontekstowego.

1. Ten ciąg zostanie natychmiast skonwertowana na nieprzetworzonego literału ciągu.  

   ![Surowego literału ciągu wyników](images/stringliteral_result.png)