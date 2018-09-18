---
title: Kompilator ostrzeżenie (poziom 4) C4512 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4512
dev_langs:
- C++
helpviewer_keywords:
- C4512
ms.assetid: afb68995-684a-4be5-a73a-38d7a16dc030
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9aee9e7f48430ddc9b2b9a6a7f055ac8b1e32b71
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029952"
---
# <a name="compiler-warning-level-4-c4512"></a>Kompilator ostrzeżenie (poziom 4) C4512

"class": nie można wygenerować operatora przypisania

Kompilator nie można wygenerować operatora przypisania dla danej klasy. Żaden operator przypisywania został utworzony.

Operator przypisania klasy podstawowej, która nie jest dostępna w klasie pochodnej może być przyczyną tego ostrzeżenia.

Aby uniknąć tego ostrzeżenia, należy określić operatora przypisania zdefiniowanego przez użytkownika, dla klasy.

Kompilator wygeneruje również funkcję operatora przypisania dla klasy, w którym nie zdefiniowano jeden. Ten operator przypisania jest kopią wszystkich elementów członkowskich składowych danych obiektu. Ponieważ `const` elementów danych nie może być modyfikowany po inicjalizacji, jeśli klasa zawiera `const` elementu, operator przypisania domyślne nie będzie działać. Inną przyczyną ostrzeżenie C4512 jest deklaracją niestatycznej składowej danych typu referencyjnego. Jeśli chcesz utworzyć-copyable typu, możesz także zapobiega tworzeniu domyślny Konstruktor kopiujący.

Ostrzeżenie C4512 rozpozna dla kodu w jednym z trzech sposobów:

- Jawne zdefiniowanie operatora przypisania klasy.

- Usuń **const** lub operatora odwołania z elementu danych w klasie.

- Użyj #pragma [ostrzeżenie](../../preprocessor/warning.md) instrukcję, aby pominąć to ostrzeżenie.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4512.

```
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