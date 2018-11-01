---
title: Kompilator ostrzeżenie (poziom 1) C4350
ms.date: 11/04/2016
f1_keywords:
- C4350
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
ms.openlocfilehash: 8f23751151d8d83c68608d926ef422d56dde41a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571954"
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