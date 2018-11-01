---
title: Błąd kompilatora C3893
ms.date: 11/04/2016
f1_keywords:
- C3893
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
ms.openlocfilehash: 45a140d3fd5f510ee2434950ca3c4b47c0756d75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447237"
---
# <a name="compiler-error-c3893"></a>Błąd kompilatora C3893

"var": wykorzystanie wartości l składowej danych initonly jest dozwolone tylko w konstruktorze wystąpienia klasy "type_name"

Statyczne [initonly](../../dotnet/initonly-cpp-cli.md) elementy członkowskie danych może mieć tylko adresu pobranego w konstruktorze statycznym.

Składowe danych initonly (niestatycznych) wystąpienie może mieć tylko adresu pobranego w konstruktory wystąpień (niestatycznych).

Poniższy przykład spowoduje wygenerowanie C3893:

```
// C3893.cpp
// compile with: /clr
ref struct Y1 {
   Y1() : data_var(0) {
      int% i = data_var;   // OK
   }
   initonly int data_var;
};

int main(){
   Y1^ y= gcnew Y1;
   int% i = y->data_var;   // C3893
}
```