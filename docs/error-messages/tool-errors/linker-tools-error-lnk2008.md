---
title: Błąd narzędzi konsolidatora LNK2008
ms.date: 11/04/2016
f1_keywords:
- LNK2008
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
ms.openlocfilehash: c7794d09f7eeb9dceba7098ca7af90ccf2eeccad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194827"
---
# <a name="linker-tools-error-lnk2008"></a>Błąd narzędzi konsolidatora LNK2008

Cel naprawy nie jest wyrównany "symbol_name"

LINK znalazł miejsce docelowe naprawy w pliku obiektu, które nie zostało prawidłowo wyrównane.

Przyczyną tego błędu może być niestandardowe wyrównanie secton (na przykład [pack](../../preprocessor/pack.md)#pragma), [wyrównanie](../../cpp/align-cpp.md) modyfikatora lub użycie kodu języka asemblera modyfikującego secton wyrównania.

Jeśli kod nie używa żadnego z powyższych, może to być spowodowane kompilatorem.
