---
title: Kompilator ostrzeżenie (poziom 1) C4951
ms.date: 08/27/2018
f1_keywords:
- C4951
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
ms.openlocfilehash: 73e048aeaa044c35e09539b07d51398829a0fdfd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617870"
---
# <a name="compiler-warning-level-1-c4951"></a>Kompilator ostrzeżenie (poziom 1) C4951

> "*funkcja*" został wyedytowany od profilu dane zostały zebrane, nieużywane dane profilu funkcji

Funkcja został zmodyfikowany w danych wejściowych modułu [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), dzięki czemu dane profilu są obecnie nieprawidłowe. Moduł wejściowy został ponownie kompilowana po **pginstrument** i ma funkcję (*funkcja*) przy użyciu różnych przepływu sterowania niż w module w momencie **pginstrument**  operacji.

To ostrzeżenie ma charakter informacyjny. Aby rozwiązać tego ostrzeżenia, należy uruchomić **pginstrument**, powtórz wszystkie testu działa, a następnie uruchom **/LTCG:PGOPTIMIZE**.

To ostrzeżenie zostanie zamienione błąd Jeśli **/LTCG:PGOPTIMIZE** została użyta.