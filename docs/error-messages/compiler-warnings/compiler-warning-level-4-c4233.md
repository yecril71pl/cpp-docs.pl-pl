---
title: Kompilator ostrzeżenie (poziom 4) C4233
ms.date: 10/25/2017
f1_keywords:
- C4233
helpviewer_keywords:
- C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
ms.openlocfilehash: 361e00b7361aab51ea077d7e248503f3654e5e58
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516522"
---
# <a name="compiler-warning-level-4-c4233"></a>Kompilator ostrzeżenie (poziom 4) C4233

> użyto niestandardowego rozszerzenia: "*— słowo kluczowe*" obsługiwane tylko w języku C++, a nie w języku C słowo kluczowe

Kompilator skompilowany kodu źródłowego C, a nie w języku C++ i użyte słowo kluczowe, które jest prawidłowy tylko w języku C++. Kompilator kompiluje pliku źródłowego c, jeśli rozszerzenie nazwy pliku źródłowego jest .c lub używasz [TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md).

To ostrzeżenie zostanie automatycznie podwyższony do błędu. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md). Na przykład aby C4233 do poziomu 4 ostrzeżenie problem, Dodaj ten wiersz do pliku kodu źródłowego:

```cpp
#pragma warning(4:4233)
```
