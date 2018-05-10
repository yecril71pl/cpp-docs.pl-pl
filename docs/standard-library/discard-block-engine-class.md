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
ms.openlocfilehash: b814f64f340577508add6bf3c0f85ffac0786db7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="discardblockengine-class"></a>discard_block_engine — Klasa

Generuje losowe sekwencji odrzucając wartości zwracanych przez silnik podstawowej.

## <a name="syntax"></a>Składnia

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>Parametry

`Engine` Typ podstawowy aparatu.

`P` **Rozmiaru bloku**. Liczba wartości w każdym bloku.

`R` **Blok używane**. Liczba wartości w każdym bloku, które są używane. Pozostałe zostaną odrzucone ( `P`  -  `R`). **Warunek wstępny**: `0 < R ≤ P`

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|

Aby uzyskać więcej informacji na temat aparatu członków zobacz [ \<losowe >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Ta klasa szablonu opisuje Adapter aparat tworzącego wartości odrzucając niektórych wartości zwracanych przez silnik podstawowej.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[\<losowe >](../standard-library/random.md)<br/>
