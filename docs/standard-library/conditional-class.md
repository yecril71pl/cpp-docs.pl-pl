---
title: "Conditional — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::conditional
dev_langs: C++
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 08c0428f5ed82c0890cdbcbb051f128c52281ce7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="conditional-class"></a>conditional — Klasa
Wybiera jeden z dwóch typów, w zależności od określonego warunku.  
  
## <a name="syntax"></a>Składnia  
  
```
template <bool B, class T1, class T2>  
struct conditional;

template <bool _Test, class _T1, class _T2>  
using conditional_t = typename conditional<_Test, _T1, _T2>::type;
```  
  
#### <a name="parameters"></a>Parametry  
 `B`  
 Wartość, która określa wybrany typ.  
  
 `T1`  
 Wynik typu, jeśli B ma wartość true.  
  
 `T2`  
 Wynik typu, gdy B ma wartość false.  
  
## <a name="remarks"></a>Uwagi  
 Element typedef elementu członkowskiego szablonu `conditional<B, T1, T2>::type` daje w wyniku `T1` podczas `B` daje w wyniku `true`i daje w wyniku `T2` podczas `B` daje w wyniku `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)



