---
title: "Kompilatora (poziom 1) ostrzeżenie C4291 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4291
dev_langs: C++
helpviewer_keywords: C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a1c03e12805c35ce04322a7ffb4d48499a9a9f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4291"></a>Kompilator C4291 ostrzegawcze (poziom 1)
"deklaracją": nie pasującego operatora delete znaleziono; pamięć nie zostanie zwolniona, jeśli Inicjalizacja generuje wyjątek  
  
 Położenia [nowe](../../cpp/new-operator-cpp.md) jest używany dla których nie istnieją żadne umieszczania [usunąć](../../cpp/delete-operator-cpp.md).  
  
 Gdy jest przydzielana pamięć dla obiekt z operatorem **nowe**, Konstruktor obiektu jest wywoływany. Jeśli w Konstruktorze zgłasza wyjątek, wszystkie pamięci, która została przydzielona dla obiekt powinien alokację. Nie może to mieć miejsce, chyba że operator **usunąć** funkcja istnieje pasujący operator **nowe**.  
  
 Użycie operatora **nowe** bez żadnych dodatkowych argumentów i skompiluj z [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHS](../../build/reference/eh-exception-handling-model.md), lub opcji/eha Włącz obsługę wyjątków, kompilator wygeneruje kod operator wywołania **usunąć** Jeśli w Konstruktorze zgłasza wyjątek.  
  
 Jeśli używasz umieszczania formę **nowe** — operator (formularza z argumentami oprócz rozmiar alokacji) i konstruktora obiektu zgłasza wyjątek, kompilator nadal wygeneruje kod wywoła operator **usunąć**; ale tylko będzie wykonywał tak więc jeśli formularza umieszczania operatora **usunąć** istnieje dopasowania umieszczania formę operator **nowe** przydzielone pamięci. Na przykład:  
  
```  
// C4291.cpp  
// compile with: /EHsc /W1  
#include <malloc.h>  
  
class CList  
{  
public:  
   CList(int)  
   {  
      throw "Fail!";  
   }  
};  
  
void* operator new(size_t size, char* pszFilename, int nLine)  
{  
   return malloc(size);  
}  
  
int main(void)  
{  
   try  
   {  
      // This will call ::operator new(unsigned int) to allocate heap  
      // memory. Heap memory pointed to by pList1 will automatically be  
      // deallocated by a call to ::operator delete(void*) when  
      // CList::CList(int) throws an exception.  
      CList* pList1 = new CList(10);  
   }  
   catch (...)  
   {  
   }  
  
   try  
   {  
      // This will call the overloaded ::operator new(size_t, char*, int)  
      // to allocate heap memory. When CList::CList(int) throws an  
      // exception, ::operator delete(void*, char*, int) should be called  
      // to deallocate the memory pointed to by pList2. Since  
      // ::operator delete(void*, char*, int) has not been implemented,  
      // memory will be leaked when the deallocation cannot occur.  
      CList* pList2 = new(__FILE__, __LINE__) CList(20);   // C4291  
   }  
   catch (...)  
   {  
   }  
}  
```  
  
 Powyższy przykład generuje ostrzeżenie C4291, ponieważ żaden formularz umieszczania operatora **usunąć** został zdefiniowany formularz umieszczania operatora, które odpowiadają **nowe**. Aby rozwiązać ten problem, Wstaw następujący kod powyżej **głównego**. Zwróć uwagę, że wszystkie Przeciążony operator **usunąć** parametrów funkcji zgodne z tymi przeciążonego operatora **nowe**, z wyjątkiem pierwszego parametru.  
  
```  
void operator delete(void* pMem, char* pszFilename, int nLine)  
{  
   free(pMem);  
}  
```