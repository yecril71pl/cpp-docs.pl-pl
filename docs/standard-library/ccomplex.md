---
title: '&lt;ccomplex&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <ccomplex>
dev_langs:
- C++
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de5c67fc88da6fc4674b7dad67b5f74dcc3ce54d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850388"
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;

Zawiera nagłówek standardowa biblioteka C++ [ \<złożonych >](../standard-library/complex.md), w tym skutecznie nagłówka biblioteki standardowe C \<complex.h > i dodaje skojarzone nazwy `std` przestrzeni nazw.

## <a name="syntax"></a>Składnia

```cpp
#include <ccomplex>

```

## <a name="remarks"></a>Uwagi

Ten nagłówek w tym zapewnia, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku biblioteki standardowe C są zadeklarowane w `std` przestrzeni nazw.

Nazwa `clog`, która jest zadeklarowana w \<complex.h >, nie jest zdefiniowany w `std` przestrzeni nazw z powodu potencjalnych konfliktów z `clog` zadeklarowanego w [ \<iostream >](../standard-library/iostream.md).

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
