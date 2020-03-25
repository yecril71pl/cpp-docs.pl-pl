---
title: Błąd PRJ0032 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0032
helpviewer_keywords:
- PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
ms.openlocfilehash: 62efa0e72c6fbe4bd38983ff0507923392427c04
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192487"
---
# <a name="project-build-error-prj0032"></a>Błąd PRJ0032 kompilacji projektu

Właściwość "Outputs" niestandardowego kroku kompilacji na poziomie projektu zawiera "makro", które oblicza wartość "macro_expansion".

Niestandardowy krok kompilacji w projekcie miał prawdopodobnie nieprawidłowe wyniki wyjściowe z powodu problemu z oceną makra. Ten błąd może również oznaczać, że ścieżka jest źle sformułowana, zawierającą znaki lub kombinacje znaków, które nie są dozwolone w ścieżce pliku.

Aby rozwiązać ten problem, napraw makro lub Popraw specyfikację ścieżki. Szacowana ścieżka jest ścieżką bezwzględną z katalogu projektu.
