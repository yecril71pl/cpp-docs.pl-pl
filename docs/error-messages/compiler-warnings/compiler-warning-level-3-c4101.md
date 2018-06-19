---
title: Kompilatora (poziom 3) ostrzeżenie C4101 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4101
dev_langs:
- C++
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 973b966e4b589cb35ffc92da9031779b14d448e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291118"
---
# <a name="compiler-warning-level-3-c4101"></a>Kompilator C4101 ostrzegawcze (poziom 3)
'Identyfikator': nieużywane zmiennej lokalnej  
  
 Zmienna lokalna nie jest używany. To ostrzeżenie odbędzie się oczywiste sytuacji:  
  
```  
// C4101a.cpp  
// compile with: /W3  
int main() {  
int i;   // C4101  
}  
```  
  
 To ostrzeżenie odbywa się jednak również podczas wywoływania metody **statycznych** funkcji członkowskiej przez wystąpienie klasy:  
  
```  
// C4101b.cpp  
// compile with:  /W3  
struct S {  
   static int func()  
   {  
      return 1;  
   }  
};  
  
int main() {  
   S si;   // C4101, si is never used  
   int y = si.func();  
   return y;  
}  
```  
  
 W takim przypadku kompilator używa informacji o `si` dostępu **statycznych** funkcji, ale wystąpienie klasy nie jest wymagane do wywołania **statycznych** funkcji; dlatego ostrzeżenia. Aby usunąć to ostrzeżenie, możesz:  
  
-   Dodaj Konstruktor, w którym kompilator użyje wystąpienia `si` w wywołaniu `func`.  
  
-   Usuń **statycznych** — słowo kluczowe w definicji `func`.  
  
-   Wywołanie **statycznych** funkcji jawnie: `int y = S::func();`.