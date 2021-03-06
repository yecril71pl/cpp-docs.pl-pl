---
title: Wyodrębnij funkcję
ms.date: 11/16/2016
ms.assetid: e31d1249-9705-4511-acbd-9f6fe73bdf2d
ms.openlocfilehash: ec3b9a0aeaef9e418b457bafdfb9bb1bbd2edffc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349369"
---
# <a name="extract-function"></a>Wyodrębnij funkcję

**Co:** Pozwala włączyć fragment kodu do jego własnej funkcji.

**Kiedy:** W niektórych funkcji, która musi zostać wywołana z innej funkcji znajduje się fragment kodu z istniejących.

**Dlaczego:** Można kopiujesz/wklejasz kod, ale, co może spowodować dublowania.  Lepszym rozwiązaniem jest Refaktoryzacja tego fragmentu do jego własnej funkcji, która może być wywoływany za darmo przez innych funkcji.

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
