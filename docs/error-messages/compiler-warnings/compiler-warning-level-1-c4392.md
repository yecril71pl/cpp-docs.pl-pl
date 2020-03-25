---
title: Ostrzeżenie kompilatora (poziom 1) C4392
ms.date: 11/04/2016
f1_keywords:
- C4392
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
ms.openlocfilehash: a62bfdb6b9b29abf047e7690179978cb9516d477
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186884"
---
# <a name="compiler-warning-level-1-c4392"></a>Ostrzeżenie kompilatora (poziom 1) C4392

"Signature": niepoprawna liczba argumentów dla wewnętrznej funkcji, oczekiwano argumentów "number"

Deklaracja funkcji dla wewnętrznego kompilatora miała nieprawidłową liczbę argumentów. Obraz z wynikiem może nie działać poprawnie.

Aby usunąć to ostrzeżenie, Popraw deklarację lub Usuń deklarację i po prostu #include odpowiedni plik nagłówkowy.

Poniższy przykład generuje C4392:

```cpp
// C4392.cpp
// compile with: /W1
// processor: x86
// uncomment the following line and delete the line that
// generated the warning to resolve
// #include "xmmintrin.h"

#ifdef  __cplusplus
extern "C" {
#endif

extern void _mm_stream_pd(double *dp);   // C4392

#ifdef  __cplusplus
}
#endif

int main()
{
}
```
