---
title: discard_block_engine — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::discard_block_engine
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
ms.openlocfilehash: 76a78a2f47bd160c6b2b981b1ccdda2ef3a90575
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454394"
---
# <a name="discardblockengine-class"></a>discard_block_engine — Klasa

Generuje losową sekwencję przez odrzucenie wartości zwracanych przez aparat podstawowy.

## <a name="syntax"></a>Składnia

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>Parametry

*Wyszukiwarce*\
Typ aparatu podstawowego.

*ST*\
**Rozmiar bloku**. Liczba wartości w każdym bloku.

*R*\
**Używany blok**. Liczba wartości w każdym używanym bloku. Pozostałe są odrzucane (`P` - `R`). **Warunek wstępny**:`0 < R ≤ P`

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|

Aby uzyskać więcej informacji na temat elementów członkowskich silnika, zobacz [ \<Random >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Ta klasa szablonu opisuje adapter aparatu, który tworzy wartości przez odrzucenie niektórych wartości zwracanych przez aparat podstawowy.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[\<random>](../standard-library/random.md)
