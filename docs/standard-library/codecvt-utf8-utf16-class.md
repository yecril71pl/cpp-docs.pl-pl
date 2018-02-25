---
title: codecvt_utf8_utf16 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- codecvt/std::cvt_utf8_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 83f67c9d410aeca92c343c8e598fa9db4b7c59ae
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16
Reprezentuje [ustawień regionalnych](../standard-library/locale-class.md) aspekt, który wykonuje konwersję między znaki dwubajtowe zakodowane jako UTF-16, a strumień bajtów zakodowane jako UTF-8.

```
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

`Elem`  
Typ elementu znaków dwubajtowych.  
`Maxcode`  
Maksymalna liczba znaków aspekt ustawień regionalnych.  
`Mode`  
Informacje o konfiguracji aspekt ustawień regionalnych.  

## <a name="remarks"></a>Uwagi

Strumień bajtów można zapisać pliku binarnego lub pliku tekstowego.  

## <a name="requirements"></a>Wymagania

Nagłówek: <codecvt> Namespace: Standard
