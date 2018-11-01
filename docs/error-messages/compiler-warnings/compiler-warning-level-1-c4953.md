---
title: Kompilator ostrzeżenie (poziom 1) C4953
ms.date: 08/27/2018
f1_keywords:
- C4953
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
ms.openlocfilehash: 1948342e1ff97c38ca3a44694dc7e7d399d96825
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568052"
---
# <a name="compiler-warning-level-1-c4953"></a>Kompilator ostrzeżenie (poziom 1) C4953

> Wbudowany "*funkcja*" został wyedytowany od profilu dane zostały zebrane, dane profilu nieużywane

Korzystając z [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilator wykrył moduł wejściowy nie kompilowanej po `/LTCG:PGINSTRUMENT` i ma funkcję (*funkcja*), był edytowany i którym wskazany działa istniejącego testu pełnią kandydatem do wbudowanie. Jednak w wyniku o konieczności ponownego kompilowania modułu, funkcja nie będzie już kandydatem do wbudowanie.

To ostrzeżenie ma charakter informacyjny. Aby rozwiązać tego ostrzeżenia, należy uruchomić `/LTCG:PGINSTRUMENT`, powtórz wszystkie testu działa, a następnie uruchom `/LTCG:PGOPTIMIZE`.

To ostrzeżenie zostanie zamienione błąd Jeśli `/LTCG:PGOPTIMIZE` została użyta.