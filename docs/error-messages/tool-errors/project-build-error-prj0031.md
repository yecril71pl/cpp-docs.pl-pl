---
title: Błąd PRJ0031 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0031
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
ms.openlocfilehash: e13236f65aaca778a297cdd2942c07b75dd701d0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192500"
---
# <a name="project-build-error-prj0031"></a>Błąd PRJ0031 kompilacji projektu

Właściwość "Outputs" niestandardowego kroku kompilacji dla pliku "File" zawiera "Macro", który szacuje wartość "macro_expansion".

Niestandardowy krok kompilacji w pliku miał prawdopodobnie nieprawidłowe wyniki z powodu problemu z oceną makra. Ten błąd może również oznaczać, że ścieżka jest źle sformułowana, zawierającą znaki lub kombinacje znaków, które nie są dozwolone w ścieżce pliku.

Aby rozwiązać ten problem, napraw makro lub Popraw specyfikację ścieżki. Szacowana ścieżka jest ścieżką bezwzględną z katalogu projektu.
