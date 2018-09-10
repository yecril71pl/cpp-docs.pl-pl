---
title: discard_block_engine — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::discard_block_engine
dev_langs:
- C++
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c9620003c1f57af966628dda2a5a0ab8352c6d2
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107331"
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
