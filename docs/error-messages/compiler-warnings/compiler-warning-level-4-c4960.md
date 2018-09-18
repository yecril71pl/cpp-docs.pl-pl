---
title: Kompilator ostrzeżenie (poziom 4) C4960 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4960
dev_langs:
- C++
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed6ba083017c84cd6af05b917ff8417b0394d7c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085722"
---
# <a name="compiler-warning-level-4-c4960"></a>Kompilator ostrzeżenie (poziom 4) C4960

'Funkcja' jest zbyt duży do profilowania

Korzystając z [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), kompilator wykrył moduł danych wejściowych przy użyciu funkcji, które są większe niż 65 535 instrukcje. Duże funkcja nie jest dostępna dla optymalizacje sterowane profilem.

Aby rozwiązać tego ostrzeżenia, należy zmniejszyć rozmiar funkcji.