---
title: Błąd narzędzi konsolidatora LNK1301
ms.date: 11/04/2016
f1_keywords:
- LNK1301
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
ms.openlocfilehash: fe64eecfbc9fed57c3748afd5804b76d6e4284a4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990939"
---
# <a name="linker-tools-error-lnk1301"></a>Błąd narzędzi konsolidatora LNK1301

Znaleziono moduły CLR LTCG, niezgodne z/LTCG: Parameter

Moduł skompilowany z/CLR i/GL został przekierowany do konsolidatora wraz z jednym z parametrów profilowanych optymalizacji (PGO)/LTCG.

Profilowana Optymalizacja nie jest obsługiwana w przypadku modułów/CLR.

Aby uzyskać więcej informacji, zobacz:

- [/GL (Optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (Generowanie łączonych kodów czasowych)](../../build/reference/ltcg-link-time-code-generation.md)

- [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Optymalizacje sterowane profilem](../../build/profile-guided-optimizations.md)

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Nie Kompiluj z opcją/CLR lub nie łącz z jednym z parametrów PGO na/LTCG.

## <a name="example"></a>Przykład

Poniższy przykład generuje LNK1301:

```cpp
// LNK1301.cpp
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj
// LNK1301 expected
class MyClass {
public:
   int i;
};
```
