---
title: "make_unsigned — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::make_unsigned
dev_langs: C++
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c071aebac468e0feeb8e0964fe04527a29140a5a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="makeunsigned-class"></a>make_unsigned — Klasa
Wpisz sprawia, że lub najmniejszą niepodpisanych wpisz większa niż lub równa o rozmiarze do typu.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`T`|Typ do modyfikacji.|  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie modyfikator typu przechowuje zmodyfikowane — typ danych `T` Jeśli `is_unsigned<T>` jest spełniony. W przeciwnym razie jest najmniejszą typu ze znakiem `ST` dla którego `sizeof (T) <= sizeof (ST)`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)



