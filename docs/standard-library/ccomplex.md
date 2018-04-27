---
title: '&lt;ccomplex&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <ccomplex>
dev_langs:
- C++
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ea7ffa0db396242ab072efd01ccdd3def75fea9
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
