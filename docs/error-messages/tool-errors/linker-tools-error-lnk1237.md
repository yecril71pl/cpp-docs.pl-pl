---
title: Błąd narzędzi konsolidatora LNK1237
ms.date: 11/04/2016
f1_keywords:
- LNK1237
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
ms.openlocfilehash: ae1a397cdcc10cd89fd046a94e78c15dd46dceed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242534"
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