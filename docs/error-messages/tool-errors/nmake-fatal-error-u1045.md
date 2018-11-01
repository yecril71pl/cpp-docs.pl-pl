---
title: Błąd krytyczny NMAKE U1045
ms.date: 11/04/2016
f1_keywords:
- U1045
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
ms.openlocfilehash: bb1dfac36eda263e656ca85fb1f5b74babfd2e2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607967"
---
# <a name="nmake-fatal-error-u1045"></a>Błąd krytyczny NMAKE U1045

zduplikowanie nie powiodło się: komunikat

Polecenie wywoływane przez NMAKE lub program nie powiodło się z powodu danego. Kiedy NMAKE wywołuje inny program — na przykład, kompilator lub konsolidator — wywołanie może zakończyć się niepowodzeniem i błędem mogą być zwrócone przez program o nazwie. Ten komunikat jest używana do zgłaszania błędu.

Aby rozwiązać ten problem, należy najpierw określić przyczynę błędu. Można użyć poleceń zgłoszone przez NMAKE [/N](../../build/nmake-options.md) opcję, aby sprawdzić ustawienia środowiska i powtórz czynności wykonywane przez NMAKE w wierszu polecenia.