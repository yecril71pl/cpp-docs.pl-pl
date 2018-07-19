---
title: codecvt_utf8 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- codecvt/std::codecvt_utf8
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf8 class
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c0230c92a448eedf0cae7c80778c2bd4c48d077
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963170"
---
# <a name="codecvtutf8"></a>codecvt_utf8

Reprezentuje [ustawień regionalnych](../standard-library/locale-class.md) reguł, który wykonuje konwersję między zakodowanymi w formacie UCS-2 lub UCS-4 znaki dwubajtowe, a strumień bajtów zakodowanymi w formacie UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

*Elem* typ elementu znaków dwubajtowych.
*Maxcode* maksymalną liczbę znaków dla zestawu reguł ustawień regionalnych.
*Tryb* informacje o konfiguracji dla zestawu reguł ustawień regionalnych.

## <a name="remarks"></a>Uwagi

Strumień bajtów można zapisać do pliku binarnego lub pliku tekstowego.

## <a name="requirements"></a>Wymagania

Nagłówek: <codecvt> Namespace: standardowe
