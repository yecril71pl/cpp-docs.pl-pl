---
title: Błąd PRJ0031 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0031
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
ms.openlocfilehash: e5edae0c1b7464e4a3a5e9523332ce956d0dcf92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648594"
---
# <a name="project-build-error-prj0031"></a>Błąd PRJ0031 kompilacji projektu

Właściwość 'Wyniki' dla kroku kompilacji niestandardowej krok dla pliku 'Plik' zawiera 'makra"co ewaluowane jest"macro_expansion".

Niestandardowego kroku kompilacji dla pliku miał złe dane wyjściowe, prawdopodobnie z powodu problemu z oceny makra. Ten błąd może również oznaczać, że ścieżka jest nieprawidłowo sformułowany, zawierające znaki lub kombinacje znaków, które nie są dozwolone w ścieżce pliku.

Aby rozwiązać ten problem, napraw makra, lub usuń specyfikację ścieżki. Oceniono ścieżka jest ścieżką bezwzględną z katalogu projektu.