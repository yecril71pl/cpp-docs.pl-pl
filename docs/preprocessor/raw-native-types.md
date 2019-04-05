---
title: raw_native_types
ms.date: 11/04/2016
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: 32b77905ef7025334e5101e76864da9a15c50cf6
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024971"
---
# <a name="rawnativetypes"></a>raw_native_types
**Określonego język C++**

Wyłącza używanie klas obsługi COM w funkcjach otoki wysokiego poziomu, a zamiast tego wymusza stosowanie typów danych niskiego poziomu.

## <a name="syntax"></a>Składnia

```
raw_native_types
```

## <a name="remarks"></a>Uwagi

Domyślnie wysokiego poziomu metody obsługi błędów za pomocą klas obsługi COM [_bstr_t](../cpp/bstr-t-class.md) i [_variant_t](../cpp/variant-t-class.md) zamiast `BSTR` i `VARIANT` i typy danych COM surowego interfejsu wskaźników. W ramach tych zajęć hermetyzacji szczegółów alokowanie i dealokowanie pamięci magazynu dla tych typów danych i znacznie upraszczają operacji rzutowania i konwersji typu.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)