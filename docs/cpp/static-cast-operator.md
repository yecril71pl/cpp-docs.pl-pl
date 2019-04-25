---
title: Operator static_cast
ms.date: 11/04/2016
f1_keywords:
- static_cast_cpp
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
ms.openlocfilehash: dca6d5297379e6ddc1c70dba80f35f2f55672e49
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267131"
---
# <a name="staticcast-operator"></a>Operator static_cast

Konwertuje *wyrażenie* do typu *identyfikator typu* wyłącznie według typów, które są obecne w wyrażeniu.

## <a name="syntax"></a>Składnia

```
static_cast <type-id> ( expression )
```

## <a name="remarks"></a>Uwagi

W standardowym C++ nie jest wykonywane żadne sprawdzenie typu w czasie wykonywania, aby pomóc w zapewnieniu bezpieczeństwa konwersji. W C++/CX, wykonywane są sprawdzenia czasu kompilacji i czasu wykonywania. Aby uzyskać więcej informacji, zobacz [rzutowanie](casting.md).

**Static_cast** operator może służyć do operacji, takich jak konwertowanie wskaźnika do klasy bazowej na wskaźnik do klasy pochodnej. Takie konwersje nie zawsze są bezpieczne.

Ogólnie rzecz biorąc używasz **static_cast** niektóre typy danych, gdy chcesz przekonwertować typy danych numerycznych, takich jak typy wyliczeniowe na liczby całkowite lub liczby całkowite na wartości zmiennoprzecinkowe i są zaangażowane w konwersji. **static_cast** konwersje nie są tak bezpieczne, jak **dynamic_cast** konwersji, ponieważ **static_cast** sprawdza żadnych typów w czasie wykonywania, podczas gdy **dynamic_cast** wykonuje. A **dynamic_cast** do niejednoznacznego wskaźnika zakończy się niepowodzeniem, podczas gdy **static_cast** zwraca, jak gdyby nic się nie stało; może to być niebezpieczne. Mimo że **dynamic_cast** konwersje są bezpieczniejsze, **dynamic_cast** tylko works na wskaźników lub odwołań i wyboru typu run-time to obciążenie. Aby uzyskać więcej informacji, zobacz [dynamic_cast Operator](../cpp/dynamic-cast-operator.md).

W przykładzie poniżej, wiersz `D* pd2 = static_cast<D*>(pb);` nie jest bezpieczne ponieważ `D` może posiadać pola i metody, które nie znajdują się w `B`. Jednakże wiersz `B* pb2 = static_cast<B*>(pd);` jest bezpieczną konwersją, ponieważ `D` zawsze zawiera wszystkie `B`.

```cpp
// static_cast_Operator.cpp
// compile with: /LD
class B {};

class D : public B {};

void f(B* pb, D* pd) {
   D* pd2 = static_cast<D*>(pb);   // Not safe, D can have fields
                                   // and methods that are not in B.

   B* pb2 = static_cast<B*>(pd);   // Safe conversion, D always
                                   // contains all of B.
}
```

W przeciwieństwie do [dynamic_cast](../cpp/dynamic-cast-operator.md), jest wykonywane żadne sprawdzenie czasu wykonywania, na **static_cast** konwersja `pb`. Obiekt wskazywany przez `pb` nie może być obiektem typu `D`, w którym to przypadku użycia `*pd2` mogłoby być katastrofalne. Na przykład, wywołanie funkcji, która jest elementem członkowskim `D` klasy, ale nie `B` klasy, może spowodować naruszenie zasad dostępu.

**Dynamic_cast** i **static_cast** operatorów przesuwania wskaźnika w całej hierarchii klas. Jednak **static_cast** opiera się wyłącznie na informacjach dostarczonych w instrukcji cast i dlatego może być niebezpieczne. Na przykład:

```cpp
// static_cast_Operator_2.cpp
// compile with: /LD /GR
class B {
public:
   virtual void Test(){}
};
class D : public B {};

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);
   D* pd2 = static_cast<D*>(pb);
}
```

Jeśli `pb` naprawdę wskazuje na obiekt typu `D`, następnie `pd1` i `pd2` otrzymają taką samą wartość. Otrzymają one również taką samą wartość Jeśli `pb == 0`.

Jeśli `pb` wskazuje na obiekt typu `B` , a nie pełne `D` klasy, następnie **dynamic_cast** będzie wiedzieć wystarczająco dużo, aby zwrócić zero. Jednak **static_cast** opiera się na potwierdzeniu programisty, `pb` wskazuje na obiekt typu `D` i po prostu zwraca wskaźnik do tego domniemanego obiektu `D` obiektu.

W związku z tym **static_cast** może wykonać odwrotność konwersji niejawnych, w tym przypadku wyniki są niezdefiniowane. Pozostaje ona do programisty należy sprawdzenie, czy wyniki **static_cast** konwersji są bezpieczne.

To działanie dotyczy także innych typów niż typy klas. Na przykład **static_cast** może służyć do konwersji z int do **char**. Jednak wynikowy **char** może nie mieć wystarczającej liczby bitów, aby pomieścić całą **int** wartość. Ponownie go pozostało do programisty należy sprawdzenie, czy wyniki **static_cast** konwersji są bezpieczne.

**Static_cast** operator może również służyć do wykonywania niejawnej konwersji, w tym konwersji standardowych i konwersje zdefiniowane przez użytkownika. Na przykład:

```cpp
// static_cast_Operator_3.cpp
// compile with: /LD /GR
typedef unsigned char BYTE;

void f() {
   char ch;
   int i = 65;
   float f = 2.5;
   double dbl;

   ch = static_cast<char>(i);   // int to char
   dbl = static_cast<double>(f);   // float to double
   i = static_cast<BYTE>(ch);
}
```

**Static_cast** operator może jawnie przekonwertować wartością całkowitą typ wyliczenia. Jeśli wartość typu całkowitego nie wchodzi w zakres wartości wyliczenia, wynikowa wartość wyliczenia jest niezdefiniowana.

**Static_cast** operator konwertuje wartość pustego wskaźnika do wartości pustego wskaźnika typu miejsca docelowego.

Dowolne wyrażenie może być jawnie konwertowane na typ void przez **static_cast** operatora. Docelowy typ void może opcjonalnie uwzględnić **const**, **volatile**, lub **__unaligned** atrybutu.

**Static_cast** operator nie może oddać **const**, **volatile**, lub **__unaligned** atrybutów. Zobacz [const_cast Operator](../cpp/const-cast-operator.md) informacji na temat usuwania tych atrybutów.

**C++/CLI:** Ze względu na niebezpieczeństwo wykonywania niesprawdzonych rzutowań na górze przenoszonego modułu odśmiecania pamięci, użycie **static_cast** powinny być tylko w kodzie wydajności krytycznej, gdy masz pewność, będą działać poprawnie. Jeśli musisz użyć **static_cast** w trybie zwolnienia, zastąp go [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) w swoich kompilacjach debugowania, aby zapewnić sukces.

## <a name="see-also"></a>Zobacz także

[Operatory rzutowania](../cpp/casting-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)