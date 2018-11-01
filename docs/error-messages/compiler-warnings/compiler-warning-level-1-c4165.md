---
title: Kompilator ostrzeżenie (poziom 1) C4165
ms.date: 11/04/2016
f1_keywords:
- C4165
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
ms.openlocfilehash: 4d6377730e262efafb38f5e714989e9075a77a04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534384"
---
# <a name="compiler-warning-level-1-c4165"></a>Kompilator ostrzeżenie (poziom 1) C4165

"HRESULT" jest konwertowana na "bool"; Czy na pewno jest to, co chcesz zrobić?

Korzystając z wartości HRESULT w [Jeśli](../../cpp/if-else-statement-cpp.md) instrukcji, HRESULT zostaną przekonwertowane na [bool](../../cpp/bool-cpp.md) , chyba że jawnie testu dla zmiennej jako wartość HRESULT. To ostrzeżenie jest domyślnie wyłączona.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4165

```cpp
// C4165.cpp
// compile with: /W1
#include <windows.h>
#pragma warning(1:4165)

extern HRESULT hr;
int main() {
   if (hr) {
   // try either of the following ...
   // if (FAILED(hr)) { // C4165 expected
   // if (hr != S_OK) {
   }
}
```