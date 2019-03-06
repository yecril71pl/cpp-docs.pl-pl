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
ms.openlocfilehash: 1d3555dc66ba9939ce346a692df9d0151fcf87d2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423082"
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

## <a name="see-also"></a>Zobacz także

[NMAKE — dokumentacja](../build/nmake-reference.md)
