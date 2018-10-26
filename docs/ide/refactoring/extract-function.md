---
title: Wyodrębnij funkcję | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: e31d1249-9705-4511-acbd-9f6fe73bdf2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e032c2f1579294431b01d5a7695bf2c8a35aa421
ms.sourcegitcommit: 072e12d6b7a242765bdcc9afe4a14a284ade01fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2018
ms.locfileid: "50136123"
---
# <a name="extract-function"></a>Wyodrębnij funkcję
**Co:** pozwala włączyć fragment kodu do jego własnej funkcji.

**Kiedy:** masz fragmentu istniejącego kodu w niektórych funkcji, która musi zostać wywołana z inną funkcję.

**Dlaczego:** można kopiujesz/wklejasz kod, ale, co może spowodować dublowania.  Lepszym rozwiązaniem jest Refaktoryzacja tego fragmentu do jego własnej funkcji, która może być wywoływany za darmo przez innych funkcji.

**Jak:**

1. Wyróżnij kod w celu wyodrębnienia:

   ![Wyróżniony kod](images/extractfunction_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + M**.  (Należy pamiętać, że skrót klawiaturowy może różnić się w oparciu o profilu, który wybrano.)
     * Naciśnij klawisz **Ctrl +.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Wyodrębnij funkcję (funkcja eksperymentalna)** z menu kontekstowego.
   * **Myszy**
     * Wybierz **Edytuj > Refaktoryzuj > Wyodrębnianie (eksperymentalne) funkcja**.
     * Kliknij prawym przyciskiem myszy ten kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Wyodrębnij funkcję (funkcja eksperymentalna)** z menu kontekstowego.
     * Kliknij przycisk ![żarówki](images/bulb.png) ikonę, która pojawia się na lewym marginesie, a następnie wybierz pozycję **Wyodrębnij funkcję (funkcja eksperymentalna)** z menu kontekstowego.

1. W **Wyodrębnij funkcję/metodę (funkcja eksperymentalna)** , wprowadź nową nazwę funkcji, wybierz, gdzie kod do umieszczenia, a kliknij **OK** przycisku.

   ![Wyodrębnij funkcję okna dialogowego](images/extractfunction_dialog.png)

1. Zostanie utworzona nowa funkcja w przypadku, gdy został określony, prototypu funkcji w odpowiedni plik nagłówkowy i oryginalny kod zostanie zmieniona tak, aby wywołać tę funkcję.

   ![Wyodrębnienie wyniku funkcji](images/extractfunction_result.png)
