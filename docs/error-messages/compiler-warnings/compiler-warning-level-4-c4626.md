---
title: Kompilator ostrzeżenie (poziom 4) C4626
ms.date: 11/04/2016
f1_keywords:
- C4626
helpviewer_keywords:
- C4626
ms.assetid: 7f822ff4-a4a3-4f17-b45b-e8b7b4659a14
ms.openlocfilehash: cb00365d12a60885a86a42417bf1c1052a5c6d6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349607"
---
# <a name="compiler-warning-level-4-c4626"></a>Kompilator ostrzeżenie (poziom 4) C4626

"Klasa pochodna": operator przypisania został niejawnie zdefiniowany jako usunięty, ponieważ operator przypisania klasy bazowej jest niedostępne lub zostały usunięte

Operator przypisania został usunięty lub nie jest dostępna w klasie bazowej, a w związku z tym nie został wygenerowany dla klasy pochodnej. Błąd kompilatora spowoduje, że każda próba przypisywać obiektów tego typu.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

Poniższy przykład generuje C4626 i pokazuje, jak go naprawić:

```
// C4626
// compile with: /W4
#pragma warning(default : 4626)
class B
{
// public:
   B& operator = (const B&)
   {
      return *this;
   }
};

class D : public B
{

}; // C4626 - to fix, make B's copy constructor public

int main()
{
   D m;
   D n;
   // m = n;   // this line will cause an error
}
```