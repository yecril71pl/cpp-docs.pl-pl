---
title: "make_signed — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::make_signed
dev_langs:
- C++
helpviewer_keywords:
- make_signed class
- make_signed
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 34ed7804d00e6c36d3f71f6b1699e7f9f7654bb3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="makesigned-class"></a>make_signed — Klasa
Wpisz sprawia, że lub najmniejszą podpisem wpisz większa niż lub równa o rozmiarze do typu.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>
struct make_signed;

template <class T>
using make_signed_t = typename make_signed<T>::type;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do modyfikacji.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie modyfikator typu przechowuje zmodyfikowane — typ danych `T` Jeśli `is_signed<T>` jest spełniony. W przeciwnym razie jest najmniejszą typu bez znaku `UT` dla którego `sizeof (T) <= sizeof (UT)`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [<type_traits>](../standard-library/type-traits.md)



