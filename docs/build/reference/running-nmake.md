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
ms.openlocfilehash: dac5e9c1676278d150dd9802697a8ae8959a40e5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823832"
---
# <a name="running-nmake"></a>Uruchomienie NMAKE

## <a name="syntax"></a>Składnia

> **NMAKE** [*opcji* ...] [*makra* ...] [*cele* ...] [**\@**<em>commandfile</em> ...]

## <a name="remarks"></a>Uwagi

Kompilacje NMAKE określony tylko *cele* albo, jeśli nie zostanie określona, pierwszy w pliku reguł programu make. Pierwszy element docelowy pliku reguł programu make może być [pseudotarget](pseudotargets.md) opiera się innych celów. NMAKE używa plików reguł programu make określony za pomocą /F; Jeśli /F nie zostanie określony, zostanie użyta plik pliku reguł programu make w bieżącym katalogu. Jeśli określono nie pliku reguł programu make, używa reguły wnioskowania Tworzenie wiersza polecenia *cele*.

*Commandfile* plik tekstowy (lub pliku odpowiedzi) zawiera dane wejściowe wiersza polecenia. Inne dane wejściowe mogą poprzedzających lub następnych \@ *commandfile*. Ścieżka jest dozwolone. W *commandfile*, podziały wierszy są traktowane jako miejsca do magazynowania. Definicje makr należy ująć w znaki cudzysłowu, gdy miejsca do magazynowania.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

[Opcje NMAKE](nmake-options.md)

[Tools.ini i NMAKE](tools-ini-and-nmake.md)

[Kody zakończenia z NMAKE](exit-codes-from-nmake.md)

## <a name="see-also"></a>Zobacz także

[NMAKE — dokumentacja](nmake-reference.md)
