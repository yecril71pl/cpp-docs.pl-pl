---
title: Kompilator ostrzeżenie (poziom 1) C4965 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4965
dev_langs:
- C++
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8613585d1f34060fb2e60f976f76c6801005aca
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036647"
---
# <a name="compiler-warning-level-1-c4965"></a>Kompilator ostrzeżenie (poziom 1) C4965

niejawne rzutowanie liczby całkowitej 0; Użyj nullptr lub jawnego rzutowania

Visual C++ funkcje niejawna konwersja boxing typów wartości. Instrukcji, która spowodowała przypisanie wartości null, przy użyciu zarządzanych rozszerzeń języka C++ teraz staje się przypisania do spakowanej int.

Aby uzyskać więcej informacji, zobacz [pakowania](../../windows/boxing-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4965.

```
// C4965.cpp
// compile with: /clr /W1
int main() {
   System::Object ^o = 0;   // C4965

   // the previous line is the same as the following line
   // using Managed Extensions for C++
   // System::Object *o = __box(0);

   // OK
   System::Object ^o2 = nullptr;
   System::Object ^o3 = safe_cast<System::Object^>(0);
}
```