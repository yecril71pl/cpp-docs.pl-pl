---
title: C3382 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3382
dev_langs:
- C++
helpviewer_keywords:
- C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8bcca58aecc3d5a5e7b621f45e102690c9f138c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254540"
---
# <a name="compiler-error-c3382"></a>C3382 błąd kompilatora
"sizeof" nie jest obsługiwany z/CLR: Safe  
  
 Plik wyjściowy z **/CLR: Safe** kompilacji jest plikiem, który jest typu sprawdzalnie bezpieczne i sizeof nie jest obsługiwana, ponieważ wartość zwracaną przez sizeof operator size_t, którego rozmiar może być różna w zależności od systemu operacyjnego.  
  
 Aby uzyskać więcej informacji, zobacz,  
  
-   [sizeof, operator](../../cpp/sizeof-operator.md)  
  
-   [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Typowe problemy przy migracji Visual C++ w wersji 64-bitowej](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3382.  
  
```  
// C3382.cpp  
// compile with: /clr:safe  
int main() {  
   sizeof( char );   // C3382  
}  
```