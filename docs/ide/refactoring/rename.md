---
title: Zmień nazwę
ms.date: 11/16/2016
ms.assetid: 64b42a88-3bd9-4399-8b96-75bceffc353b
ms.openlocfilehash: a747784f46341f130d1271fd0f15475b63d7b6d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265025"
---
# <a name="rename"></a>Zmień nazwę

**Co:** Umożliwia zmianę nazwy identyfikatorów w celu symbole kodu, takie jak pola, zmienne lokalne, metody, przestrzenie nazw, właściwości i typów.

**Kiedy:** Chcesz coś bezpiecznie zmienić bez konieczności Znajdź wszystkie wystąpienia i kopiowanie/wklejanie nowej nazwy.

**Dlaczego:** Kopiowanie i wklejanie nową nazwę dla całego projektu, prawdopodobnie będą powodować błędy.  To narzędzie refaktoryzacji dokładnie wykona akcję zmiany nazwy.

**Jak:**

1. Zaznacz lub umieść kursor tekstu w można zmienić nazwy elementu:

   ![Wyróżniony kod](images/rename_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + R**.  (Należy pamiętać, że skrót klawiaturowy może różnić się w oparciu o profilu, który wybrano.)
   * **Myszy**
     * Wybierz **Edytuj > Refaktoryzuj > Zmień nazwę**.
     * Kliknij prawym przyciskiem myszy ten kod, a następnie wybierz pozycję **Zmień nazwę**.

1. W **Zmień nazwę** okna, które się pojawi, wprowadź nową nazwę wybranego elementu, a następnie kliknij przycisk **Podgląd** przycisku.  Zmiana **zakres wyszukiwania** Jeśli potrzebujesz rozszerzyć lub zawęzić zakres zmianą nazwy.

   ![Zmienianie nazwy okna dialogowego](images/rename_dialog.png)

   > [!TIP]
   > Możesz pominąć korzystania z wersji zapoznawczej, sprawdzając **Pomiń podgląd zmian w przypadku wszystkich odwołań** opcji.

1. Gdy **podgląd zmian — zmiana nazwy** pojawi się okno, upewnij się, że zażądano zmian odpowiednio.  Użyj pól wyboru w górnej połowie okna, aby włączyć lub wyłączyć, zmiana nazwy dowolnego elementu.

   ![Zmień nazwę (wersja zapoznawcza)](images/rename_preview.png)

1. Gdy wszystko będzie wyglądać dobrze, kliknij przycisk **Zastosuj** przycisk, a element zostanie zmieniona w kodzie źródłowym.
