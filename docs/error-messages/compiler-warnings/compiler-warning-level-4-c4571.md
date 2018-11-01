---
title: Kompilator ostrzeżenie (poziom 4) C4571
ms.date: 11/04/2016
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 92164bf297a44871897b6c6150eb54f8c5ccf3cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431060"
---
# <a name="compiler-warning-level-4-c4571"></a>Kompilator ostrzeżenie (poziom 4) C4571

Informacja: semantyka instrukcji catch(...) została zmieniona od czasu Visual C++ 7.1; Wyjątki strukturalne (SEH) nie są już przechwytywane

C4571 jest generowany dla każdego bloku catch(...) podczas kompilowania za pomocą **/EHS**.

Podczas kompilowania za pomocą **/EHS**, blok catch(...) nie będzie przechwytywać wyjątków strukturalnych (dzielenie przez zero, pustym wskaźnikiem, na przykład); catch(...) bloku będzie tylko bloku catch jawnie zgłoszony, wyjątki C++.  Aby uzyskać więcej informacji, zobacz [wyjątków](../../cpp/exception-handling-in-visual-cpp.md).

To ostrzeżenie jest domyślnie wyłączona.  Włącz to ostrzeżenie, w celu zapewnienia, że podczas kompilowania z **/EHS** swoje bloków catch (...) nie zamierzasz przechwycić wyjątki strukturalne.  Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

W jednym z następujących metod można rozwiązać C4571

- Kompiluj przy użyciu **/eha** Jeśli nadal chcesz bloki swoje catch(...) w taki sposób, aby przechwytywać wyjątki strukturalne.

- Nie należy włączać C4571, jeśli nie chcesz, aby Twoje bloki catch(...), aby przechwytywać wyjątki strukturalne, ale chcesz nadal używać catch(...) bloków.  Nadal może przechwycić wyjątków strukturalnych za pomocą słów kluczowych obsługi wyjątków strukturalnych (**__try**, **__except**, i **__finally**).  Jednak należy pamiętać, że podczas kompilowania **/EHS** destruktory tylko zostanie wywołana, gdy zgłoszony wyjątek języka C++, nie w przypadku, gdy wystąpi wyjątek SEH.

- Zastąp blok catch(...) przy użyciu bloków catch dla określonych wyjątków C++ i opcjonalnie Dodaj obsługi wokół obsługi wyjątków C++ wyjątków strukturalnych (**__try**, **__except**, i **_ _finally**).  Zobacz [obsługi wyjątków strukturalnych, (C/C++)](../../cpp/structured-exception-handling-c-cpp.md) Aby uzyskać więcej informacji.

Zobacz [/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4571.

```
// C4571.cpp
// compile with: /EHs /W4 /c
#pragma warning(default : 4571)
int main() {
   try {
      int i = 0, j = 1;
      j /= i;   // this will throw a SE (divide by zero)
   }
   catch(...) {}   // C4571 warning
}
```