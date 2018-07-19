---
title: time_base — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- locale/std::time_base
dev_langs:
- C++
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e1111ede44edc36e5399d82b3c4e088b20cc1c9
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957301"
---
# <a name="timebase-class"></a>time_base — Klasa

Klasa służy jako klasa bazowa dla zestawów reguł klasy szablonu time_get, definiująca tylko Typ wyliczany `dateorder` oraz kilka stałych tego typu.

## <a name="syntax"></a>Składnia

```cpp
class time_base : public locale::facet {
public:
    enum dateorder {no_order,
    dmy,
 mdy,
    ymd,
 ydm};
    time_base(
 size_t _Refs = 0)
 ~time_base();

};
```

## <a name="remarks"></a>Uwagi

Każdej z nich charakteryzuje się inny sposób, aby uporządkować składniki daty. Stałe są następujące:

- `no_order` Określa losowej kolejności.

- `dmy` Określa kolejność dzień, miesiąc, a następnie roku, tak jak 2 1979 grudnia.

- `mdy` Określa kolejność miesiąc, dzień, a następnie roku, tak jak 2 grudnia 1979.

- `ymd` Określa kolejność rok, miesiąc, a następnie dzień, jak 1979/12/2.

- `ydm` Określa kolejność rok, dzień, a następnie miesiąca, tak jak gru 1979:2.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
