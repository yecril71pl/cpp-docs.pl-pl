---
title: '&lt;wyliczenia kodekvt&gt;'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: e67290d8de0b8251191c4a93b66b7e19a293ed61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371944"
---
# <a name="ltcodecvtgt-enums"></a>&lt;wyliczenia kodekvt&gt;

## <a name="codecvt_mode-enumeration"></a><a name="codecvt_mode"></a>Codecvt_mode Wyliczenie

Określa informacje o konfiguracji dla aspektów [regionalnych.](../standard-library/locale-class.md)

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>Uwagi

Wyliczenie definiuje trzy stałe, które dostarczają informacje o konfiguracji do ustawień regionalnych aspektów zadeklarowanych w [ \<>. ](../standard-library/codecvt.md) Odrębne wartości to:

- `consume_header`, aby zużywać początkową sekwencję nagłówków podczas odczytywania sekwencji wielobajtowej i określić endianness kolejnej sekwencji wielobajtowej do odczytu

- `generate_header`, aby wygenerować początkową sekwencję nagłówka podczas pisania sekwencji wielobajtowej w celu reklamowania endianness kolejnej sekwencji wielobajtowej, która ma zostać napisana

- `little_endian`, aby wygenerować sekwencję wielobajtową w porządku mało endijskim, w przeciwieństwie do domyślnej kolejności big-endian

Te stałe mogą być ORed razem w dowolnych kombinacji.

## <a name="see-also"></a>Zobacz też

[\<>kodekvt](../standard-library/codecvt.md)
