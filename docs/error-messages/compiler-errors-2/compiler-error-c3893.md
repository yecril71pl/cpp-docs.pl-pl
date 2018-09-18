---
title: Błąd kompilatora C3893 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3893
dev_langs:
- C++
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 857d13de61f03bf0784d8cd10ad092d16f7acdaa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087050"
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