---
title: Błąd BSCMAKE BK1513
ms.date: 11/04/2016
f1_keywords:
- BK1513
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
ms.openlocfilehash: 3a16163f33814be18a67833995362ee9b13d8118
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197642"
---
# <a name="bscmake-error-bk1513"></a>Błąd BSCMAKE BK1513

Aktualizacja nieprzyrostowa wymaga wszystkich. Pliki SBR

BSCMAKE nie może utworzyć nowego pliku informacji o przeglądaniu (BSC), ponieważ co najmniej jeden plik. sbr został obcięty. Aby znaleźć nazwy obciętych plików SBR, przeczytaj ostrzeżenia [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) , które towarzyszą temu błędowi.

BSCMAKE może zaktualizować plik BSC z obciętym plikiem. sbr, ale nie może utworzyć nowego. BSCMAKE może utworzyć nowy plik BSC z następujących powodów:

- Brak pliku BSC.

- Określono nieprawidłową nazwę pliku dla pliku BSC.

- Uszkodzony plik BSC.

Aby rozwiązać ten problem, Usuń obcięte pliki SBR i Skompiluj ponownie lub wyczyść rozwiązanie i Skompiluj ponownie. (W środowisku IDE wybierz opcję **Kompiluj**, **Wyczyść rozwiązanie**, a następnie wybierz **kompilacja**, **Skompiluj ponownie rozwiązanie**).
