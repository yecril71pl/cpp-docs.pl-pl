---
title: Błąd narzędzi konsolidatora LNK1237 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1237
dev_langs:
- C++
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9ada38fcf3a706f7852f49f60f677fb5dc10d7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065299"
---
# <a name="linker-tools-error-lnk1237"></a>Błąd narzędzi konsolidatora LNK1237

podczas generowania kodu kompilator wprowadził odwołanie do symbolu "symbol" zdefiniowanego w module "module" skompilowanym z opcją /GL

Podczas generowania kodu kompilator nie powinna wprowadzać symbole, które później są rozwiązywane do definicji skompilowany **/GL**. `symbol` to symbol, które zostały wprowadzone, a następnie później rozwiązany do definicji, który został skompilowany przy użyciu **/GL**.

Aby uzyskać więcej informacji, zobacz [/GL (Optymalizacja Całoprogramowa)](../../build/reference/gl-whole-program-optimization.md).

Aby rozwiązać LNK1237, nie można skompilować symbol za pomocą **/GL** lub użyj [/include (Wymuszaj odwołania do symboli)](../../build/reference/include-force-symbol-references.md) wymuszenie odwołania do symbolu.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie LNK1237. Aby rozwiązać ten problem, nie inicjowania tablicy LNK1237_a.cpp i dodawania **/ include: __chkstk** polecenia łącza.

```
// LNK1237_a.cpp
int main() {
   char c[5000] = {0};
}
```

```
// LNK1237_b.cpp
// compile with: /GS- /GL /c LNK1237_a.cpp
// processor: x86
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)
extern "C" void _chkstk(size_t s) {}
```