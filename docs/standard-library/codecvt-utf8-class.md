---
title: "codecvt_utf8 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: codecvt/std::codecvt_utf8
dev_langs: C++
helpviewer_keywords: codecvt_utf8 class
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: da936d5a454557ef0a5934472b329cf60df66b41
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
