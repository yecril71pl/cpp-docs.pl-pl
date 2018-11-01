---
title: Błąd PRJ0036 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0036
helpviewer_keywords:
- PRJ0036
ms.assetid: ee215cd1-2d66-474d-9a63-b9096f1c4923
ms.openlocfilehash: 9b9232583c464548167e22d0104e0c6098093eab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435285"
---
# <a name="project-build-error-prj0036"></a>Błąd PRJ0036 kompilacji projektu

Właściwość 'Dodatkowe pliki' narzędzia wdrażania Web zawiera niepoprawny wpis.

Właściwość dodatkowe pliki na stronie właściwości sieci Web Deployment zawiera błąd, prawdopodobnie z powodu problemu z oceny makra. Ten błąd może również oznaczać, że ścieżka jest nieprawidłowo sformułowany, zawierające znaki lub kombinacje znaków, które nie są dozwolone w ścieżce pliku.

Aby rozwiązać ten problem, napraw makra, lub usuń specyfikację ścieżki. Oceniono ścieżka jest ścieżką bezwzględną z katalogu projektu.

Ten błąd może również oznaczać, że jeden z plików, do których odwołuje się nie istnieje.