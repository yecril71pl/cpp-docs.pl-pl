---
title: Klasa is_trivially_constructible | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::is_trivially_constructible
dev_langs: C++
helpviewer_keywords: is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0a01ee89c1bb07ab0ca3c9c54161b7d9a3097be3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible — klasa
Sprawdza, czy typ jest trivially umożliwia konstrukcji, gdy określone typy argumentów są używane.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T, class... Args>  
struct is_trivially_constructible;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do zapytania.  
  
 `Args`  
 Typy argumentów do dopasowania w konstruktora `T`.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest trivially umożliwia konstrukcji, korzystając z typami argumentów w `Args`, w przeciwnym razie ma wartość false. Typ `T` trivially umożliwia konstrukcji Jeśli definicja zmiennej `T t(std::declval<Args>()...);` jest poprawnie sformułowany i jest rozpoznawany do wywołania ma nieuproszczone operacji. Zarówno `T` i wszystkie typy w `Args` musi być ukończone typy `void`, lub tablic z nieznanym powiązaniem.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [<type_traits>](../standard-library/type-traits.md)



