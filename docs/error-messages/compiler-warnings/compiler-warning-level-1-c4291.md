---
title: Kompilator ostrzeżenie (poziom 1) C4291 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4291
dev_langs:
- C++
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8c5f2fe57d26de4b4b2f88a85f20b99344ac201
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038051"
---
# <a name="compiler-warning-level-1-c4291"></a>Kompilator ostrzeżenie (poziom 1) C4291

"deklaracją": nie pasującego operatora delete odnaleziony; pamięć nie zostanie zwolniona, jeśli Inicjalizacja generuje wyjątek

Umieszczanie [nowe](../../cpp/new-operator-cpp.md) jest używany dla których nie ma żadnych umieszczania [Usuń](../../cpp/delete-operator-cpp.md).

Jeśli pamięć została przydzielona do obiektu za pomocą operatora **nowe**, wywoływany jest konstruktor obiektu. Jeśli Konstruktor zgłasza wyjątek, wszystkie pamięci, która została przydzielona dla obiektu powinien być z cofniętą alokacją. Nie może to mieć miejsce, chyba że operator **Usuń** istnieje funkcja pasujący operator **nowe**.

Jeśli korzystasz z operatora **nowe** bez żadnych dodatkowych argumentów i kompilujesz z [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHS](../../build/reference/eh-exception-handling-model.md), lub opcji/eha, aby włączyć obsługę wyjątków, kompilator wygeneruje kod operator wywołania **Usuń** Jeśli Konstruktor zgłasza wyjątek.

Jeśli używasz postaci umieszczania **nowe** operatora (formularza z argumentami prócz rozmiaru alokacji) i konstruktora obiektu zgłasza wyjątek, kompilator wygeneruje nadal kod, aby wywołać operator **Usuń**; ale tylko wtedy będzie wykonywać więc jeśli formularza położenia operatora **Usuń** istnieje dopasowanie formularza położenia operatora **nowe** , przydzielonej pamięci. Na przykład:

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

Powyższy przykład generuje ostrzeżenie C4291, ponieważ żadna z form położenia operatora **Usuń** została zdefiniowana, które odpowiadają formularza położenia operatora **nowe**. Aby rozwiązać ten problem, Wstaw następujący kod powyżej **głównego**. Należy zauważyć, że wszystkie przeciążonego operatora **Usuń** parametry funkcji są zgodne z tymi przeciążonego operatora **nowe**, z wyjątkiem pierwszego parametru.

```
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```