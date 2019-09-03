---
title: raw_native_types — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: eb08a8e7cb081bd7a470c3c1ecf1492a7a65f833
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216066"
---
# <a name="raw_native_types-import-attribute"></a>raw_native_types — atrybut importowania

**C++Specjalne**

Wyłącza korzystanie z klas obsługi COM w funkcjach otoki wysokiego poziomu i wymusza użycie typów danych niskiego poziomu.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **raw_native_types**

## <a name="remarks"></a>Uwagi

Domyślnie metody obsługi błędów wysokiego poziomu wykorzystują klasy obsługi com [_bstr_t](../cpp/bstr-t-class.md) i [_variant_t](../cpp/variant-t-class.md) `BSTR` zamiast wskaźników i `VARIANT` nieprzetworzonych interfejsów com. Te klasy hermetyzowają szczegóły alokacji i cofania przydziału pamięci masowej dla tych typów danych oraz znacznie upraszczają Operacje rzutowania i konwersji typów.

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
