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
ms.openlocfilehash: 272e4007c3421613acfecc95fdd9548663dfceeb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719995"
---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16

Reprezentuje [ustawień regionalnych](../standard-library/locale-class.md) reguł, który wykonuje konwersję między zakodowanymi w formacie UTF-16 znaków dwubajtowych i strumień bajtów zakodowanymi w formacie UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

*Elem*<br/>
Typ elementu znaków dwubajtowych.

*Maxcode*<br/>
Maksymalna liczba znaków dla zestawu reguł ustawień regionalnych.

*Tryb*<br/>
Informacje o konfiguracji dla zestawu reguł ustawień regionalnych.

## <a name="remarks"></a>Uwagi

Strumień bajtów można zapisać do pliku binarnego lub pliku tekstowego.

## <a name="requirements"></a>Wymagania

Nagłówek: \<codecvt >

Namespace: standardowe
