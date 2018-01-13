---
title: "is_nothrow_move_constructible — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_nothrow_move_constructible
dev_langs: C++
helpviewer_keywords: is_nothrow_move_constructible
ms.assetid: d186d97b-7b89-470a-8d30-993046a83379
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e69d49204e4ab933d1dca10030701b1353b94a03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="isnothrowmoveconstructible-class"></a>is_nothrow_move_constructible — klasa
Sprawdza, czy typ ma **nothrow** przenoszenie konstruktora.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Ty>
struct is_nothrow_move_constructible;
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` ma nothrow Konstruktor przenoszący, w przeciwnym razie posiada wartość false.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [<type_traits>](../standard-library/type-traits.md)




