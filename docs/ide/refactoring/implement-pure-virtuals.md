---
title: Zaimplementuj czyste elementy wirtualne
ms.date: 11/16/2016
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
ms.openlocfilehash: 59e4519f57a1d9bd9ba1cee1ed6ae41bea785a9f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265094"
---
# <a name="implement-pure-virtuals"></a>Zaimplementuj czyste elementy wirtualne

**Co:** Pozwala natychmiast wygenerować kod wymagany do implementowania czystych metod wirtualnych w klasie.

**Kiedy:** Chcesz dziedziczyć klasy z czystych funkcji wirtualnych.

**Dlaczego:** Wszystkie czyste funkcje wirtualne jeden po drugim, można zaimplementować ręcznie, jednak tej funkcji będzie generowana automatycznie wszystkich podpisów metody.

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
