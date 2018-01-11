---
title: "Kompilatora (poziom 1) ostrzeżenie C4835 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4835
dev_langs: C++
helpviewer_keywords: C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 92e2d17ada58773a34d8c2d14424dd88e74a06d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4835"></a>Kompilator C4835 ostrzegawcze (poziom 1)
"Zmienna": Inicjator dla eksportowanych danych nie zostaną uruchomione, dopóki kod zarządzany jest wykonywany jako pierwszy w zestawie hosta  
  
 Podczas uzyskiwania dostępu do danych między składników zarządzanych, zaleca się nie Użyj natywnego języka C++ importu i eksportu mechanizmów. Zamiast tego należy zadeklarować członkowie danych wewnątrz typu zarządzanego i odwołania do metadanych z `#using` na komputerze klienckim. Aby uzyskać więcej informacji, zobacz [# dyrektywa using](../../preprocessor/hash-using-directive-cpp.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4835.  
  
```  
// C4835.cpp  
// compile with: /W1 /clr /LD  
int f() { return 1; }  
int n = 9;  
  
__declspec(dllexport) int m = f();   // C4835  
__declspec(dllexport) int *p = &n;   // C4835  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykorzystuje składnik wbudowane poprzedni przykład, pokazujący, że wartość zmiennych jest niezgodne z oczekiwaniami.  
  
```  
// C4835_b.cpp  
// compile with: /clr C4835.lib  
#include <stdio.h>  
__declspec(dllimport) int m;  
__declspec(dllimport) int *p;  
  
int main() {  
   printf("%d\n", m);  
   printf("%d\n", p);  
}  
```  
  
```Output  
0  
268456008  
```