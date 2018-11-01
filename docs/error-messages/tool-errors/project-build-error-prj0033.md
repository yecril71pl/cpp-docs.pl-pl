---
title: Błąd PRJ0033 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0033
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
ms.openlocfilehash: e074ee18508271b56686aa16f9012085ed3bd77d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586215"
---
# <a name="project-build-error-prj0033"></a>Błąd PRJ0033 kompilacji projektu

Właściwość 'Dodatkowe zależności' dla kroku kompilacji niestandardowej krok dla pliku 'Plik' zawiera 'makra"co ewaluowane jest"macro_expansion".

Wystąpił błąd podczas jego dodatkowe zależności, prawdopodobnie z powodu problemu z oceny makra znajdujących się w niestandardowego kroku kompilacji dla pliku. Ten błąd może również oznaczać, że ścieżka jest nieprawidłowo sformułowany, zawierające znaki lub kombinacje znaków, które nie są dozwolone w ścieżce pliku.

Aby rozwiązać ten problem, napraw makra, lub usuń specyfikację ścieżki. Oceniono ścieżka jest ścieżką bezwzględną z katalogu projektu.