---
title: __unaligned | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unaligned_cpp
dev_langs:
- C++
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d73b082b9f41d03eb0b1a8c9fe772351ff4da91f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="unaligned"></a>__unaligned

**Microsoft określonych**. Gdy zadeklarować wskaźnika z `__unaligned` modyfikator, kompilator przyjęto założenie, że wskaźnik adresów dane, które nie jest wyrównany. W związku z tym odpowiednie platformy kod jest generowane w celu obsługi niewyrównany odczytuje i zapisuje za pomocą wskaźnika.

## <a name="remarks"></a>Uwagi

Modyfikator opisuje wyrównania danych dotyczy wskaźnika; przyjęto, że wskaźnik sam być wyrównane.

Konieczność `__unaligned` — słowo kluczowe jest zależna od platformy i środowiska. Nie można oznaczyć odpowiednio danych może spowodować problemy z zakresu od spadku wydajności do błędów sprzętu. `__unaligned` Modyfikator nie jest prawidłowa dla x86 platformy.

Aby uzyskać więcej informacji na temat wyrównania zobacz:

- [align](../cpp/align-cpp.md)

- [Operator __alignof](../cpp/alignof-operator.md)

- [pakiet](../preprocessor/pack.md)

- [/Zp (Wyrównanie składowej struktury)](../build/reference/zp-struct-member-alignment.md)

- [Przykłady wyrównania struktury](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)
