---
title: Kompilator ostrzeżenie (poziom 1) C4729 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4729
dev_langs:
- C++
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d1f5b4fe452937ce74e56886a5214ff92f44af7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096083"
---
# <a name="compiler-warning-level-1-c4729"></a>Kompilator ostrzeżenie (poziom 1) C4729

Funkcja za duża dla grafu przepływu na podstawie ostrzeżenia

To ostrzeżenie jest generowane, gdy funkcja jest zbyt duży, aby być skompilowana przy użyciu niezawodnych sprawdzanie w sytuacjach, generujących ostrzeżenia. To ostrzeżenie jest tylko wygenerowany, gdy [/Od](../../build/reference/od-disable-debug.md) — opcja kompilatora używane.

Aby rozwiązać tego ostrzeżenia, Podziel funkcji na mniejsze.