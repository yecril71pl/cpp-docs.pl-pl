---
title: Błąd narzędzi konsolidatora LNK1301
ms.date: 11/04/2016
f1_keywords:
- LNK1301
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
ms.openlocfilehash: 6a82d7756f1460c56d87a3d7b1360c140de19827
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812099"
---
# <a name="linker-tools-error-lnk1301"></a>Błąd narzędzi konsolidatora LNK1301

Znaleziono niezgodne z /LTCG:parameter moduły LTCG clr

Moduł skompilowany z/CLR i /GL został przekazany do konsolidatora razem z jedną optymalizacje profilowe z przewodnikiem parametrów (PGO) opcję/LTCG.

Optymalizacje profilowe z przewodnikiem nie są obsługiwane dla modułów/CLR.

Aby uzyskać więcej informacji, zobacz:

- [/GL (Optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (Generowanie łączonych kodów czasowych)](../../build/reference/ltcg-link-time-code-generation.md)

- [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Optymalizacje sterowane profilem](../../build/profile-guided-optimizations.md)

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Nie można skompilować z/CLR lub nie należy przeprowadzać konsolidacji z jednego z parametrów funkcji optymalizacji PGO do opcję/LTCG.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie LNK1301:

```
// LNK1301.cpp
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj
// LNK1301 expected
class MyClass {
public:
   int i;
};
```