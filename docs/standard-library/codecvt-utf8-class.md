---
title: codecvt_utf8
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf8
helpviewer_keywords:
- codecvt_utf8 class
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
ms.openlocfilehash: dcbb34c300d7c15f89c4a882275be0efd68359dc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458713"
---
# <a name="codecvtutf8"></a>codecvt_utf8

Reprezentuje zestaw reguł [ustawień regionalnych](../standard-library/locale-class.md) , który konwertuje między znaki szerokie kodowane jako UCS-2 lub UCS-4, oraz strumień bajtów zakodowany jako UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>
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
