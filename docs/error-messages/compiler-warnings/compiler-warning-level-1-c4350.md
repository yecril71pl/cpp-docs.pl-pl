---
title: Kompilator ostrzeżenie (poziom 1) C4350 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4350
dev_langs:
- C++
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ad49a7471be257fa0c22f66fa1bb2bbea049194
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096694"
---
# <a name="compiler-warning-level-1-c4350"></a>Kompilator ostrzeżenie (poziom 1) C4350

zmiana zachowania: wywołano element członkowski 'członek1' zamiast 'członek2'

Odwołanie niestałe nie może być powiązane rvalue. W wersjach programu Visual C++ przed Visual Studio 2003 było możliwe powiązać rvalue odwołanie niestałe w inicjalizacji bezpośredniej. Ten kod wyświetla teraz ostrzeżenie.

W celu zapewnienia zgodności z poprzednimi wersjami jest nadal możliwe powiązać rvalues odwołania do wartości innej niż stała, ale konwersje standardowe są preferowane w przypadku, gdy jest to możliwe.

To ostrzeżenie reprezentuje zmianę zachowania kompilatora Visual C++ .NET 2002. Jeśli włączone, to ostrzeżenie można prawdopodobnie należy podać prawidłowy kod. Na przykład może być udzielona, gdy za pomocą **std::auto_ptr** szablonu klasy.

Jeśli to ostrzeżenie, należy zbadać jego kod, aby sprawdzić, czy jest to uzależnione od rvalues wiązanie do odwołania o wartości innej niż stała. Dodawanie typu const do odwołania albo udostępniające dodatkowe przeciążenia odwołanie niestałe może rozwiązać ten problem.

To ostrzeżenie jest domyślnie wyłączona. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Poniższy przykład spowoduje wygenerowanie C4350:

```cpp
// C4350.cpp
// compile with: /W1
#pragma warning (default : 4350)
class A {};

class B
{
public:
   B(B&){}
   // try the following instead:
   // B(const B&){}

   B(A){}
   operator A(){ return A();}
};

B source() { return A(); }

int main()
{
   B ap(source());   // C4350
}
```