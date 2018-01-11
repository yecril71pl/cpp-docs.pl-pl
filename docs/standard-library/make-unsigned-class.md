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
ms.workload: cplusplus
ms.openlocfilehash: ea6150163c63378ed131db3c97e879b89aba9556
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
 [<type_traits>](../standard-library/type-traits.md)



