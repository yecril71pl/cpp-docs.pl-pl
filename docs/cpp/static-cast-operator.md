---
title: Operator static_cast
ms.date: 11/04/2016
f1_keywords:
- static_cast_cpp
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
ms.openlocfilehash: 8551d41417647ee4f759e2547e2c1909c59d78cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213206"
---
# <a name="static_cast-operator"></a>Operator static_cast

Konwertuje *wyrażenie* na typ *typu,* na podstawie tylko typów, które są obecne w wyrażeniu.

## <a name="syntax"></a>Składnia

```
static_cast <type-id> ( expression )
```

## <a name="remarks"></a>Uwagi

W standardowym C++ nie jest wykonywane żadne sprawdzenie typu w czasie wykonywania, aby pomóc w zapewnieniu bezpieczeństwa konwersji. W C++/CX, wykonywane są sprawdzenia czasu kompilacji i czasu wykonywania. Aby uzyskać więcej informacji, zobacz [rzutowanie](casting.md).

**`static_cast`** Operatora można używać na potrzeby operacji takich jak konwertowanie wskaźnika do klasy bazowej na wskaźnik do klasy pochodnej. Takie konwersje nie zawsze są bezpieczne.

Ogólnie używa się **`static_cast`** , gdy chcesz skonwertować liczbowe typy danych, takie jak wyliczenia na liczby całkowite lub liczby całkowite na Floating, i że masz pewne typy danych, które są wykorzystywane podczas konwersji. **`static_cast`** Konwersje nie są tak bezpieczne jak **`dynamic_cast`** konwersje, ponieważ nie **`static_cast`** sprawdzają typów w czasie wykonywania **`dynamic_cast`** . **`dynamic_cast`** Do niejednoznacznego wskaźnika zakończy się niepowodzeniem, podczas gdy **`static_cast`** zwraca wartość tak, jakby nic się nie stało; może to być niebezpieczne. Chociaż **`dynamic_cast`** konwersje są bezpieczniejsze, **`dynamic_cast`** działają tylko w przypadku wskaźników lub odwołań, a sprawdzanie typu w czasie wykonywania jest narzutem. Aby uzyskać więcej informacji, zobacz [dynamic_cast operator](../cpp/dynamic-cast-operator.md).

W poniższym przykładzie wiersz `D* pd2 = static_cast<D*>(pb);` nie jest bezpieczny, ponieważ `D` może mieć pola i metody, które nie znajdują się w `B` . Jednak wiersz `B* pb2 = static_cast<B*>(pd);` jest bezpieczną konwersją, ponieważ `D` zawsze zawiera wszystkie z nich `B` .

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

W przeciwieństwie do [dynamic_cast](../cpp/dynamic-cast-operator.md)nie jest przeprowadzane sprawdzanie w czasie wykonywania **`static_cast`** konwersji `pb` . Obiekt wskazywany przez `pb` nie może być obiektem typu `D` , w tym przypadku użycie `*pd2` może być katastrofalne. Na przykład wywołanie funkcji, która jest elementem członkowskim `D` klasy, ale nie `B` klasy, może spowodować naruszenie zasad dostępu.

**`dynamic_cast`** Operatory i **`static_cast`** przesuwają wskaźnik w całej hierarchii klas. Jest jednak **`static_cast`** zależne wyłącznie od informacji podanych w instrukcji Cast i dlatego mogą być niebezpieczne. Na przykład:

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

Jeśli `pb` naprawdę wskazuje na obiekt typu `D` , a następnie uzyska `pd1` tę `pd2` samą wartość. Otrzymają one również taką samą wartość, jeśli `pb == 0` .

Jeśli `pb` wskazuje obiekt typu, `B` a nie do kompletnej `D` klasy, **`dynamic_cast`** będzie wystarczająco dużo, aby zwrócić zero. Jednakże **`static_cast`** opiera się na potwierdzeniu programisty, który `pb` wskazuje na obiekt typu `D` i po prostu zwraca wskaźnik do tego `D` obiektu.

**`static_cast`** W związku z tym można wykonać odwrotność konwersji niejawnych, w tym przypadku wyniki są niezdefiniowane. Pozostało do programisty, aby sprawdzić, czy wyniki **`static_cast`** konwersji są bezpieczne.

To działanie dotyczy także innych typów niż typy klas. Na przykład, **`static_cast`** może służyć do konwersji z int na **`char`** . Jednak wyniki **`char`** mogą nie mieć wystarczającej liczby bitów, aby pomieścić całą **`int`** wartość. Ponownie pozostało do programisty, aby sprawdzić, czy wyniki **`static_cast`** konwersji są bezpieczne.

**`static_cast`** Operatora można także użyć do wykonania dowolnej niejawnej konwersji, w tym konwersji standardowych i konwersji zdefiniowanych przez użytkownika. Na przykład:

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

**`static_cast`** Operator może jawnie skonwertować wartość całkowitą na typ wyliczeniowy. Jeśli wartość typu całkowitego nie wchodzi w zakres wartości wyliczenia, wynikowa wartość wyliczenia jest niezdefiniowana.

**`static_cast`** Operator konwertuje wartość wskaźnika o wartości null na wartość wskaźnika o wartości null typu docelowego.

Każde wyrażenie może być jawnie konwertowane na typ void przez **`static_cast`** operatora. Docelowy typ void może opcjonalnie zawierać **`const`** **`volatile`** atrybut,, lub **`__unaligned`** .

**`static_cast`** Operator nie może rzutować **`const`** atrybutów, **`volatile`** , ani **`__unaligned`** . Aby uzyskać informacje na temat usuwania tych atrybutów, zobacz [Operator const_cast](../cpp/const-cast-operator.md) .

**/CLI C++:** Ze względu na niebezpieczeństwo wykonywania niezaznaczonych rzutów w stosunku do ponownego lokalizowania modułu wyrzucania elementów bezużytecznych, użycie **`static_cast`** powinna być tylko w kodzie krytycznym dla wydajności, gdy jest to konieczne. Jeśli musisz użyć **`static_cast`** w trybie wydania, zastąp go [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) w kompilacjach debugowania, aby upewnić się, że powodzenie.

## <a name="see-also"></a>Zobacz także

[Operatory rzutowania](../cpp/casting-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
