---
title: Ostrzeżenie kompilatora (poziom 1) C4350
ms.date: 11/04/2016
f1_keywords:
- C4350
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
ms.openlocfilehash: 890ecd4fcec1212fa04a58b0eaab8c2eb4206763
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187222"
---
# <a name="compiler-warning-level-1-c4350"></a>Ostrzeżenie kompilatora (poziom 1) C4350

zmiana zachowania: wywołano element członkowski 'członek1' zamiast 'członek2'

Element rvalue nie może być powiązany z odwołaniem niestałym. W wersjach programu Visual C++ przed visual Studio 2003 można było powiązać rvalue z odwołaniem niestałym w ramach inicjalizacji bezpośredniej. Ten kod zawiera teraz ostrzeżenie.

W celu zapewnienia zgodności z poprzednimi wersjami nadal można powiązać rvalues z odwołaniami niebędącymi const, ale standardowe konwersje są preferowane wszędzie tam, gdzie to możliwe.

To ostrzeżenie reprezentuje zmianę zachowania z kompilatora Visual C++ .NET 2002. W przypadku włączenia tego ostrzeżenia może być możliwe poprawność kodu. Na przykład, może być podawane przy użyciu szablonu klasy **std:: auto_ptr** .

Jeśli zostanie wyświetlone to ostrzeżenie, sprawdź kod, aby sprawdzić, czy zależy on od powiązania rvalues z odwołaniami niebędącymi const. Dodanie stałej do odwołania lub dostarczenie dodatkowego przeciążenia odwołania do stałej może rozwiązać problem.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Poniższy przykład generuje C4350:

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
