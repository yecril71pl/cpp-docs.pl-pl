---
title: Błąd kompilatora zasobów RC2001 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2001
dev_langs:
- C++
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d75d0f906ba0d7be75ca5177bc1f58bccd226251
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039975"
---
# <a name="resource-compiler-error-rc2001"></a>Błąd kompilatora zasobów RC2001

Nowy wiersz w stałej

Stała typu string była kontynuowana w drugim wierszu bez kreski ułamkowej odwróconej (**\\**) lub zamknięcie i otwarcie podwójnego cudzysłowu (**"**).

Aby przerwać stała ciągu, która znajduje się na dwa wiersze w pliku źródłowym, wykonaj jedną z następujących czynności:

- Koniec pierwszy wiersz od znaku kontynuacji wiersza, ukośnika odwrotnego.

- Zamknij ciąg znaków w pierwszym wierszu za pomocą podwójnego cudzysłowu i otwórz ciągu w następnym wierszu, kolejny znak cudzysłowu.

Nie jest wystarczające, aby zakończyć pierwszy wiersz z \n, sekwencja unikowa osadzania znak nowego wiersza w stałą typu string.