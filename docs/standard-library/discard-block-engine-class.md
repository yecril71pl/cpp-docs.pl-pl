---
title: discard_block_engine — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::discard_block_engine
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
ms.openlocfilehash: a0df754f53b52c134b9eb1126f90882ceaaf1e2f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676827"
---
# <a name="discardblockengine-class"></a>discard_block_engine — Klasa

Generuje losową sekwencję przez odrzucenie wartości zwracanych przez silnik podstawowy.

## <a name="syntax"></a>Składnia

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>Parametry

*Aparat*<br/>
Typ podstawowy aparat.

*P*<br/>
**Rozmiaru bloku**. Liczba wartości w każdym bloku.

*R*<br/>
**Blok używanych**. Liczba wartości w każdym bloku, które są używane. Pozostałe zostaną odrzucone (`P` - `R`). **Warunek wstępny**: `0 < R ≤ P`

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|

Aby uzyskać więcej informacji na temat elementów członkowskich aparatu zobacz [ \<losowy >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Ta klasa szablonu opisuje Adapter aparat, który tworzy wartości przez odrzucenie niektórych wartości zwracanych przez silnik podstawowy.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowy >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[\<losowy >](../standard-library/random.md)<br/>
