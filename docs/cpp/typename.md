---
title: Element TypeName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- typename_cpp
dev_langs:
- C++
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77e3cc6f9691cf071a420ee2659c713f9e28036f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061594"
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