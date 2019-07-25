---
title: time_base — Klasa
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: 85565dc0c0ec904551eb8dd981cfacc9a2e1f256
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460037"
---
# <a name="timebase-class"></a>time_base — Klasa

Klasa służy jako klasa bazowa dla aspektów klasy szablonu time_get, definiując tylko typ `dateorder` wyliczeniowy i kilka stałych tego typu.

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

Każda stała charakteryzuje inny sposób uporządkowania składników daty. Stałe są następujące:

- `no_order`Określa brak określonej kolejności.

- `dmy`określa dzień zamówienia, miesiąc, rok, jak w 2 grudnia 1979.

- `mdy`określa miesiąc zamówienia, dzień, rok, zgodnie z 2 grudnia 1979.

- `ymd`Określa rok zamówienia, miesiąc, dzień, jak w 1979/12/2.

- `ydm`Określa rok zamówienia, dzień, miesiąc, jak w 1979: 2 grudnia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
