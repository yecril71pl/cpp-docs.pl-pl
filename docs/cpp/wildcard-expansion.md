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
ms.openlocfilehash: 1fdea297bb45a06a08bde4f63f90eabef6ddb539
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857180"
---
# <a name="wildcard-expansion"></a>Rozwijanie symbolu wieloznacznego

**Microsoft Specific**

Możesz użyć symboli wieloznacznych — znaku zapytania (?) i gwiazdki (*), aby określić argumenty filename i Path w wierszu polecenia.

Argumenty wiersza polecenia są obsługiwane przez procedurę o nazwie `_setargv` (lub `_wsetargv` w środowisku szerokich znaków), która domyślnie nie rozszerza symboli wieloznacznych na oddzielne ciągi w `argv` tablicy ciągów. Aby uzyskać więcej informacji na temat włączania rozszerzania symboli wieloznacznych, zobacz [rozszerzanie symboli wieloznacznych](../c-language/expanding-wildcard-arguments.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[main: uruchamianie programu](../cpp/main-program-startup.md)