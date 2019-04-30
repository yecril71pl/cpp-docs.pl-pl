---
title: '&lt;codecvt —&gt; Typy wyliczeniowe'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: 0b43c7c148076e96dd0d3f444ffa8b6bad7c8b29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405290"
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt —&gt; Typy wyliczeniowe

## <a name="codecvt_mode"></a>  codecvt_mode — wyliczenie

Określa informacje o konfiguracji dla [ustawień regionalnych](../standard-library/locale-class.md) aspektami.

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>Uwagi

Wyliczenie definiuje trzy stałych, które dostarczają informacje konfiguracyjne do zestawów reguł ustawień regionalnych, zadeklarowany w [ \<codecvt >](../standard-library/codecvt.md). Są różne wartości:

- `consume_header`, do wykorzystania sekwencji początkowej nagłówka, odczytując wielobajtowych sekwencji i określić kolejność bajtów kolejnych wielobajtowych sekwencji do odczytu

- `generate_header`, można wygenerować sekwencji początkowej nagłówka podczas zapisywania wielobajtowych sekwencji anonsowanie kolejność bajtów kolejnych wielobajtowych sekwencji do zapisania

- `little_endian`, aby wygenerować wielobajtowych sekwencji w kolejności little-endian, w przeciwieństwie do domyślnej kolejności big-endian

Te stałe może być operacja logiczna ze sobą w dowolnej kombinacji.

## <a name="see-also"></a>Zobacz także

[\<codecvt>](../standard-library/codecvt.md)<br/>
