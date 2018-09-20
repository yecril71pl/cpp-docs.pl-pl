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
ms.openlocfilehash: 7a00eed341e0fc1ca8573e2f66744ea04055f259
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399215"
---
# <a name="rename"></a>Zmień nazwę
**Co:** umożliwia zmianę nazwy identyfikatorów w celu symbole kodu, takie jak pola, zmienne lokalne, metody, przestrzenie nazw, właściwości i typów.

**Kiedy:** chcesz bezpiecznie zmienić coś bez konieczności Znajdź wszystkie wystąpienia i kopiowanie/wklejanie nowej nazwy.

**Dlaczego:** kopiowanie i wklejanie nową nazwę dla całego projektu, prawdopodobnie będą powodować błędy.  To narzędzie refaktoryzacji dokładnie wykona akcję zmiany nazwy.

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
