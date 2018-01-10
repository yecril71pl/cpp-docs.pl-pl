---
title: Zmienianie podpisu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8daaa060-7305-4035-99d2-8b460b4f4454
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5280b4940c2a52fc6e72b397300040ca4c1ac92e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="change-signature"></a>Zmiana podpisu
**Co:** umożliwia modyfikowanie parametrów funkcji.

**Kiedy:** chcesz zmienić kolejność, dodać, usunąć ani zmodyfikować parametrów funkcji, które jest obecnie używana w różnych lokalizacjach.  

**Dlaczego:** można ręcznie samodzielnie, zmienić te parametry i następnie odnaleźć wszystkie wywołania tej funkcji i zmień je jeden po drugim, ale który może prowadzić do błędów.  To narzędzie refaktoryzacji będzie automatycznie wykonywać zadania.

**Jak:**

1. Umieść kursor tekst lub myszy wewnątrz nazwę metody, aby zmodyfikować lub jednego z jego użycia:

   ![Wyróżniony kod](images/changesignature_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + O**.  (Należy pamiętać, że skrót klawiaturowy mogą być różne oparte na profil, który wybrano).
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **zmiany sygnatury** z menu kontekstowego.
   * **Myszy**
     * Wybierz **Edytuj > Refaktoryzuj > zmiany kolejności parametrów**.
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **zmiany sygnatury** z menu kontekstowego.

1. W **Zmienianie podpisu** okna dialogowego, które pojawia się, umożliwia przycisków po prawej stronie Zmień podpis metody:

   ![Zmiana podpisu w oknie dialogowym](images/changesignature_dialog.png)

   | Przycisk | Opis
   | ------ | ---
   | **Góra/dół**    | Przenieś zaznaczony parametr w górę i w dół listy
   | **Dodaj**        | Dodaj nowy parametr do listy
   | **Usuń**     | Usuń zaznaczony parametr z listy
   | **Modyfikowanie**     | Zmodyfikuj wybrany parametr, zmieniając jej typ, nazwa i czy jest opcjonalny, a wartością wprowadzony, co będzie
   | **Przywróć**     | Przywrócić oryginalny stan wybrany parametr
   | **Przywróć wszystkie** | Przywróć wszystkie parametry do pierwotnego stanu

   > [!TIP]
   > Użyj **Pomiń podgląd zmian odwołań przypadku potwierdzenia wszystkich odwołań** pole wyboru, aby zmiany natychmiast bez wyświetlanie pierwszego okna podglądu.

   Podczas dodawania lub modyfikowania parametru, zostanie wyświetlony **Dodaj parametr** lub **Edytuj parametr** okna.

   ![Dodawanie/Modyfikowanie parametrów](images/changesignature_addmodify.png)

   W tym miejscu można wykonywać następujące czynności:

   | Wpis | Opis
   | ----- | ---
   | **Typ**               | Typ parametru (int, kliknij dwukrotnie, float, itp.)
   | **Nazwa**               | Nazwa parametru
   | **Opcjonalny parametr** | Sprawia, że parametr opcjonalnie określić
   | **Wprowadzony wartość**     | Wartość wstawiana do żadnych wywołań funkcji, której nie określono parametru (dotyczy tylko **Dodaj**)
   | **Wartość domyślna**      | Wartość używana przez funkcję, jeśli element wywołujący nie określił (dotyczy tylko **następujące parametry opcjonalne**)

1. Użyj **zakres wyszukiwania** listy rozwijanej, aby wybrać, jeśli zmiany zostaną zastosowane do projektu lub całego rozwiązania.

1. Po zakończeniu naciśnij klawisz **OK** przycisk, aby wprowadzić zmiany.  Upewnij się, że żądanej zmian odpowiednio.  Użyj pól wyboru w górnej połowie okna, aby włączyć lub wyłączyć, zmiana nazwy każdego elementu.

   ![Zmiana podpisu w wersji zapoznawczej](images/changesignature_preview.png)

1. Jeśli wszystko wygląda dobrze, kliknij przycisk **Zastosuj** przycisku oraz funkcji zostanie zmieniony w kodzie źródłowym.

   ![Zmiana wyniku podpisu](images/changesignature_result.png)