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
ms.openlocfilehash: 58551874227bde5d158946c7df9c77bcc0ff3ef3
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108349"
---
# <a name="codecvtutf8"></a>codecvt_utf8

Reprezentuje [ustawień regionalnych](../standard-library/locale-class.md) reguł, który wykonuje konwersję między zakodowanymi w formacie UCS-2 lub UCS-4 znaki dwubajtowe, a strumień bajtów zakodowanymi w formacie UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>
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

Nagłówek: \<codecvt > \
Namespace: standardowe
