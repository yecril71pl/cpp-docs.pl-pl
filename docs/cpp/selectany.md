---
title: selectany
ms.date: 11/04/2016
f1_keywords:
- selectany_cpp
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
ms.openlocfilehash: e279184322c239e7768eb8fd4321ee451b2cb94c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213232"
---
# `selectany`

**Specyficzne dla firmy Microsoft**

Informuje kompilator, że zadeklarowany element danych globalnych (zmienna lub obiekt) jest pobraniem COMDAT (spakowaną funkcją).

## <a name="syntax"></a>Składnia

> **`__declspec( selectany )`***deklarator*

## <a name="remarks"></a>Uwagi

W czasie linku, jeśli są widoczne liczne definicje elementu COMDAT, konsolidator wybiera jeden i odrzuca resztę. Jeśli wybrano opcję konsolidatora [`/OPT:REF`](../build/reference/opt-optimizations.md) (Optymalizacja), COMDAT eliminacja nastąpi w celu usunięcia wszystkich elementów danych, do których nie ma odwołań w danych wyjściowych konsolidatora.

Konstruktory i przypisania przez funkcję globalną lub metody statyczne w deklaracji nie tworzą odwołania i nie uniemożliwią/OPT: eliminacji odwołania. Skutki uboczne tego kodu nie powinny być zależne od tego, czy istnieją inne odwołania do danych.

W przypadku dynamicznej inicjacji obiekty globalne **`selectany`** odrzucają również kod inicjujący obiektu, którego nie można odwołać.

Element danych globalnych można zwykle zainicjować tylko raz w projekcie EXE lub DLL. **`selectany`** może służyć do inicjowania danych globalnych zdefiniowanych przez nagłówki, gdy ten sam nagłówek występuje w więcej niż jednym pliku źródłowym. **`selectany`** jest dostępny zarówno w kompilatorach C, jak i C++.

> [!NOTE]
> **`selectany`** mogą być stosowane tylko do rzeczywistej inicjalizacji elementów danych globalnych, które są widoczne na zewnątrz.

## <a name="example"></a>Przykład

Ten kod pokazuje, jak używać **`selectany`** atrybutu:

```cpp
//Correct - x1 is initialized and externally visible
__declspec(selectany) int x1=1;

//Incorrect - const is by default static in C++, so
//x2 is not visible externally (This is OK in C, since
//const is not by default static in C)
const __declspec(selectany) int x2 =2;

//Correct - x3 is extern const, so externally visible
extern const __declspec(selectany) int x3=3;

//Correct - x4 is extern const, so it is externally visible
extern const int x4;
const __declspec(selectany) int x4=4;

//Incorrect - __declspec(selectany) is applied to the uninitialized
//declaration of x5
extern __declspec(selectany) int x5;

// OK: dynamic initialization of global object
class X {
public:
X(int i){i++;};
int i;
};

__declspec(selectany) X x(1);
```

## <a name="example"></a>Przykład

Ten kod pokazuje, jak używać **`selectany`** atrybutu w celu zapewnienia, że dane COMDAT są również używane w przypadku korzystania z [`/OPT:ICF`](../build/reference/opt-optimizations.md) opcji konsolidatora. Należy zauważyć, że dane muszą być oznaczone **`selectany`** i umieszczone w **`const`** sekcji (ReadOnly). Należy jawnie określić sekcję tylko do odczytu.

```cpp
// selectany2.cpp
// in the following lines, const marks the variables as read only
__declspec(selectany) extern const int ix = 5;
__declspec(selectany) extern const int jx = 5;
int main() {
   int ij;
   ij = ix + jx;
}
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[`__declspec`](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
