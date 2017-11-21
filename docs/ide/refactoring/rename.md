---
title: "Zmień nazwę | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64b42a88-3bd9-4399-8b96-75bceffc353b
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d8e4152a1c920a243be9d4aa23712420893e29f5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="rename"></a>Zmień nazwę
**Co:** pozwala zmienić identyfikatory symboli kodu, takich jak pola, zmienne lokalne, metody, obszary nazw, właściwości i typów.

**Kiedy:** chcesz zmienić element bezpiecznie bez konieczności Znajdź wszystkie wystąpienia i kopiowania/wklejania nową nazwę.  

**Dlaczego:** kopiowania i wklejania nową nazwę dla całego projektu prawdopodobnie będą powodować błędy.  To narzędzie refaktoryzacji dokładnie będzie wykonywać operacji zmiany nazwy.

**Jak:**

1. Zaznacz lub umieść kursor tekst wewnątrz można zmienić nazwy elementu:

   ![Wyróżniony kod](images/rename_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
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
