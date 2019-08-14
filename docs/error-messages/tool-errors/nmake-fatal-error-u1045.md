---
title: Błąd krytyczny NMAKE U1045
ms.date: 08/11/2019
f1_keywords:
- U1045
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
ms.openlocfilehash: bdc28bcf02aea791a346a0a74915707fef551b8b
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980543"
---
# <a name="nmake-fatal-error-u1045"></a>Błąd krytyczny NMAKE U1045

> Niepowodzenie duplikowania: *komunikat*

Program lub polecenie wywoływane przez NMAKE nie powiodło się zpowodu przyczyny w komunikacie. Gdy NMAKE wywołuje inny program, na przykład kompilator lub konsolidator, wywołanie może zakończyć się niepowodzeniem. Lub błąd może zostać zwrócony przez wywołany program. Ten komunikat służy do zgłaszania błędu.

Aby rozwiązać ten problem, należy najpierw określić przyczynę błędu. Możesz użyć poleceń zgłoszonych przez opcję NMAKE [/n](../../build/reference/running-nmake.md#nmake-options) , aby sprawdzić ustawienia środowiska i powtórzyć akcje wykonywane przez NMAKE w wierszu polecenia.
