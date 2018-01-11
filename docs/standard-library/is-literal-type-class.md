---
title: Klasa is_literal_type | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_literal_type
dev_langs: C++
helpviewer_keywords: is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aabb7d1c6e0c194f5d031e62d84753dfc0ded3d2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="isliteraltype-class"></a>is_literal_type — klasa
Sprawdza, czy typ mogą być używane jako `constexpr` zmiennej lub skonstruowany, używany przez lub zwrócony z `constexpr` funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
struct is_literal_type;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest *literalne*, w przeciwnym razie ma wartość false. Jest typem literału, albo `void`, typem skalarnym, typu odwołania, tablicy typu literału lub typie klasy literałów. Typie klasy literałów jest typem klasy, który ma destruktor trivial, jest łączny typu lub ma co najmniej jeden z systemem innym niż z move bez kopiowania `constexpr` Konstruktor i wszystkie jej klasy podstawowe i elementy członkowskie danych niestatyczna są trwałej typy literału. Typ literału zawsze jest typem literału, koncepcja literału typu obejmuje wszystkie elementy, które kompilator może służyć do oceny jako `constexpr` w czasie kompilacji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [<type_traits>](../standard-library/type-traits.md)



