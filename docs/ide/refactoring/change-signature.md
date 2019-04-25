---
title: Zmień podpis
ms.date: 11/16/2016
ms.assetid: 8daaa060-7305-4035-99d2-8b460b4f4454
ms.openlocfilehash: ec42fd00ecf48fb700042f02543e3fe194fe6975
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265237"
---
# <a name="change-signature"></a>Zmień podpis

**Co:** Umożliwia modyfikowanie parametrów funkcji.

**Kiedy:** Chcesz zmienić kolejność, dodać, usunąć lub zmodyfikować parametrów funkcji, które jest obecnie używana w różnych lokalizacjach.

**Dlaczego:** Można ręcznie samodzielnie, zmienić te parametry i następnie Znajdź wszystkie wywołania tej funkcji i zmień je pojedynczo, ale która może prowadzić do błędów.  To narzędzie refaktoryzacji będzie automatycznie wykonywać zadania.

**Jak:**

1. Umieść kursor tekstu lub myszy w nazwie metody, aby zmodyfikować lub jednego z jego użycia:

   ![Wyróżniony kod](images/changesignature_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl + R**, następnie **klawisze Ctrl + O**.  (Należy pamiętać, że skrót klawiaturowy może różnić się w oparciu o profilu, który wybrano.)
     * Naciśnij klawisz **Ctrl +.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zmień podpis** z menu kontekstowego.
   * **Myszy**
     * Wybierz **Edytuj > Refaktoryzuj > Zmień kolejność parametrów**.
     * Kliknij prawym przyciskiem myszy ten kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zmień podpis** z menu kontekstowego.

1. W **Zmień podpis** okna dialogowego, które się pojawi, umożliwia przyciski po prawej stronie Zmień sygnaturę metody:

   ![Zmień podpis w oknie dialogowym](images/changesignature_dialog.png)

   | Przycisk | Opis
   | ------ | ---
   | **Góra/dół**    | Przenieś wybrany parametr w górę i w dół listy
   | **Add**        | Dodano nowy parametr do listy
   | **Usuń**     | Usuń wybrany parametr z listy
   | **Modyfikowanie**     | Zmodyfikuj wybrany parametr, zmieniając jej typ nazwy i czy jest to opcjonalne, a wartością wprowadzonego kodu, co będzie
   | **Przywróć**     | Przywrócić oryginalny stan wybrany parametr
   | **Przywróć wszystkie** | Przywróć wszystkie parametry do pierwotnego stanu

   > [!TIP]
   > Użyj **odwołania (wersja zapoznawcza) Pomiń zmieni się, gdy przypadku potwierdzenia wszystkich odwołań** pole wyboru, aby zmiany od razu bez wyświetlanie pierwsze okno podglądu.

   Podczas dodawania lub modyfikowania parametru, zostanie wyświetlony **Dodaj parametr** lub **Edytuj parametr** okna.

   ![Dodawanie/Modyfikowanie parametrów](images/changesignature_addmodify.png)

   W tym miejscu możesz wykonać następujące czynności:

   | Wpis | Opis
   | ----- | ---
   | **Typ**               | Typ parametru (int, dwukrotnie, float, itp.)
   | **Nazwa**               | Nazwa parametru
   | **Parametr opcjonalny** | Sprawia, że parametr opcjonalnie określić
   | **Wartość wprowadzonego kodu**     | Wartość wstawiony wszelkie wywołania funkcji, gdy parametr nie jest określony (prawidłowe tylko dla **Dodaj**)
   | **Wartość domyślna**      | Wartość używana przez funkcję, jeśli nie określono elementu wywołującego (prawidłowe tylko dla **następujące parametry opcjonalne**)

1. Użyj **zakres wyszukiwania** listy rozwijanej wybierz, jeśli zmiany zostaną zastosowane do projektu lub całe rozwiązanie.

1. Gdy skończysz, naciśnij klawisz **OK** , aby wprowadzić zmiany.  Upewnij się, że żądana jest zmieniana odpowiednio.  Użyj pól wyboru w górnej połowie okna, aby włączyć lub wyłączyć, zmiana nazwy dowolnego elementu.

   ![Zmienianie podpisu (wersja zapoznawcza)](images/changesignature_preview.png)

1. Gdy wszystko będzie wyglądać dobrze, kliknij przycisk **Zastosuj** przycisk, a funkcja zostanie zmieniona w kodzie źródłowym.

   ![Zmień podpis wynik](images/changesignature_result.png)