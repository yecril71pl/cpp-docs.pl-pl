---
title: "Błąd narzędzi konsolidatora LNK1301 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1301
dev_langs: C++
helpviewer_keywords: LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a01d56f0239160a059fb67774916d9d9aa792709
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1301"></a>Błąd narzędzi konsolidatora LNK1301
Znaleziono niezgodny z /LTCG:parameter moduły LTCG clr  
  
 Moduł skompilowany z/CLR i /GL został przekazany do konsolidatora wraz z jedną optymalizacje profilowe z przewodnikiem parametry opcję/LTCG (PGO).  
  
 Optymalizacje profilowe z przewodnikiem nie są obsługiwane dla modułów/CLR.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [/GL (optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md)  
  
-   [/ LTCG (Generowanie łączonych kodów czasowych)](../../build/reference/ltcg-link-time-code-generation.md)  
  
-   [/ CLR (kompilacja języka wspólnego środowiska wykonawczego)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
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