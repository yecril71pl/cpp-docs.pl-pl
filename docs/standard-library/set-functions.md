---
title: '&lt;ustawić funkcje&gt;'
ms.date: 11/04/2016
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: a3a63fb86caa3485b1ee14538c3eb1f1ff72923e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875772"
---
# <a name="ltsetgt-functions"></a>&lt;ustawić funkcje&gt;

## <a name="swap"></a>Zamień (mapa)

Zamienia elementy z dwóch zestawów.

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Zestaw udostępniający elementy, które mają zostać zamienione lub zestaw, którego elementy mają być wymieniane z tymi z zestawu *po lewej stronie*.

\ *lewo*
Zestaw, którego elementy mają być wymieniane z tymi zestawami *po prawej stronie*.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytmem wyspecjalizowanym dla klasy kontenera ustawioną do wykonywania funkcji składowej `left.`[swap](../standard-library/set-class.md#swap)(`right`). Jest to wystąpienie częściowego porządkowania szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu

`template` \< **klasa**> **void swap**( **t &** , **t &** )

w klasie algorytmu działa przez przypisanie i jest operacją powolnej. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy Container.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla zestawu klasy składowej [:: swap](../standard-library/set-class.md#swap) na przykład używania wersji szablonu `swap`.

## <a name="swap_multiset"></a>swap (zestaw wielokrotny)

Wymienia elementy dwóch zestawów wielozbiorówowych.

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Zestaw *wielokrotny*udostępniający elementy, które mają zostać zamienione, lub zestaw wielokrotny, którego elementy mają być wymieniane z tymi z zestawu wielokrotnego.

\ *lewo*
Zestaw *wielokrotny*, którego elementy mają być wymieniane z tymi samymi zestawem wielokrotnym.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytmem wyspecjalizowanym dla zestawu wielokrotnego klasy kontenera, aby wykonać funkcję członkowską `left.`[swap](../standard-library/multiset-class.md#swap)(`right`). Jest to wystąpienie częściowego porządkowania szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu

`template` \< **klasa**> **void swap**( **t &** , **t &** )

w klasie algorytmu działa przez przypisanie i jest operacją powolnej. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy Container.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla klasy składowej zestaw [wielokrotny:: swap](../standard-library/multiset-class.md#swap)na przykład używania wersji szablonu `swap`.
