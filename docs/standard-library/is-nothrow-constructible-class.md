---
title: Klasa is_nothrow_constructible | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::is_nothrow_constructible
dev_langs: C++
helpviewer_keywords: is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 02698c90714ae530e827d9bfbe6cdc7ce1fd0abf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="isnothrowconstructible-class"></a>is_nothrow_constructible — klasa
Sprawdza, czy typem umożliwia konstrukcji, nie wiadomo throw, gdy określone typy argumentów są używane.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T, class... Args>  
struct is_nothrow_constructible;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do zapytania.  
  
 `Args`  
 Typy argumentów do dopasowania w konstruktora `T`.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest umożliwia konstrukcji, korzystając z typami argumentów w `Args`i Konstruktor jest znana przez kompilator nie throw; w przeciwnym razie ma wartość false. Typ `T` umożliwia konstrukcji Jeśli definicja zmiennej `T t(std::declval<Args>()...);` jest poprawnie sformułowany. Zarówno `T` i wszystkie typy w `Args` musi być ukończone typy `void`, lub tablic z nieznanym powiązaniem.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [<type_traits>](../standard-library/type-traits.md)



