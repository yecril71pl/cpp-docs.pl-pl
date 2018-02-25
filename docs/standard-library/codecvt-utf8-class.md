---
title: codecvt_utf8 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- codecvt/std::codecvt_utf8
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf8 class
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e211d58843b365610a674500afa3b713b37d7a2c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="codecvtutf8"></a>codecvt_utf8
Reprezentuje [ustawień regionalnych](../standard-library/locale-class.md) aspekt, który wykonuje konwersję między znaki dwubajtowe zakodowane jako UCS 2 lub UCS 4 i strumień bajtów zakodowane jako UTF-8.

```
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>
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
