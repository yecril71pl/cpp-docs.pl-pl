---
title: Klasa is_move_assignable | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_move_assignable
dev_langs: C++
helpviewer_keywords: is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9fba36cfb8b23a804a6851810294b54bf65c5055
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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



