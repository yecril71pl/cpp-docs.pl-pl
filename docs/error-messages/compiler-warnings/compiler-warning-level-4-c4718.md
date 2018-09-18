---
title: Kompilator ostrzeżenie (poziom 4) C4718 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4718
dev_langs:
- C++
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8736902f4c3a1cfac7313806fde65d1b253716b3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054236"
---
# <a name="compiler-warning-level-4-c4718"></a>Kompilator ostrzeżenie (poziom 4) C4718

"wywołanie funkcji": wywołanie cykliczne nie ma żadnych efektów ubocznych, usuwanie

Funkcja zawiera wywołanie cykliczne, a w przeciwnym razie ma żadnych efektów ubocznych. Wywołanie tej funkcji jest usuwana. Poprawność program nie ma wpływu, ale jest to zachowanie. Natomiast opuszczania wywołanie może spowodować wyjątek przepełnienia stosu środowiska uruchomieniowego, usuwając wywołanie usuwa tę możliwość.