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
ms.openlocfilehash: 0b4e298ad3815c741ff6c901ac39bf7838ed135d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299708"
---
# <a name="linker-tools-error-lnk1301"></a>Błąd narzędzi konsolidatora LNK1301
Znaleziono niezgodny z /LTCG:parameter moduły LTCG clr  
  
 Moduł skompilowany z/CLR i /GL został przekazany do konsolidatora wraz z jedną optymalizacje profilowe z przewodnikiem parametry opcję/LTCG (PGO).  
  
 Optymalizacje profilowe z przewodnikiem nie są obsługiwane dla modułów/CLR.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [/GL (Optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md)  
  
-   [/LTCG (Generowanie łączonych kodów czasowych)](../../build/reference/ltcg-link-time-code-generation.md)  
  
-   [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Optymalizacje sterowane profilem](../../build/reference/profile-guided-optimizations.md)  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Kompiluje z/CLR lub nie są połączone z jednym z parametrów PGO opcję/LTCG.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje LNK1301:  
  
```  
// LNK1301.cpp  
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj  
// LNK1301 expected  
class MyClass {  
public:  
   int i;  
};  
```