---
title: Ostrzeżenie kompilatora (poziom 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: cd161a37683703fd67b4c682558a51121c130816
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175717"
---
# <a name="compiler-warning-level-1-c4291"></a>Ostrzeżenie kompilatora (poziom 1) C4291

"Deklaracja": nie znaleziono pasującego operatora delete; pamięć nie zostanie zwolniona, jeśli Inicjalizacja zgłosi wyjątek

Zostanie użyte [nowe](../../cpp/new-operator-cpp.md) miejsce umieszczenia, dla którego nie ma żadnego [usunięcia](../../cpp/delete-operator-cpp.md)umieszczania.

Po przydzieleniu pamięci dla obiektu z operatorem **New**, Konstruktor obiektu jest wywoływany. Jeśli Konstruktor zgłasza wyjątek, wszystkie pamięci, które zostały przydzieloną dla tego obiektu, powinny zostać cofnięte. Nie można tego zrobić, chyba że istnieje funkcja **delete** operatora, która pasuje do operatora **New**.

Jeśli używasz operatora **New** bez żadnych dodatkowych argumentów i Kompiluj z opcjami [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHS](../../build/reference/eh-exception-handling-model.md)lub/EHa, aby włączyć obsługę wyjątków, kompilator generuje kod w celu wywołania operatora **delete** , jeśli Konstruktor zgłosi wyjątek.

Jeśli używasz formularza położenia operatora **New** (formularz z argumentami oprócz rozmiaru alokacji) i Konstruktor obiektu zgłasza wyjątek, kompilator nadal będzie generował kod, aby wywołać operator **delete**; jednak będzie to zrobić tylko wtedy, gdy istnieje forma rozmieszczenia operatora **delete** pasująca do formy umieszczania operatora **New** , która przydzieliła pamięć. Na przykład:

```cpp
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

Powyższy przykład generuje ostrzeżenie C4291, ponieważ nie zdefiniowano formy umieszczania operatora **delete** , która pasuje do formy umieszczania operatora **New**. Aby rozwiązać ten problem, Wstaw poniższy kod powyżej **Main**. Zwróć uwagę, że wszystkie parametry funkcji **delete** przeciążonego operatora są zgodne z tymi, które są używane przez przeciążony operator **New**, z wyjątkiem pierwszego parametru.

```
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```
