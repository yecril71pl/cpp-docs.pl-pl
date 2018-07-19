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
ms.openlocfilehash: cdfcf3c6a562f7aab0164e3d63d468ba39ec0023
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954102"
---
# <a name="codecvtutf16"></a>codecvt_utf16

Reprezentuje [ustawień regionalnych](../standard-library/locale-class.md) reguł, który wykonuje konwersję między zakodowanymi w formacie UCS-2 lub UCS-4 znaków dwubajtowych i zakodowanymi w formacie UTF-16LE lub UTF-16BE strumienia bajtów.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

*Elem* typ elementu znaków dwubajtowych.
*Maxcode* maksymalną liczbę znaków dla zestawu reguł ustawień regionalnych.
*Tryb* informacje o konfiguracji dla zestawu reguł ustawień regionalnych.

## <a name="remarks"></a>Uwagi

Konwertuje między zakodowanymi w formacie UCS-2 lub UCS-4 znaków dwubajtowych i strumień bajtów zakodowanymi w formacie UTF-16LE, w tej klasy szablonu, jeśli tryb & little_endian lub UTF-16BE inaczej.

Strumień bajtów powinny być zapisywane w pliku binarnym; mogą zostać uszkodzone, jeśli zapisane do pliku tekstowego.

## <a name="requirements"></a>Wymagania

Nagłówek: \<codecvt > Namespace: standardowe