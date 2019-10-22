---
title: time_base — Klasa
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: ddaf9905e859c062031940d35adfa2a3393dbb5a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685785"
---
# <a name="time_base-class"></a>time_base — Klasa

Klasa służy jako klasa bazowa dla aspektów szablonu klasy time_get, definiując tylko typ wyliczeniowy `dateorder` i kilka stałych tego typu.

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

- `no_order` określa brak określonej kolejności.

- `dmy` określa dzień zamówienia, miesiąc, rok, jak w 2 grudnia 1979.

- `mdy` określa miesiąc zamówienia, dzień, rok, zgodnie z 2 grudnia 1979.

- `ymd` określa rok zamówienia, miesiąc, dzień, jak w 1979/12/2.

- `ydm` określa rok zamówienia, dzień, miesiąc, jak w 1979:2 grudnia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<locale >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
