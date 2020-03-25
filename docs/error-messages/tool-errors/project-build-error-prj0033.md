---
title: Błąd PRJ0033 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0033
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
ms.openlocfilehash: 141355ac49ec4722e85b5d4c25240e8048a72c9a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192199"
---
# <a name="project-build-error-prj0033"></a>Błąd PRJ0033 kompilacji projektu

Właściwość "dodatkowe zależności" dla niestandardowego kroku kompilacji dla pliku "File" zawiera "Macro", który szacuje wartość "macro_expansion".

Niestandardowy krok kompilacji w pliku zawierał błąd w dodatkowej zależności prawdopodobnie z powodu problemu z oceną makra. Ten błąd może również oznaczać, że ścieżka jest źle sformułowana, zawierającą znaki lub kombinacje znaków, które nie są dozwolone w ścieżce pliku.

Aby rozwiązać ten problem, napraw makro lub Popraw specyfikację ścieżki. Szacowana ścieżka jest ścieżką bezwzględną z katalogu projektu.
