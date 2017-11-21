---
title: Implementowanie czyste elementy wirtualne | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e753654ebada3c508858ff0ceb3d840e4a592c4c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="implement-pure-virtuals"></a>Zaimplementuj czyste elementy wirtualne
**Co:** pozwala natychmiast wygenerować kod wymagany do zaimplementowania w klasie czystych metod wirtualnych. 

**Kiedy:** ma być dziedziczona z klasy z czystych funkcji wirtualnych.  

**Dlaczego:** ręcznie można zaimplementować wszystkie czystych funkcji wirtualnych jeden po drugim, jednak funkcja ta automatycznie wygeneruje wszystkie podpisy metod.

**Jak:**

1. Umieść kursor tekstu lub mysz nad klasą, w którym chcesz zaimplementować czystych funkcji wirtualnych klasy podstawowej.

   ![Wyróżniony kod](images/virtuals_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz  **zaimplementować wszystkie czyste elementy wirtualne dla klasy*ClassName*"** z menu kontekstowego, gdzie  *ClassName* to nazwa wybranej klasy.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz  **zaimplementować wszystkie czyste elementy wirtualne dla klasy*ClassName*"** z menu kontekstowego, gdzie  *ClassName* to nazwa wybranej klasy.

1. Podpisy czystej metody wirtualnej zostanie automatycznie utworzone, gotowy do zaimplementowania.

   ![Powoduje implementowania czystych elementów wirtualnych](images/virtuals_result.png)
