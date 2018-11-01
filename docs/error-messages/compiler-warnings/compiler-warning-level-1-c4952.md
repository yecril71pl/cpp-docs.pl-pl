---
title: Kompilator ostrzeżenie (poziom 1) C4952
ms.date: 08/27/2018
f1_keywords:
- C4952
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
ms.openlocfilehash: c2e9b88125655d9ea0abe3e65500b149289ba83b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537582"
---
# <a name="compiler-warning-level-1-c4952"></a>Kompilator ostrzeżenie (poziom 1) C4952

> "*funkcja*": nie znaleziono danych profilowych w bazie danych programu "*pgd_file*"

Korzystając z [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilator wykrył moduł wejściowy nie kompilowanej po `/LTCG:PGINSTRUMENT` i ma nową funkcję (*funkcja*) istnieje.

To ostrzeżenie ma charakter informacyjny. Aby rozwiązać tego ostrzeżenia, należy uruchomić `/LTCG:PGINSTRUMENT`, powtórz wszystkie testu działa, a następnie uruchom `/LTCG:PGOPTIMIZE`.

To ostrzeżenie zostanie zamienione błąd Jeśli `/LTCG:PGOPTIMIZE` została użyta.