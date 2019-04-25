---
title: Ostrzeżenie kompilatora C4368
ms.date: 11/04/2016
f1_keywords:
- C4368
helpviewer_keywords:
- C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
ms.openlocfilehash: b2af1166738d867c84ff4ebae832f831af7940ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311502"
---
# <a name="compiler-warning-c4368"></a>Ostrzeżenie kompilatora C4368

Nie można zdefiniować "członek" jako członka zarządzanego "type": mieszane typy nie są obsługiwane.

Element członkowski danych natywnych nie można osadzić w typie CLR.

Możliwe, jednak zadeklarować wskaźnika do typu macierzystego i kontrolować jego okres istnienia w Konstruktor i destruktor i finalizator klasy zarządzanej. Aby uzyskać więcej informacji, zobacz [destruktory i finalizatory](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

To jest zawsze ostrzeżenie jako błąd. Użyj [ostrzeżenie](../../preprocessor/warning.md) pragma może wyłączyć C4368.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4368.

```
// C4368.cpp
// compile with: /clr /c
struct N {};
ref struct O {};
ref struct R {
    R() : m_p( new N ) {}
    ~R() { delete m_p; }

   property N prop;   // C4368
   int i[10];   // C4368

   property O ^ prop2;   // OK
   N * m_p;   // OK
};
```