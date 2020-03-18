---
title: '&lt;typy wyliczeniowe&gt; codecvt'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: bbef1fe28c3321f06c0cc586062cd017168f8e73
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421927"
---
# <a name="ltcodecvtgt-enums"></a>&lt;typy wyliczeniowe&gt; codecvt

## <a name="codecvt_mode"></a>codecvt_mode, Wyliczenie

Określa informacje o konfiguracji dla zestawów reguł [ustawień regionalnych](../standard-library/locale-class.md) .

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>Uwagi

Wyliczenie definiuje trzy stałe, które dostarczają informacje o konfiguracji do zestawów reguł ustawień regionalnych zadeklarowanych w [\<codecvt >](../standard-library/codecvt.md). Unikatowe wartości to:

- `consume_header`, aby użyć początkowej sekwencji nagłówka podczas odczytywania sekwencji wielobajtowej i ustalania wartości endian kolejnej sekwencji wielobajtowej do odczytu

- `generate_header`, aby wygenerować początkową sekwencję nagłówka podczas pisania sekwencji wielobajtowej w celu zaanonsowania przystąpień kolejnej sekwencji wielobajtowej do zapisania

- `little_endian`w celu wygenerowania sekwencji wielobajtowej w kolejności little-endian, w przeciwieństwie do domyślnej kolejności big-endian

Te stałe mogą być logicznie razem w dowolnej kombinacji.

## <a name="see-also"></a>Zobacz też

[\<codecvt >](../standard-library/codecvt.md)
