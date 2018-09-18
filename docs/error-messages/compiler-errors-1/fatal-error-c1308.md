---
title: Błąd krytyczny C1308 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1308
dev_langs:
- C++
helpviewer_keywords:
- C1308
ms.assetid: 46177997-069e-433a-8e20-93c846d78ffd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd778e95f3ace413dbeb409da3c4b2493208e8bf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104189"
---
# <a name="fatal-error-c1308"></a>Błąd krytyczny C1308

Łączenie zestawów nie jest obsługiwana.

.Netmodule jest dozwolona jako dane wejściowe do konsolidatora, ale zestaw nie jest. Ten błąd może zostać wygenerowany, gdy podejmowana jest próba połączyć zestawu skompilowanego z `/clr:safe`.

Aby uzyskać więcej informacji, zobacz [pliki .netmodule — wejście konsolidatora](../../build/reference/netmodule-files-as-linker-input.md).

Poniższy przykład spowoduje wygenerowanie C1308:

```
// C1308.cpp
// compile with: /clr:safe /LD
public ref class MyClass {
public:
   int i;
};
```

Następnie wyszukaj maszynę

```
// C1308b.cpp
// compile with: /clr /link C1308b.obj C1308.dll
// C1308 expected
#using "C1308.dll"
int main() {
   MyClass ^ my = gcnew MyClass();
}
```