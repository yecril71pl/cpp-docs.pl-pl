---
title: '&lt;funkcje wektorowe &gt;'
ms.date: 11/04/2016
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
ms.openlocfilehash: bf28e44b4f603b1e4d6a87f0c28b42d6cc159980
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224555"
---
# <a name="ltvectorgt-functions"></a>&lt;funkcje wektorowe &gt;

## <a name="swap"></a><a name="swap"></a>wymiany

Wymienia elementy dwóch wektorów.

```cpp
template <class Type, class Allocator>
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Wektor udostępniający elementy do zamiany lub wektor, którego elementy mają być wymieniane z *pozostałymi*środkami wektora.

*lewym*\
Wektor, którego elementy są wymieniane z *prawami*do wektora.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytmem wyspecjalizowanym dla wektora klasy kontenera, aby wykonać funkcję członkowską `left` . [Vector:: swap](../standard-library/vector-class.md) *(Right*). Są to wystąpienia częściowego uporządkowania szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu, **`template`** \< **class T**> **void swap**( **t&**, **t&**) w klasie algorytmu działa przez przypisanie i jest operacją powolne. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy Container.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla funkcji składowej [Vector:: swap](../standard-library/vector-class.md) dla przykładu korzystającego z wersji szablonu `swap` .
