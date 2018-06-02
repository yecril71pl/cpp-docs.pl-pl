---
title: Implementowanie czyste elementy wirtualne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afce516f2718a76658846ed4f992aeabff75330b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "33328029"
---
# <a name="implement-pure-virtuals"></a>Zaimplementuj czyste elementy wirtualne
**Co:** pozwala natychmiast wygenerować kod wymagany do zaimplementowania w klasie czystych metod wirtualnych. 

**Kiedy:** ma być dziedziczona z klasy z czystych funkcji wirtualnych.  

**Dlaczego:** ręcznie można zaimplementować wszystkie czystych funkcji wirtualnych jeden po drugim, jednak funkcja ta automatycznie wygeneruje wszystkie podpisy metod.

**Jak:**

1. Umieść kursor tekstu lub mysz nad klasą, w którym chcesz zaimplementować czystych funkcji wirtualnych klasy podstawowej.

   ![Wyróżniony kod](images/virtuals_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **zaimplementować wszystkie czyste elementy wirtualne dla klasy*ClassName*"** z menu kontekstowego, gdzie  *ClassName* to nazwa wybranej klasy.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **zaimplementować wszystkie czyste elementy wirtualne dla klasy*ClassName*"** z menu kontekstowego, gdzie  *ClassName* to nazwa wybranej klasy.

1. Podpisy czystej metody wirtualnej zostanie automatycznie utworzone, gotowy do zaimplementowania.

   ![Powoduje implementowania czystych elementów wirtualnych](images/virtuals_result.png)
