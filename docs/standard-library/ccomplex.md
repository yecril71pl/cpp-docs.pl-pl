---
title: '&lt;ccomplex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ccomplex>
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
ms.openlocfilehash: ab9e95eb7b432a85a75d73d388ec069b0d04ac62
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51517205"
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;

Dołącza nagłówek biblioteki standardowej języka C++ [ \<złożonych >](../standard-library/complex.md), które efektywnie dołącza nagłówek biblioteki standardowej C \<complex.h > i dodaje skojarzone nazwy `std` przestrzeni nazw.

## <a name="syntax"></a>Składnia

```cpp
#include <ccomplex>
```

## <a name="remarks"></a>Uwagi

Dołączenie tego pliku nagłówkowego gwarantuje również, że nazwy zadeklarowane przez zewnętrzne powiązanie w nagłówku standardowej biblioteki C są deklarowane w `std` przestrzeni nazw.

Nazwa `clog`, która jest zadeklarowana w \<complex.h >, nie jest zdefiniowany w `std` przestrzeni nazw z powodu potencjalnych konfliktów z `clog` zadeklarowanego w [ \<iostream >](../standard-library/iostream.md).

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
