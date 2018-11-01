---
title: Rozwijanie symbolu wieloznacznego
ms.date: 11/04/2016
f1_keywords:
- _setargv
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
ms.openlocfilehash: 2d495f94f2e3fb7b88d235edc7b98f8e90775393
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507439"
---
# <a name="wildcard-expansion"></a>Rozwijanie symbolu wieloznacznego

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

Można używać symboli wieloznacznych — znak zapytania (?) i gwiazdki (*), aby określić nazwę pliku i ścieżkę argumenty w wierszu polecenia.

Argumenty wiersza polecenia są obsługiwane przez procedurę o nazwie `_setargv` (lub `_wsetargv` w środowisku znaków dwubajtowych), które domyślnie nie jest powiększony, symboli wieloznacznych do oddzielnych ciągów w `argv` tablicy ciągów. Aby uzyskać więcej informacji na temat włączania rozszerzenia symboli wieloznacznych, zobacz [rozszerzanie argumentów z symbolami wieloznacznymi](../c-language/expanding-wildcard-arguments.md).

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[main: uruchamianie programu](../cpp/main-program-startup.md)