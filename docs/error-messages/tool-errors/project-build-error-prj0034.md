---
title: Błąd PRJ0034 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0034
helpviewer_keywords:
- PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
ms.openlocfilehash: bcb7e22d6a09e3435eb2236532101a1836c08a03
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192195"
---
# <a name="project-build-error-prj0034"></a>Błąd PRJ0034 kompilacji projektu

Właściwość "dodatkowe zależności" dla niestandardowego kroku kompilacji na poziomie projektu zawiera "makro", które oblicza wartość "macro_expansion".

Niestandardowy krok kompilacji w projekcie zawiera błąd w dodatkowej zależności prawdopodobnie z powodu problemu z oceną makra. Ten błąd może również oznaczać, że ścieżka jest źle sformułowana, zawierającą znaki lub kombinacje znaków, które nie są dozwolone w ścieżce pliku.

Aby rozwiązać ten problem, napraw makro lub Popraw specyfikację ścieżki. Szacowana ścieżka jest ścieżką bezwzględną z katalogu projektu.
