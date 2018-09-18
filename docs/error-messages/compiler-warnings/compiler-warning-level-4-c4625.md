---
title: Kompilator ostrzeżenie (poziom 4) C4625 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4625
dev_langs:
- C++
helpviewer_keywords:
- C4625
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 970321370aeeea0ca4324f9a25d3ee1d8e54e15e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069108"
---
# <a name="compiler-warning-level-4-c4625"></a>Kompilator ostrzeżenie (poziom 4) C4625

"Klasa pochodna": Konstruktor kopiujący został niejawnie zdefiniowany jako usunięty, ponieważ Konstruktor kopiowania klasy bazowej jest niedostępne lub zostały usunięte

Konstruktor kopiujący został usunięty lub nie jest dostępna w klasie bazowej, a w związku z tym nie został wygenerowany dla klasy pochodnej. Błąd kompilatora spowoduje, że każda próba kopiowanie obiektu tego typu.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4625 i pokazuje, jak go naprawić.

```
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