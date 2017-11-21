---
title: "Kompilatora (poziom 1) ostrzeżenie C4742 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4742
dev_langs: C++
helpviewer_keywords: C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 934c7d14d95d0b90cfdcdb694f743e6b13abd0e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4742"></a>Kompilator C4742 ostrzegawcze (poziom 1)
"var" ma inne wyrównanie w 'plik1' i 'plik2': numer i  
  
 Zmienną zewnętrznego, który odwołuje się do lub zdefiniowane w dwóch plikach ma inne wyrównanie w tych plików. To ostrzeżenie jest emitowany, gdy kompilator stwierdzi, że `__alignof` dla zmiennej w *file1* różni się od `__alignof` dla zmiennej w *plik2*. Może to być spowodowane przy użyciu niezgodne typy przy deklarowaniu zmiennej w różnych plików lub przy użyciu niezgodny `#pragma pack` w różnych plikach.  
  
 Aby usunąć to ostrzeżenie, użyj tej samej definicji typu lub użyj innej nazwy zmiennych.  
  
 Aby uzyskać więcej informacji, zobacz [pakietu](../../preprocessor/pack.md) i [__alignof Operator](../../cpp/alignof-operator.md).  
  
## <a name="example"></a>Przykład  
 Jest to pierwszy plik, który definiuje typ.  
  
```  
// C4742a.c  
// compile with: /c  
struct X {  
   char x, y, z, w;  
} global;  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4742.  
  
```  
// C4742b.c  
// compile with: C4742a.c /W1 /GL  
// C4742 expected  
extern struct X {  
   int a;  
} global;  
  
int main() {  
   global.a = 0;  
}  
```