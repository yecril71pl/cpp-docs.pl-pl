---
title: Zmień sygnaturę
ms.date: 11/16/2016
ms.assetid: 8daaa060-7305-4035-99d2-8b460b4f4454
ms.openlocfilehash: 1599a7900e33db61994ea75581f9d87b1aee83f9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171908"
---
# <a name="change-signature"></a>Zmień sygnaturę

**Co:** Umożliwia modyfikowanie parametrów funkcji.

**Kiedy:** Należy zmienić kolejność, dodać, usunąć lub zmodyfikować parametry funkcji, które są obecnie używane w różnych lokalizacjach.

**Dlaczego:** Możesz ręcznie zmienić te parametry, a następnie znaleźć wszystkie wywołania tej funkcji i zmienić je jeden do jednego, ale może to prowadzić do błędów.  To narzędzie refaktoryzacji będzie automatycznie wykonywać zadania.

**Jaka**

1. Umieść kursor tekstowy lub mysz wewnątrz nazwy metody do zmodyfikowania lub jednego z jej użycia:

   ![Wyróżniony kod](images/changesignature_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisze **Ctrl + R**, a następnie **Ctrl + O**.  (Należy pamiętać, że skrót klawiaturowy może różnić się w oparciu o profilu, który wybrano.)
     * Naciśnij **klawisze CTRL +.** Aby wyzwolić menu **szybkie akcje i refabryki** , a następnie wybierz pozycję **Zmień sygnaturę** z menu kontekstowego.
   * **Wskaźnik**
     * Wybierz pozycję **edytuj > refaktoryzacja > Zmień kolejność parametrów**.
     * Kliknij prawym przyciskiem myszy kod, wybierz menu **szybkie akcje i refaktoryzacje** i wybierz polecenie **Zmień sygnaturę** z menu kontekstowego.

1. W oknie dialogowym **Zmienianie podpisu** , które się pojawia, możesz użyć przycisków z prawej strony, aby zmienić sygnaturę metody:

   ![Zmień podpis w oknie dialogowym](images/changesignature_dialog.png)

   | Button | Opis
   | ------ | ---
   | **W górę/w dół**    | Przenieś wybrany parametr w górę i w dół listy
   | **Dodaj**        | Dodaj nowy parametr do listy
   | **Usuń**     | Usuń wybrany parametr z listy
   | **Zmodyfikować**     | Zmodyfikuj wybrany parametr, zmieniając jego typ, nazwę i niezależnie od tego, czy jest on opcjonalny, i jakie wartości wprowadzano.
   | **Stan**     | Przywróć wybrany parametr jako oryginalny stan
   | **Przywróć wszystko** | Przywróć wszystkie parametry do ich oryginalnego stanu

   > [!TIP]
   > Użyj pola wyboru **Pomiń odwołanie w wersji zapoznawczej, jeśli wszystkie odwołania są zatwierdzone** , aby natychmiast wprowadzić zmiany bez okna podglądu usuwanie.

   Dodanie lub zmodyfikowanie parametru spowoduje wyświetlenie okna **Dodawanie parametru** lub **Edytowanie parametru** .

   ![Dodaj/Modyfikuj parametr](images/changesignature_addmodify.png)

   W tym miejscu można wykonać następujące czynności:

   | Wpis | Opis
   | ----- | ---
   | **Typ**               | Typ parametru (int, Double, float itp.)
   | **Nazwa**               | Nazwa parametru.
   | **Parametr opcjonalny** | Sprawia, że parametr jest opcjonalnie określony
   | **Wartość wprowadzona**     | Wartość wstawiona do dowolnych wywołań do funkcji, w której parametr nie jest określony (prawidłowy tylko dla **dodania**)
   | **Wartość domyślna**      | Wartość używana przez funkcję, jeśli obiekt wywołujący nie określa jednego (prawidłowy dla **parametrów opcjonalnych**)

1. Użyj listy rozwijanej **zakres wyszukiwania** , aby wybrać, czy zmiany będą stosowane do projektu, czy całego rozwiązania.

1. Po zakończeniu kliknij przycisk **OK** , aby wprowadzić zmiany.  Upewnij się, że żądane zmiany są wprowadzane odpowiednio.  Użyj pól wyboru w górnej połowie okna, aby włączyć lub wyłączyć zmianę nazwy dowolnego elementu.

   ![Zmień podgląd sygnatur](images/changesignature_preview.png)

1. Gdy wszystko wygląda dobrze, kliknij przycisk **Zastosuj** , a funkcja zostanie zmieniona w kodzie źródłowym.

   ![Zmień wynik podpisu](images/changesignature_result.png)
