---
title: '&lt;codecvt —&gt; wyliczenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: 612570680bfacb2bc9c237c60b3e9f6c4f8266a8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725338"
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

[\<codecvt — >](../standard-library/codecvt.md)<br/>
