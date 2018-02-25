---
title: Klasa is_move_assignable | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1003b77fcca3a5b0f6840f53d353c882e45a5ef3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ismoveassignable-class"></a>is_move_assignable — klasa
Testy, jeśli typ można przenieść przypisane.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>
struct is_move_assignable;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Typ jest przeniesienie można przypisać, jeśli odwołania do r-wartości na typ można przypisać do odwołania do typu. Predykat typów jest odpowiednikiem `is_assignable<T&, T&&>`. Przenieś można przypisać typy referenceable typów skalarnych i operatory przypisania przenoszenia typy klas, którzy generowane przez kompilator lub zdefiniowanej przez użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [<type_traits>](../standard-library/type-traits.md)



