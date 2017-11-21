---
title: "codecvt_utf16 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: codecvt/std::codecvt_utf16
dev_langs: C++
helpviewer_keywords: codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b84e12815483b2d2caff35d024c8efa21d183025
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="codecvtutf16"></a>codecvt_utf16
Reprezentuje [ustawień regionalnych](../standard-library/locale-class.md) aspekt, który wykonuje konwersję między znaki dwubajtowe zakodowane jako UCS 2 lub UCS 4 i strumień bajtów zakodowane jako UTF-16LE lub UTF-16BE.

```
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```
## <a name="parameters"></a>Parametry
`Elem`  
Typ elementu znaków dwubajtowych.  
`Maxcode`  
Maksymalna liczba znaków aspekt ustawień regionalnych.  
`Mode`  
Informacje o konfiguracji aspekt ustawień regionalnych.  

## <a name="remarks"></a>Uwagi
Ta klasa szablonu wykonuje konwersję między znaki dwubajtowe zakodowane jako UCS 2 lub UCS 4 i strumień bajtów zakodowane jako UTF-16LE, jeśli tryb & little_endian lub UTF-16BE w inny sposób.

Strumień bajtów mają być zapisywane w pliku binarnym; może być uszkodzony, jeśli zapisane do pliku tekstowego.

## <a name="requirements"></a>Wymagania
Nagłówek: \<codecvt > Namespace: Standard