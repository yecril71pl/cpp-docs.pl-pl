---
title: Błąd narzędzi konsolidatora LNK1301 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1301
dev_langs:
- C++
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8646de5bb81120f6445e16b819b27da62ed9d5ec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039949"
---
# <a name="linker-tools-error-lnk1301"></a>Błąd narzędzi konsolidatora LNK1301

Znaleziono niezgodne z /LTCG:parameter moduły LTCG clr

Moduł skompilowany z/CLR i /GL został przekazany do konsolidatora razem z jedną optymalizacje profilowe z przewodnikiem parametrów (PGO) opcję/LTCG.

Optymalizacje profilowe z przewodnikiem nie są obsługiwane dla modułów/CLR.

Aby uzyskać więcej informacji, zobacz:

- [/GL (Optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (Generowanie łączonych kodów czasowych)](../../build/reference/ltcg-link-time-code-generation.md)

- [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Optymalizacje sterowane profilem](../../build/reference/profile-guided-optimizations.md)

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