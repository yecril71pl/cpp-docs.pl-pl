---
title: Błąd kompilatora C3278
ms.date: 11/04/2016
f1_keywords:
- C3278
helpviewer_keywords:
- C3278
ms.assetid: 56f818f5-85a6-4792-843b-54fe16327658
ms.openlocfilehash: ec51064853afa37f75022042c8c6121b6c5248a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201438"
---
# <a name="compiler-error-c3278"></a>Błąd kompilatora C3278

> bezpośrednie wywołanie interfejsu lub czystej metody "*Method*" zakończy się niepowodzeniem w czasie wykonywania

## <a name="remarks"></a>Uwagi

Wykonano wywołanie metody interfejsu lub czystej metody, co jest niedozwolone.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3278:

```cpp
// C3278_2.cpp
// compile with: /clr
using namespace System;
interface class I
{
   void vmf();
};

public ref class C: public I
{
public:
   void vmf()
   {
      Console::WriteLine( "In C::vmf()" );
      I::vmf(); // C3278
   }

};

int main()
{
   C^ pC = gcnew C;
   pC->vmf();
}
```
