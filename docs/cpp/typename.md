---
title: typename
ms.date: 11/04/2016
f1_keywords:
- typename_cpp
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
ms.openlocfilehash: 789bb879922bbd96a04085159205d02fb7f495c8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160687"
---
# <a name="typename"></a>typename

W obszarze definicje szablonu program dostarcza wskazówkę do kompilatora, że nieznany identyfikator jest typem. Na listach parametrów szablonu służy do określania parametru typu.

## <a name="syntax"></a>Składnia

```
typename identifier;
```

## <a name="remarks"></a>Uwagi

Tego słowa kluczowego należy użyć, jeśli nazwa w definicji szablonu jest kwalifikowana nazwa, która jest zależna od argumentu szablonu; jest opcjonalne, jeśli kwalifikowana nazwa nie jest zależna. Aby uzyskać więcej informacji, zobacz [Szablony i rozpoznawanie nazw](../cpp/templates-and-name-resolution.md).

**Właściwość TypeName** może być używana przez dowolny typ dowolnego miejsca w deklaracji lub definicji szablonu. Nie jest to dozwolone na liście klas bazowych, chyba że jako argument szablonu dla klasy podstawowej szablonu.

```cpp
template <class T>
class C1 : typename T::InnerType // Error - typename not allowed.
{};
template <class T>
class C2 : A<typename T::InnerType>  // typename OK.
{};
```

Można również użyć słowa kluczowego **TypeName** zamiast **klasy** na listach parametrów szablonu. Na przykład następujące instrukcje są semantycznie równoważne:

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

## <a name="see-also"></a>Zobacz też

[Szablony](../cpp/templates-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
