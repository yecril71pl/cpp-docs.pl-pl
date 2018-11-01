---
title: time_base — Klasa
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: e790237e506aa32bafdb39938d841307bbc4d9c3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593404"
---
# <a name="timebase-class"></a>time_base — Klasa

Klasa służy jako klasa bazowa dla zestawów reguł klasy szablonu time_get, definiująca tylko Typ wyliczany `dateorder` oraz kilka stałych tego typu.

## <a name="syntax"></a>Składnia

```cpp
class time_base : public locale::facet {
public:
    enum dateorder {
        no_order,
        dmy,
        mdy,
        ymd,
        ydm
    };
    time_base(size_t _Refs = 0)
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
