---
title: Zmień nazwę | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 64b42a88-3bd9-4399-8b96-75bceffc353b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a064527f6afcbf91be3fb4e51180be647c1f506
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="rename"></a>Zmień nazwę
**Co:** pozwala zmienić identyfikatory symboli kodu, takich jak pola, zmienne lokalne, metody, obszary nazw, właściwości i typów.

**Kiedy:** chcesz zmienić element bezpiecznie bez konieczności Znajdź wszystkie wystąpienia i kopiowania/wklejania nową nazwę.  

**Dlaczego:** kopiowania i wklejania nową nazwę dla całego projektu prawdopodobnie będą powodować błędy.  To narzędzie refaktoryzacji dokładnie będzie wykonywać operacji zmiany nazwy.

**Jak:**

1. Zaznacz lub umieść kursor tekst wewnątrz można zmienić nazwy elementu:

   ![Wyróżniony kod](images/rename_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + R**.  (Należy pamiętać, że skrót klawiaturowy mogą być różne oparte na profil, który wybrano).
   * **Myszy**
     * Wybierz **Edytuj > Refaktoryzuj > Zmień nazwę**.
     * Kliknij prawym przyciskiem myszy kod i wybierz **zmienić**.

1. W **zmienić** oknie wyskakującym, wprowadź nową nazwę dla wybranego elementu i kliknij przycisk **Podgląd** przycisku.  Zmień **zakres wyszukiwania** Aby rozszerzyć lub zawęzić zakres zmianą nazwy.

   ![Zmień nazwę okna dialogowego](images/rename_dialog.png)

   > [!TIP]
   > Wersja zapoznawcza można pominąć, sprawdzając **Pomiń podgląd zmian wszystkich odwołań** opcji.

1. Gdy **zmienić podgląd zmian -** zostanie wyświetlone okno, upewnij się, że zażądano zmian odpowiednio.  Użyj pól wyboru w górnej połowie okna, aby włączyć lub wyłączyć, zmiana nazwy każdego elementu.

   ![Zmień nazwę podglądu](images/rename_preview.png)

1. Jeśli wszystko wygląda dobrze, kliknij przycisk **Zastosuj** przycisk i elementu zostanie zmieniona w kodzie źródłowym.
