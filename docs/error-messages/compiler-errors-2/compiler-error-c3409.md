---
title: C3409 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C3409
dev_langs:
- C++
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 22b179a74701cb79100285aeb426bb28531730b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3409"></a>C3409 błąd kompilatora
pusty blok atrybutu nie jest dozwolone.  
  
 Nawiasy kwadratowe są interpretowane przez kompilator jako [atrybutu](../../windows/cpp-attributes-reference.md) znaleziono bloku, ale żadne atrybuty.  
  
 Kompilator może wygenerować tego błędu, gdy Użyj nawiasów kwadratowych w definicji wyrażenia lambda. Ten błąd występuje, gdy kompilator nie może określić, czy nawiasy kwadratowe są częścią definicji wyrażenia lambda lub bloku atrybutu. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda](../../cpp/lambda-expressions-in-cpp.md).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Jeśli nawiasy kwadratowe są częścią blok atrybutu:  
  
    1.  Podaj jeden lub więcej atrybutów w bloku attribute.  
  
    2.  Usuń blok atrybutu.  
  
2.  Jeśli nawiasy kwadratowe są częścią wyrażenia lambda:  
  
    1.  Upewnij się, że wyrażenie lambda postępuje prawidłowej składni reguł.  
  
         Aby uzyskać więcej informacji na temat składni wyrażenia lambda, zobacz [składnia wyrażenia Lambda](../../cpp/lambda-expression-syntax.md).  
  
    2.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3409.  
  
```  
// C3409.cpp  
// compile with: /c  
#include <windows.h>  
[]   // C3409  
class a {};  
  
// OK  
[object, uuid("00000000-0000-0000-0000-000000000000")]  
__interface x {};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000001")]  
class b : public x {};  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3409, ponieważ korzysta z wyrażenia lambda `mutable` specyfikacji, ale nie ma listy parametrów. Kompilator nie może określić, czy nawiasy kwadratowe są częścią definicji wyrażenia lambda lub bloku atrybutu.  
  
```  
// C3409b.cpp  
  
int main()  
{  
   [] mutable {}();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [atrybut](../../windows/cpp-attributes-reference.md)   
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)   
 [Składnia wyrażenia lambda](../../cpp/lambda-expression-syntax.md)