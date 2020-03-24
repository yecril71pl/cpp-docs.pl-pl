---
title: operator = = (&lt;przykładowy kontener&gt;)
ms.date: 11/04/2016
f1_keywords:
- std.==
- std::==
- operator==
- std.operator==
- std::operator==
- ==
helpviewer_keywords:
- operator ==, containers
- operator==, containers
- == operator, with specific standard C++ objects
ms.assetid: d3d8754e-5157-4b8b-bf9c-da41856f5eed
ms.openlocfilehash: 08adfcc770551d3050daa46c870b950e468c95b3
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150645"
---
# <a name="operator-ltsample-containergt"></a>operator = = (&lt;przykładowy kontener&gt;)

> [!NOTE]
> Ten temat znajduje się w dokumentacji C++ firmy Microsoft jako przykład niefunkcjonalny kontenerów używanych w C++ standardowej bibliotece. Aby uzyskać więcej informacji, zobacz [ C++ Kontenery biblioteki standardowej](../standard-library/stl-containers.md).

Przeciążenia `operator==` do porównywania dwóch obiektów [kontenera](../standard-library/sample-container-class.md)szablonów klas.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Wartość zwracana

Zwraca `left.`[rozmiaru](../standard-library/container-class-size.md) `== right.size && equal(left.`[Rozpocznij](../standard-library/container-class-begin.md)`, left.`[`, right.begin)`](../standard-library/container-class-end.md) .

## <a name="see-also"></a>Zobacz też

[\<przykładowego kontenera >](../standard-library/sample-container.md)
