---
title: Błąd PRJ0034 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0034
helpviewer_keywords:
- PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
ms.openlocfilehash: 7c078a3d2aef24df9151cb10f81c1b7423809e68
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549061"
---
# <a name="project-build-error-prj0034"></a>Błąd PRJ0034 kompilacji projektu

Właściwość 'Dodatkowe zależności' dla niestandardowego na poziomie projektu kompilacji kroku zawarte "makra" ewaluowane jest jako "macro_expansion".

Wystąpił błąd podczas jego dodatkowe zależności, prawdopodobnie z powodu problemu z oceny makra znajdujących się w niestandardowego kroku kompilacji dla projektu. Ten błąd może również oznaczać, że ścieżka jest nieprawidłowo sformułowany, zawierające znaki lub kombinacje znaków, które nie są dozwolone w ścieżce pliku.

Aby rozwiązać ten problem, napraw makra, lub usuń specyfikację ścieżki. Oceniono ścieżka jest ścieżką bezwzględną z katalogu projektu.