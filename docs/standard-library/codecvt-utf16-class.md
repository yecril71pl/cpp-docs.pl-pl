---
title: codecvt_utf16 — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- codecvt/std::codecvt_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa4147f28e7b780e9d916526f0e46e91432fd1ce
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714236"
---
# <a name="codecvtutf16"></a>codecvt_utf16

Reprezentuje [ustawień regionalnych](../standard-library/locale-class.md) reguł, który wykonuje konwersję między zakodowanymi w formacie UCS-2 lub UCS-4 znaków dwubajtowych i zakodowanymi w formacie UTF-16LE lub UTF-16BE strumienia bajtów.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

*Elem*<br/>
Typ elementu znaków dwubajtowych.

*Maxcode*<br/>
Maksymalna liczba znaków dla zestawu reguł ustawień regionalnych.

*Tryb*<br/>
Informacje o konfiguracji dla zestawu reguł ustawień regionalnych.

## <a name="remarks"></a>Uwagi

Konwertuje między zakodowanymi w formacie UCS-2 lub UCS-4 znaków dwubajtowych i strumień bajtów zakodowanymi w formacie UTF-16LE, w tej klasy szablonu, jeśli tryb & little_endian lub UTF-16BE inaczej.

Strumień bajtów powinny być zapisywane w pliku binarnym; mogą zostać uszkodzone, jeśli zapisane do pliku tekstowego.

## <a name="requirements"></a>Wymagania

Nagłówek: \<codecvt >

Namespace: standardowe