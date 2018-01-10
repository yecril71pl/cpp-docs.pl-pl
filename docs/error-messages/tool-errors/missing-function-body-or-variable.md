---
title: "Brak treść funkcji lub zmienna | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 356d0f0a71feccee953a0b1bd7dc54bc64a0e233
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="missing-function-body-or-variable"></a>Brakująca treść funkcji lub zmienna
Z właśnie prototypu funkcji kompilator może kontynuować bez błędów, ale konsolidator nie można rozpoznać wywołania adres, ponieważ nie jest dostępna funkcja kodu ani zastrzeżonej zmiennej. Nie będą widzieć tego błędu, dopóki nie zostaną utworzone wywołanie funkcji, że konsolidator musi zostać rozpoznany.  
  
## <a name="example"></a>Przykład  
 Wywołanie funkcji w głównym spowoduje LNK2019, ponieważ prototyp umożliwia kompilatorowi wydaje się, że funkcja istnieje.  Konsolidator stwierdzi, że nie.  
  
```  
// LNK2019_MFBV.cpp  
// LNK2019 expected  
void DoSomething(void);  
int main() {  
   DoSomething();  
}  
```  
  
## <a name="example"></a>Przykład  
 W języku C++ upewnij się, obejmują implementacji określoną funkcję dla klasy, a nie tylko prototypu w definicji klasy. Jeśli definiujesz klasy poza pliku nagłówka, należy uwzględnić nazwę klasy przed funkcji (`Classname::memberfunction`).  
  
```  
// LNK2019_MFBV_2.cpp  
// LNK2019 expected  
struct A {  
   static void Test();  
};  
  
// Should be void A::Test() {}  
void Test() {}  
  
int main() {  
   A AObject;  
   AObject.Test();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Błąd narzędzi konsolidatora LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)