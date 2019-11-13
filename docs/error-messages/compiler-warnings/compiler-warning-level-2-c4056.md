---
title: Ostrzeżenie kompilatora (poziom 2) C4056
ms.date: 11/04/2016
f1_keywords:
- C4056
helpviewer_keywords:
- C4056
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
ms.openlocfilehash: 20e7c2693c14c0ea05cc6f07f8dad4ce76c1ef5e
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052193"
---
# <a name="compiler-warning-level-2-c4056"></a>Ostrzeżenie kompilatora (poziom 2) C4056

przepełnienie w zmiennoprzecinkowej stałej arytmetycznej

Stała zmiennoprzecinkowa arytmetyczna generuje wynik, który przekracza maksymalną dozwoloną wartość.

To ostrzeżenie może być spowodowane optymalizacją kompilatora wykonywaną podczas arytmetycznej stałej. Możesz bezpiecznie zignorować to ostrzeżenie, Jeśli wyłączysz opcję Optymalizacja ([/od](../../build/reference/od-disable-debug.md)).

Poniższy przykład generuje C4056:

```cpp
// C4056.cpp
// compile with: /W2 /LD
#pragma warning (default : 4056)
float fp_val = 1.0e300 * 1.0e300;   // C4056
```