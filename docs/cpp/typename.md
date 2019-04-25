---
title: typename
ms.date: 11/04/2016
f1_keywords:
- typename_cpp
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
ms.openlocfilehash: 7dbe4381465036bdd102b3be753a18451886a3d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166259"
---
# <a name="typename"></a>typename

W definicjach szablonów stanowi wskazówkę kompilator, że typem jest nieznany identyfikator. W przypadku list parametrów szablonu służy do określania parametrów typu.

## <a name="syntax"></a>Składnia

```
typename identifier;
```

## <a name="remarks"></a>Uwagi

This — słowo kluczowe należy użyć, jeśli nazwa w definicji szablonu jest kwalifikowana nazwa, która jest zależna od argumentu szablonu; jest to opcjonalne, jeśli kwalifikowana nazwa nie jest zależny. Aby uzyskać więcej informacji, zobacz [szablony i rozpoznawanie nazw](../cpp/templates-and-name-resolution.md).

**Element TypeName** mogą być używane przez dowolny typ w dowolnym miejscu w deklaracji szablonu lub definicji. Nie są dozwolone na liście klas bazowych, chyba że jako argument szablonu dla klasy bazowej szablonu.

```cpp
template <class T>
class C1 : typename T::InnerType // Error - typename not allowed.
{};
template <class T>
class C2 : A<typename T::InnerType>  // typename OK.
{};
```

**Typename** — słowo kluczowe może również służyć zamiast **klasy** parametr szablonu na liście. Na przykład poniższe instrukcje są semantycznie równoważne:

```cpp
template<class T1, class T2>...
template<typename T1, typename T2>...
```

## <a name="example"></a>Przykład

```cpp
// typename.cpp
template<class T> class X
{
   typename T::Y m_y;   // treat Y as a type
};

int main()
{
}
```

## <a name="see-also"></a>Zobacz także

[Szablony](../cpp/templates-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)