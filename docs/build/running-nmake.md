---
title: Uruchomienie NMAKE
ms.date: 09/05/2018
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
ms.openlocfilehash: 81f38792893955b476dfc7eda91ed00603924a8f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646215"
---
# <a name="running-nmake"></a>Uruchomienie NMAKE

## <a name="syntax"></a>Składnia

> **NMAKE** [*opcji* ...] [*makra* ...] [*cele* ...] [**\@**<em>commandfile</em> ...]

## <a name="remarks"></a>Uwagi

Kompilacje NMAKE określony tylko *cele* albo, jeśli nie zostanie określona, pierwszy w pliku reguł programu make. Pierwszy element docelowy pliku reguł programu make może być [pseudotarget](../build/pseudotargets.md) opiera się innych celów. NMAKE używa plików reguł programu make określony za pomocą /F; Jeśli /F nie zostanie określony, zostanie użyta plik pliku reguł programu make w bieżącym katalogu. Jeśli określono nie pliku reguł programu make, używa reguły wnioskowania Tworzenie wiersza polecenia *cele*.

*Commandfile* plik tekstowy (lub pliku odpowiedzi) zawiera dane wejściowe wiersza polecenia. Inne dane wejściowe mogą poprzedzających lub następnych \@ *commandfile*. Ścieżka jest dozwolone. W *commandfile*, podziały wierszy są traktowane jako miejsca do magazynowania. Definicje makr należy ująć w znaki cudzysłowu, gdy miejsca do magazynowania.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

[Opcje NMAKE](../build/nmake-options.md)

[Tools.ini i NMAKE](../build/tools-ini-and-nmake.md)

[Kody zakończenia z NMAKE](../build/exit-codes-from-nmake.md)

## <a name="see-also"></a>Zobacz też

[NMAKE — dokumentacja](../build/nmake-reference.md)