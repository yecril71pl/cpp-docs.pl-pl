---
title: Ostrzeżenie kompilatora (poziom 1) C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: cdc25155aced50331851e9581c346155c6f8e45c
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966344"
---
# <a name="compiler-warning-level-1-c4407"></a>Ostrzeżenie kompilatora (poziom 1) C4407

Rzutowanie między różnymi wskaźnikami do przedstawienia elementu członkowskiego, kompilator może wygenerować niepoprawny kod

Wykryto nieprawidłowe rzutowanie.

C4407 można generować z powodu zgodności kompilatora, który został wykonany w programie Visual Studio 2005. Wskaźnik do elementu członkowskiego wymaga teraz kwalifikowanej nazwy i operatora address-of (&).

C4407 może wystąpić w przypadku rzutowania między wskaźnikami dziedziczenia wielu elementów członkowskich na jeden wskaźnik dziedziczenia do elementu członkowskiego. Czasami może to być możliwe, ale czasami nie jest, ponieważ reprezentacja wskaźnika do elementu członkowskiego pojedynczego dziedziczenia nie zawiera wystarczających informacji. Kompilacja z **/VMM** może pomóc (Aby uzyskać więcej informacji, zobacz [/VMM,/VMS,/VMV (reprezentacja ogólnego przeznaczenia)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)). Możesz również spróbować ponownie rozmieścić klasy bazowe; Kompilator wykrywa utratę informacji w konwersji, ponieważ klasa bazowa ma przesunięcie o wartości innej niż zero od pochodnego.

Poniższy przykład generuje C4407:

```cpp
// C4407.cpp
// compile with: /W1 /c
struct C1 {};
struct C2 {};
struct C3 : C1, C2 {};

typedef void(C3::*PMF_C3)();
typedef void(C2::*PMF_C2)();

PMF_C2 f1(PMF_C3 pmf) {
   return (PMF_C2)pmf;   // C4407, change type of cast,
   // or reverse base class inheritance of C3 (i.e. : C2, C1)
}
```