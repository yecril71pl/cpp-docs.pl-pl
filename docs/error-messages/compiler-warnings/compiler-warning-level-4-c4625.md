---
title: Ostrzeżenie kompilatora (poziom 4) C4625
ms.date: 11/04/2016
f1_keywords:
- C4625
helpviewer_keywords:
- C4625
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
ms.openlocfilehash: d98e295a9a48da16b58202bc172e112b5c0287d9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990713"
---
# <a name="compiler-warning-level-4-c4625"></a>Ostrzeżenie kompilatora (poziom 4) C4625

"Klasa pochodna": Konstruktor kopiujący został niejawnie zdefiniowany jako usunięty, ponieważ Konstruktor kopiujący klasy bazowej jest niedostępny lub usunięty

Konstruktor kopiujący został usunięty lub nie jest dostępny w klasie bazowej i dlatego nie został wygenerowany dla klasy pochodnej. Każda próba skopiowania obiektu tego typu spowoduje błąd kompilatora.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C4625 i pokazuje, jak rozwiązać ten problem.

```cpp
// C4625.cpp
// compile with: /W4 /c
#pragma warning(default : 4625)

struct A {
   A() {}

private:
   A(const A&) {}
};

struct C : private virtual A {};
struct B :  C {};   // C4625 no copy constructor

struct D : A {};
struct E :  D {};   // OK
```
