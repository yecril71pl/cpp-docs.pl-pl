---
title: Błąd narzędzi konsolidatora LNK1237
ms.date: 11/04/2016
f1_keywords:
- LNK1237
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
ms.openlocfilehash: c56b2eb86c7605fb3330d7b1bb01e3235466ede6
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990961"
---
# <a name="linker-tools-error-lnk1237"></a>Błąd narzędzi konsolidatora LNK1237

podczas generowania kodu kompilator wprowadził odwołanie do symbolu "symbol" zdefiniowanego w module "module" skompilowanego za pomocą/GL

Podczas generowania kodu kompilator nie powinien wprowadzać symboli, które są później rozpoznawane jako definicje skompilowane **/GL**. `symbol` jest symbolem, który został wprowadzony i później rozpoznany jako definicja skompilowana z **/GL**.

Aby uzyskać więcej informacji, zobacz [/GL (Optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md).

Aby rozwiązać LNK1237, nie Kompiluj symbolu z **/GL** lub Użyj [/include (Wymuszaj odwołania do symboli)](../../build/reference/include-force-symbol-references.md) , aby wymusić odwołanie do symbolu.

## <a name="example"></a>Przykład

Poniższy przykład generuje LNK1237. Aby rozwiązać ten problem, nie należy inicjować tablicy w LNK1237_a. cpp i dodać **/include: __chkstk** do polecenia link.

```cpp
// LNK1237_a.cpp
int main() {
   char c[5000] = {0};
}
```

```cpp
// LNK1237_b.cpp
// compile with: /GS- /GL /c LNK1237_a.cpp
// processor: x86
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)
extern "C" void _chkstk(size_t s) {}
```
