---
title: C3538 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3538
dev_langs:
- C++
helpviewer_keywords:
- C3538
ms.assetid: ef3698a5-7356-4c62-b9af-5d3a4baed958
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35f852e41ff86b9eed39da0aeb367d7049b8db4b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33262582"
---
# <a name="compiler-error-c3538"></a>C3538 błąd kompilatora
na liście deklaratorów "auto" należy zawsze ustalać do tego samego typu  
  
 Wszystkie zmienne zadeklarowane na liście deklaracji nie rozpoznać do tego samego typu.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że wszystkie `auto` deklaracje na liście ustalać do tego samego typu.  
  
## <a name="example"></a>Przykład  
 Poniższe instrukcje yield C3538. Każda instrukcja deklaruje wiele zmiennych, ale każdy stosowania `auto` — słowo kluczowe nie ustalać do tego samego typu.  
  
```  
// C3538.cpp  
// Compile with /Zc:auto  
// C3538 expected  
int main()  
{  
// Variable x1 is a pointer to char, but y1 is a double.  
   auto * x1 = "a", y1 = 3.14;    
// Variable c is a char and c1 is char*, but c2, and c3 are pointers to pointers.  
   auto c = 'a', *c1 = &c, * c2 = &c1, * c3 = &c2;   
// Variable x2 is an int, but y2 is a double and z is a char.  
   auto x2(1), y2(0.0), z = 'a';   
// Variable a is a pointer to int, but b is a pointer to double.  
   auto *a = new auto(1), *b = new auto(2.0);   
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Auto, słowo kluczowe](../../cpp/auto-keyword.md)