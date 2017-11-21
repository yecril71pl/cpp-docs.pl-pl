---
title: "C3382 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3382
dev_langs: C++
helpviewer_keywords: C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 782e5c4cc61294dbdaecbd63ff5c6031d387f843
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3382"></a>C3382 błąd kompilatora
"sizeof" nie jest obsługiwany z/CLR: Safe  
  
 Plik wyjściowy z **/CLR: Safe** kompilacji jest plikiem, który jest typu sprawdzalnie bezpieczne i sizeof nie jest obsługiwana, ponieważ wartość zwracaną przez sizeof operator size_t, którego rozmiar może być różna w zależności od systemu operacyjnego.  
  
 Aby uzyskać więcej informacji, zobacz,  
  
-   [sizeof — Operator](../../cpp/sizeof-operator.md)  
  
-   [/ CLR (kompilacja języka wspólnego środowiska wykonawczego)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Typowe problemy przy migracji 64-bitowe języka Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3382.  
  
```  
// C3382.cpp  
// compile with: /clr:safe  
int main() {  
   sizeof( char );   // C3382  
}  
```