---
title: selectany | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- selectany_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee48bf8a739f7fc024604ba178b56da99844861b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102349"
---
# <a name="selectany"></a>selectany

**Microsoft Specific**

Informuje kompilator, że element zadeklarowany danych globalnych (zmiennej lub obiektu) jest pobranie dowolnego COMDAT (spakowanych funkcji).

## <a name="syntax"></a>Składnia

```
__declspec( selectany ) declarator
```

## <a name="remarks"></a>Uwagi

W czasie Jeśli wiele definicji COMDAT są widoczne, konsolidator wybiera jedną i odrzuca wszystkie pozostałe. Jeśli opcja konsolidatora [/OPT: REF](../build/reference/opt-optimizations.md) (optymalizacje) jest zaznaczone, a następnie nastąpi eliminacji COMDAT Aby usunąć wszystkie elementy danych bez odwołań w danych wyjściowych konsolidatora.

Konstruktory i przypisania przez globalnej funkcji lub metody statyczne w deklaracji nie należy tworzyć odwołanie i nie zapobiega eliminacji/OPT: REF. Efekty uboczne z takiego kodu nie powinno zależne od, gdy nie istnieją żadne inne odniesienia do danych.

W przypadku obiektów dynamicznie zainicjowany, globalne **selectany** spowoduje odrzucenie kod inicjujący nieużywanej obiektu, jak również.

Element danych globalnych normalnie mogą być inicjowane tylko raz w projekcie EXE lub DLL. **selectany** mogą być używane w inicjalizacji danych globalnych, zdefiniowane przez nagłówki, gdy ten sam nagłówek pojawi się w więcej niż jednego pliku źródłowego. **selectany** jest dostępna w kompilatorach, C i C++.

> [!NOTE]
>  **selectany** można stosować tylko do inicjowania rzeczywiste elementy danych globalnych, które są widoczne na zewnątrz.

## <a name="example"></a>Przykład

Ten kod przedstawia sposób użycia **selectany** atrybutu:

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

Ten kod przedstawia sposób użycia **selectany** atrybutu, aby upewnić się, gdy używany jest składanie COMDAT danych [/OPT: ICF](../build/reference/opt-optimizations.md) — opcja konsolidatora. Należy pamiętać, że dane muszą być oznaczone **selectany** i umieszczone w **const** sekcji (tylko do odczytu). Należy jawnie określić sekcji tylko do odczytu.

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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)