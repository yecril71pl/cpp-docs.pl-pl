---
title: selectany
ms.date: 11/04/2016
f1_keywords:
- selectany_cpp
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
ms.openlocfilehash: e8ca82900ffd16264aca494950d4793029e55d9c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365596"
---
# <a name="selectany"></a>selectany

**Specyficzne dla firmy Microsoft**

Informuje kompilator, że zadeklarowany element danych globalnych (zmienna lub obiekt) jest pobraniem dowolnego COMDAT (funkcja spakowana).

## <a name="syntax"></a>Składnia

```
__declspec( selectany ) declarator
```

## <a name="remarks"></a>Uwagi

W czasie łącza, jeśli wiele definicji COMDAT są widoczne, konsolidator wybiera jeden i odrzuca resztę. Jeśli zaznaczona jest opcja konsolidatora [/OPT:REF](../build/reference/opt-optimizations.md) (Optymalizacje), nastąpi eliminacja COMDAT w celu usunięcia wszystkich elementów danych, które nie zostały odwołane w danych wyjściowych konsolidatora.

Konstruktory i przypisanie przez funkcję globalną lub metody statyczne w deklaracji nie tworzą odwołania i nie uniemożliwi /OPT:REF eliminacji. Skutki uboczne takiego kodu nie powinny zależeć od tego, kiedy nie istnieją żadne inne odwołania do danych.

W przypadku dynamicznie inicjowanych obiektów **globalnych, selectany** odrzuci kod inicjowania obiektu nieodwołanego, jak również.

Globalny element danych można zwykle zainicjować tylko raz w projekcie EXE lub DLL. **selectany** może być używany do inicjowania danych globalnych zdefiniowanych przez nagłówki, gdy ten sam nagłówek pojawia się w więcej niż jednym pliku źródłowym. **selectany** jest dostępny zarówno w kompilatorach C i C++.

> [!NOTE]
> **selectany** można zastosować tylko do rzeczywistego inicjowania globalnych elementów danych, które są widoczne zewnętrznie.

## <a name="example"></a>Przykład

Ten kod pokazuje, jak używać atrybutu **selectany:**

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

Ten kod pokazuje, jak używać atrybutu **selectany,** aby zapewnić składanie danych COMDAT podczas korzystania z opcji konsolidatora [/OPT:ICF.](../build/reference/opt-optimizations.md) Należy zauważyć, że dane muszą być oznaczone **selectany** i umieszczone w **const** (tylko w brzmieniu) sekcji. Należy jawnie określić sekcję tylko do odczytu.

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

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
