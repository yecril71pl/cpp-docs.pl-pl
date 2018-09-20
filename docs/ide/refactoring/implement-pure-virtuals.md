---
title: Zaimplementuj czyste elementy wirtualne | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 234ae9a67bcbc60ea156fbacb5169d0bd1573a91
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442763"
---
# <a name="implement-pure-virtuals"></a>Zaimplementuj czyste elementy wirtualne
**Co:** pozwala natychmiast wygenerować kod wymagany do implementowania czystych metod wirtualnych w klasie.

**Kiedy:** ma być dziedziczona z klasy za pomocą czystych funkcji wirtualnych.

**Dlaczego:** wszystkie czyste funkcje wirtualne jeden po drugim, można zaimplementować ręcznie, jednak ta funkcja będzie generowana automatycznie wszystkich podpisów metody.

**Jak:**

1. Umieść kursor tekstu lub myszy nad klasy, w której chcesz zaimplementować czyste funkcje wirtualne klasy bazowej.

   ![Wyróżniony kod](images/virtuals_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl +.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **zaimplementuj czyste elementy wirtualne dla klasy*ClassName*"** z menu kontekstowego, gdzie  *ClassName* to nazwa wybranej klasy.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **zaimplementuj czyste elementy wirtualne dla klasy*ClassName*"** z menu kontekstowego, gdzie  *ClassName* to nazwa wybranej klasy.

1. Podpisy czystej metody wirtualnej będzie automatycznie utworzone, gotowy do zaimplementowania.

   ![Zaimplementuj czyste elementy wirtualne wyniku](images/virtuals_result.png)
