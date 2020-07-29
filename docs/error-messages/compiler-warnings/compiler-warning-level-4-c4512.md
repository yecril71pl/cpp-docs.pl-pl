---
title: Ostrzeżenie kompilatora (poziom 4) C4512
ms.date: 11/04/2016
f1_keywords:
- C4512
helpviewer_keywords:
- C4512
ms.assetid: afb68995-684a-4be5-a73a-38d7a16dc030
ms.openlocfilehash: 068bdb2c7c87e8fe7cd3e482f53934de098a6166
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218094"
---
# <a name="compiler-warning-level-4-c4512"></a>Ostrzeżenie kompilatora (poziom 4) C4512

"Class": nie można wygenerować operatora przypisania

Kompilator nie może wygenerować operatora przypisania dla danej klasy. Nie utworzono operatora przypisania.

Operator przypisania dla klasy podstawowej, która nie jest dostępna w klasie pochodnej, może spowodować to ostrzeżenie.

Aby uniknąć tego ostrzeżenia, określ zdefiniowany przez użytkownika operator przypisania dla klasy.

Kompilator generuje również funkcję operatora przypisania dla klasy, która nie definiuje jednej. Ten operator przypisania jest składowych kopią elementów członkowskich danych obiektu. Ponieważ **`const`** elementy danych nie mogą być modyfikowane po inicjacji, jeśli Klasa zawiera **`const`** element, domyślny operator przypisania nie będzie działać. Inną przyczyną ostrzeżenia C4512 jest deklaracja niestatycznej składowej danych typu referencyjnego. Jeśli celem jest utworzenie typu bez kopiowania, należy również uniemożliwić utworzenie domyślnego konstruktora kopiującego.

Ostrzeżenie C4512 dla kodu można rozwiązać na jeden z trzech sposobów:

- Jawnie Zdefiniuj operator przypisania dla klasy.

- Usuń **`const`** lub Operator Reference z elementu danych w klasie.

- Aby pominąć ostrzeżenie, użyj instrukcji #pragma [Warning](../../preprocessor/warning.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C4512.

```cpp
// C4512.cpp
// compile with: /EHsc /W4
// processor: x86

class Base {
private:
   const int a;

public:
   Base(int val = 0) : a(val) {}
   int get_a() { return a; }
};   // C4512 warning

class Base2 {
private:
   const int a;

public:
   Base2(int val = 0) : a(val) {}
   Base2 & operator=( const Base2 & ) { return *this; }
   int get_a() { return a; }
};

// Type designer intends this to be non-copyable because it has a
// reference member
class Base3
{
private:
   char& cr;

public:
   Base3(char& r) : cr(r) {}
   // Uncomment the following line to explicitly disable copying:
   // Base3(const Base3&) = delete;
};   // C4512 warning

int main() {
   Base first;
   Base second;

   // OK
   Base2 first2;
   Base2 second2;

   char c = 'x';
   Base3 first3(c);
   Base3 second3 = first3; // C2280 if no default copy ctor
}
```
