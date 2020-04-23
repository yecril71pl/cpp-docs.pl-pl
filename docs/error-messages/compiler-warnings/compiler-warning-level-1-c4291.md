---
title: Ostrzeżenie kompilatora (poziom 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: c1972236e30be4e6ca738b606b00398f5c7860e0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754855"
---
# <a name="compiler-warning-level-1-c4291"></a>Ostrzeżenie kompilatora (poziom 1) C4291

"deklaracja": nie znaleziono usuwania operatora pasującego; pamięć nie zostanie zwolniona, jeśli inicjalizacja zda wyjątek

Miejsce [docelowe nowe](../../cpp/new-operator-cpp.md) jest używane, dla którego nie ma miejsca docelowego [usunąć](../../cpp/delete-operator-cpp.md).

Gdy pamięć jest przydzielana dla obiektu z **operatorem nowym,** wywoływany jest konstruktor obiektu. Jeśli konstruktor zgłasza wyjątek, wszelkie pamięci, która została przydzielona dla obiektu powinny być cofnięte alokacji. Nie może to mieć miejsca, chyba że istnieje funkcja **usuwania** operatora, która pasuje do **nowego**operatora .

Jeśli operator **jest nowy** bez żadnych dodatkowych argumentów i skompilować z [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHs](../../build/reference/eh-exception-handling-model.md)lub /EHa opcje, aby włączyć obsługę wyjątków, kompilator wygeneruje kod do wywołania operatora **delete,** jeśli konstruktor zgłasza wyjątek.

Jeśli używasz formularza umieszczania **nowego** operatora (formularz z argumentami oprócz rozmiaru alokacji) i konstruktor obiektu zgłasza wyjątek, kompilator nadal będzie generować kod do wywołania **usunięcia**operatora; ale zrobi to tylko wtedy, gdy istnieje formularz umieszczania **usunięcia** operatora, który pasuje do formularza umieszczania **nowego** operatora, który przydzielił pamięć. Przykład:

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

Powyższy przykład generuje ostrzeżenie C4291, ponieważ nie zdefiniowano formularza umieszczania **usuwania** operatora, który pasuje do formularza umieszczania operatora **nowego**. Aby rozwiązać ten problem, wstaw poniższy kod powyżej **głównego**. Należy zauważyć, że wszystkie parametry funkcji **usuwania** przeciążonego operatora są zgodne z parametrami przeciążonego operatora **new**, z wyjątkiem pierwszego parametru.

```cpp
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```
