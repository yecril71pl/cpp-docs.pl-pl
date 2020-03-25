---
title: Błąd PRJ0036 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0036
helpviewer_keywords:
- PRJ0036
ms.assetid: ee215cd1-2d66-474d-9a63-b9096f1c4923
ms.openlocfilehash: 67a225f907d06cd240ec2ebef236c0b4e0b849e2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192106"
---
# <a name="project-build-error-prj0036"></a>Błąd PRJ0036 kompilacji projektu

Właściwość "dodatkowe pliki" narzędzia Web Deployment zawierała nieprawidłowy wpis.

Właściwość dodatkowe pliki na stronie właściwości wdrożenia sieci Web zawiera błąd, prawdopodobnie z powodu problemu z oceną makra. Ten błąd może również oznaczać, że ścieżka jest źle sformułowana, zawierającą znaki lub kombinacje znaków, które nie są dozwolone w ścieżce pliku.

Aby rozwiązać ten problem, napraw makro lub Popraw specyfikację ścieżki. Szacowana ścieżka jest ścieżką bezwzględną z katalogu projektu.

Ten błąd może również oznaczać, że jeden z plików, do którego się odwołuje, nie istnieje.
