---
title: codecvt_utf8_utf16 — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- codecvt/std::cvt_utf8_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6fba4925b6392969aceb1c00ac4c0f4e47b3b63a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16

Reprezentuje [ustawień regionalnych](../standard-library/locale-class.md) aspekt, który wykonuje konwersję między znaki dwubajtowe zakodowane jako UTF-16, a strumień bajtów zakodowane jako UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

`Elem` Typ elementu znaków dwubajtowych.
`Maxcode` Maksymalna liczba znaków aspekt ustawień regionalnych.
`Mode` Informacje o konfiguracji aspekt ustawień regionalnych.

## <a name="remarks"></a>Uwagi

Strumień bajtów można zapisać pliku binarnego lub pliku tekstowego.

## <a name="requirements"></a>Wymagania

Nagłówek: <codecvt> Namespace: Standard
