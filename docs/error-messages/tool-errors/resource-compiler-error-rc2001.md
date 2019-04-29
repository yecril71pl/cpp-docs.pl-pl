---
title: Błąd kompilatora zasobów RC2001
ms.date: 11/04/2016
f1_keywords:
- RC2001
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
ms.openlocfilehash: f4755e04a744d94636b4b37aaf727e0d733008ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346694"
---
# <a name="resource-compiler-error-rc2001"></a>Błąd kompilatora zasobów RC2001

Nowy wiersz w stałej

Stała typu string była kontynuowana w drugim wierszu bez kreski ułamkowej odwróconej (**\\**) lub zamknięcie i otwarcie podwójnego cudzysłowu (**"**).

Aby przerwać stała ciągu, która znajduje się na dwa wiersze w pliku źródłowym, wykonaj jedną z następujących czynności:

- Koniec pierwszy wiersz od znaku kontynuacji wiersza, ukośnika odwrotnego.

- Zamknij ciąg znaków w pierwszym wierszu za pomocą podwójnego cudzysłowu i otwórz ciągu w następnym wierszu, kolejny znak cudzysłowu.

Nie jest wystarczające, aby zakończyć pierwszy wiersz z \n, sekwencja unikowa osadzania znak nowego wiersza w stałą typu string.