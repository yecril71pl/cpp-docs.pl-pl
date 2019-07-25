---
title: operator&lt;= (&lt;przykład kontenera&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::<=
- std.operator<=
- operator<=
- std.<=
- std::operator<=
- <=
helpviewer_keywords:
- operator<=
- operator <=
- <= operator, with specific objects
- <= operator
ms.assetid: 338577dd-dc88-4a2b-9e12-0379c54fc8a2
ms.openlocfilehash: c559838f66c483f7c1a76fd17f6a4c07b8aa1fec
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456602"
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt;= (&lt;przykład kontenera&gt;)

> [!NOTE]
> Ten temat znajduje się w dokumentacji C++ firmy Microsoft jako przykład niefunkcjonalny kontenerów używanych w C++ standardowej bibliotece. Aby uzyskać więcej informacji, zobacz [ C++ Kontenery biblioteki standardowej](../standard-library/stl-containers.md).

Operator overloads **< =** do porównania dwóch obiektów [kontenera](../standard-library/sample-container-class.md)klasy szablonu.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
bool operator<=(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Wartość zwracana

Zwraca `!(right < left)`wartość.

## <a name="see-also"></a>Zobacz także

[\<Przykładowy > kontenera](../standard-library/sample-container.md)
