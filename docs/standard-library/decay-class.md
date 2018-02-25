---
title: "decay — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::decay
dev_langs:
- C++
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d43ee8ff7971af3026066b3483de4808ec2dc114
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="decay-class"></a>decay — Klasa
Tworzy typ jako przekazany przez wartość. Sprawia, że typem referencyjnym, wartością stałą, trwałej lub sprawia, że wskaźnik do typu z funkcją lub typem tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>
struct decay;

template <class T>  
using decay_t = typename decay<T>::type;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do modyfikacji.  
  
## <a name="remarks"></a>Uwagi  
 Szablon zanikania wygenerowało wynikowy typ tak, jakby typ został przekazany przez wartość jako argument. Typedef elementu członkowskiego szablonu klasy `type` zawiera typ zmodyfikowane, który jest zdefiniowany w następujących etapach:  
  
-   Typ `U` jest zdefiniowany jako `remove_reference<T>::type`.  
  
-   Jeśli `is_array<U>::value` ma wartość true, zmodyfikowany typ `type` jest `remove_extent<U>::type *`.  
  
-   W przeciwnym razie, jeśli `is_function<U>::value` ma wartość true, zmodyfikowany typ `type` jest `add_pointer<U>::type`.  
  
-   W przeciwnym razie zmodyfikowany typ `type` jest `remove_cv<U>::type`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [<type_traits>](../standard-library/type-traits.md)



