---
title: Kompilator ostrzeżenie (poziom 4) C4626 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4626
dev_langs:
- C++
helpviewer_keywords:
- C4626
ms.assetid: 7f822ff4-a4a3-4f17-b45b-e8b7b4659a14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16ae3e9d9e54d54a419bfde2250fc02f780e8e54
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083668"
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