---
title: "Stałe globalne w C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f47be9bad6cf7c8ccafac5dc8ce3786f8ada0dfb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="global-constants-in-c"></a>Stałe globalne w C++
Stałe globalne w C++ mieć statycznego powiązania. Ta lokalizacja jest inna niż C. Jeśli spróbujesz użyć globalnym stałej w języku C++ w wielu plikach błąd nierozwiązane zewnętrznych. Kompilator optymalizuje stałe globalne, brakuje miejsca zarezerwowane dla zmiennej.  
  
 Jednym ze sposobów rozwiązania tego błędu jest dołączyć const inicjacjach w pliku nagłówka i dołączenie nagłówka w plikach CPP, gdy jest to konieczne, tak jakby był prototypu funkcji. Inną możliwością jest zmienna z systemem innym niż stała i użyj odwołania stałej, oceniając go.  
  
 Poniższy przykład generuje C2019:  
  
```  
// global_constants.cpp  
// LNK2019 expected  
void test(void);  
const int lnktest1 = 0;  
  
int main() {  
   test();  
}  
```  
  
 a następnie  
  
```  
// global_constants_2.cpp  
// compile with: global_constants.cpp  
extern int lnktest1;  
  
void test() {  
  int i = lnktest1;   // LNK2019  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Błąd narzędzi konsolidatora LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)