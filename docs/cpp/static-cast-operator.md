---
title: Operator static_cast
ms.date: 11/04/2016
f1_keywords:
- static_cast_cpp
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
ms.openlocfilehash: 37708bf50b28eb120af8e8a79e770c3121e6f509
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178590"
---
# <a name="static_cast-operator"></a>Operator static_cast

Konwertuje *wyrażenie* na typ *typu,* na podstawie tylko typów, które są obecne w wyrażeniu.

## <a name="syntax"></a>Składnia

```
static_cast <type-id> ( expression )
```

## <a name="remarks"></a>Uwagi

W standardowym C++ nie jest wykonywane żadne sprawdzenie typu w czasie wykonywania, aby pomóc w zapewnieniu bezpieczeństwa konwersji. W C++/CX, wykonywane są sprawdzenia czasu kompilacji i czasu wykonywania. Aby uzyskać więcej informacji, zobacz [rzutowanie](casting.md).

Operatora **static_cast** można używać do operacji takich jak konwertowanie wskaźnika do klasy bazowej na wskaźnik do klasy pochodnej. Takie konwersje nie zawsze są bezpieczne.

Ogólnie rzecz biorąc, używasz **static_cast** , gdy chcesz skonwertować liczbowe typy danych, takie jak wyliczenia na liczby całkowite lub liczby całkowite na Floating, i że masz pewne typy danych w ramach konwersji. Konwersje **static_cast** nie są tak bezpieczne jak konwersje **dynamic_cast** , ponieważ **static_cast** nie sprawdza typu w czasie wykonywania, a **dynamic_cast** . **Dynamic_cast** do niejednoznacznego wskaźnika zakończy się niepowodzeniem, podczas gdy **static_cast** zwraca, jakby nic się nie stało. może to być niebezpieczne. Chociaż konwersje **dynamic_cast** są bezpieczniejsze, **dynamic_cast** działa tylko na wskaźnikach lub odwołaniach, a sprawdzanie typu w czasie wykonywania jest narzutem. Aby uzyskać więcej informacji, zobacz [dynamic_cast operator](../cpp/dynamic-cast-operator.md).

W poniższym przykładzie wiersz `D* pd2 = static_cast<D*>(pb);` nie jest bezpieczny, ponieważ `D` może mieć pola i metody, które nie znajdują się w `B`. Jednak wiersz `B* pb2 = static_cast<B*>(pd);` jest bezpieczną konwersją, ponieważ `D` zawsze zawiera wszystkie `B`.

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

W przeciwieństwie do [dynamic_cast](../cpp/dynamic-cast-operator.md), w **static_cast** konwersji `pb`nie jest przeprowadzane sprawdzanie czasu wykonania. Obiekt wskazywany przez `pb` nie może być obiektem typu `D`, w takim przypadku korzystanie z `*pd2` może być katastrofalne. Na przykład wywołanie funkcji, która jest elementem członkowskim klasy `D`, ale nie klasy `B`, może spowodować naruszenie zasad dostępu.

Operatory **dynamic_cast** i **static_cast** przesuwają wskaźnik w całej hierarchii klas. Jednak **static_cast** opiera się wyłącznie na informacjach dostarczonych w instrukcji Cast i dlatego może być niebezpieczna. Na przykład:

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

Jeśli `pb` naprawdę wskazuje na obiekt typu `D`, `pd1` i `pd2` będą mieć tę samą wartość. Otrzymają one również taką samą wartość, jeśli `pb == 0`.

Jeśli `pb` wskazuje obiekt typu `B`, a nie do kompletnej klasy `D`, wówczas **dynamic_cast** będzie wystarczająco dużo wiedzieć, aby zwrócić zero. Jednakże **static_cast** opiera się na potwierdzeniu programisty, który `pb` wskazuje na obiekt typu `D` i po prostu zwraca wskaźnik do tego obiektu `D` obiekt.

W związku z tym **static_cast** może wykonać odwrotność konwersji niejawnych, w tym przypadku wyniki są niezdefiniowane. Pozostało do programisty, aby sprawdzić, czy wyniki konwersji **static_cast** są bezpieczne.

To działanie dotyczy także innych typów niż typy klas. Na przykład, **static_cast** może służyć do konwersji z int na **char**. Jednak otrzymany **znak** może nie mieć wystarczającej liczby bitów, aby pomieścić całą wartość **int** . Ponownie pozostało do programisty, aby sprawdzić, czy wyniki konwersji **static_cast** są bezpieczne.

Operatora **static_cast** można również użyć do wykonania dowolnej niejawnej konwersji, w tym konwersji standardowych i konwersji zdefiniowanych przez użytkownika. Na przykład:

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

Operator **static_cast** może jawnie skonwertować wartość całkowitą na typ wyliczeniowy. Jeśli wartość typu całkowitego nie wchodzi w zakres wartości wyliczenia, wynikowa wartość wyliczenia jest niezdefiniowana.

Operator **static_cast** konwertuje wartość wskaźnika o wartości null na wartość wskaźnika o wartości null typu docelowego.

Każde wyrażenie może być jawnie konwertowane na typ void przez operator **static_cast** . Docelowy typ void może opcjonalnie zawierać atrybut **const**, **volatile**lub **__unaligned** .

Operator **static_cast** nie może rzutować atrybutów **const**, **volatile**lub **__unaligned** . Aby uzyskać informacje na temat usuwania tych atrybutów, zobacz [Operator const_cast](../cpp/const-cast-operator.md) .

**C++/CLI:** Ze względu na niebezpieczeństwo wykonywania niezaznaczonych rzutów na początku ponownego lokalizowania modułu wyrzucania elementów bezużytecznych użycie **static_cast** powinno być w kodzie krytycznym dla wydajności tylko wtedy, gdy jest to konieczne. Jeśli musisz użyć **static_cast** w trybie wydania, zastąp go [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) w kompilacjach debugowania, aby upewnić się, że powodzenie.

## <a name="see-also"></a>Zobacz też

[Operatory rzutowania](../cpp/casting-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
