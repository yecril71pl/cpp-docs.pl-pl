---
title: Ostrzeżenie kompilatora (poziom 4) C4626
ms.date: 11/04/2016
f1_keywords:
- C4626
helpviewer_keywords:
- C4626
ms.assetid: 7f822ff4-a4a3-4f17-b45b-e8b7b4659a14
ms.openlocfilehash: 665a21d9f0221b2cf3db111142576669a3b5d728
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198267"
---
# <a name="compiler-warning-level-4-c4626"></a>Ostrzeżenie kompilatora (poziom 4) C4626

"Klasa pochodna": operator przypisania został niejawnie zdefiniowany jako usunięty, ponieważ operator przypisania klasy bazowej jest niedostępny lub usunięty

Operator przypisania został usunięty lub nie jest dostępny w klasie podstawowej i dlatego nie został wygenerowany dla klasy pochodnej. Każda próba przypisania obiektów tego typu spowoduje błąd kompilatora.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Poniższy przykład generuje C4626 i pokazuje, jak to naprawić:

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
