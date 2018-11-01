---
title: Kompilator ostrzeżenie (poziom 4) C4960
ms.date: 11/04/2016
f1_keywords:
- C4960
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
ms.openlocfilehash: ff4a9b3d78a108a45abb18c22049b104e630bf15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516366"
---
# <a name="compiler-warning-level-4-c4960"></a>Kompilator ostrzeżenie (poziom 4) C4960

'Funkcja' jest zbyt duży do profilowania

Korzystając z [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), kompilator wykrył moduł danych wejściowych przy użyciu funkcji, które są większe niż 65 535 instrukcje. Duże funkcja nie jest dostępna dla optymalizacje sterowane profilem.

Aby rozwiązać tego ostrzeżenia, należy zmniejszyć rozmiar funkcji.