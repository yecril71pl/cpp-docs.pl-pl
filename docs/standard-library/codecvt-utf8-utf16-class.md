---
title: codecvt_utf8_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::cvt_utf8_utf16
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
ms.openlocfilehash: 879ebe6a75d76a84ef4250b95c41e02eccba5517
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458644"
---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16

Reprezentuje zestaw reguł [ustawień regionalnych](../standard-library/locale-class.md) , który konwertuje między znaki szerokie kodowane jako UTF-16 i strumień bajtów zakodowany jako UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

*Elem*\
Typ elementu dwubajtowego.

*Maxcode*\
Maksymalna liczba znaków dla zestawu reguł ustawień regionalnych.

*Wyst*\
Informacje o konfiguracji zestawu reguł ustawień regionalnych.

## <a name="remarks"></a>Uwagi

Strumień bajtów można zapisać w pliku binarnym lub pliku tekstowym.

## <a name="requirements"></a>Wymagania

Nagłówek: \<codecvt >

Przestrzeń nazw: std
