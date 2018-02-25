---
title: Klasa is_trivially_copy_assignable | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c8fe1f72d609c30dbd7abf9fb0d0ca6803d90a29
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable — klasa
Sprawdza, czy typ ma operatora przypisania kopii prosta.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Ty>
struct is_trivially_copy_assignable;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest klasa, która ma trivial operatora przypisania kopii, w przeciwnym razie posiada wartość false.  
  
 Konstruktor przypisania dla klasy `T` jest proste, jeśli jest niejawnie podany, klasa `T` ma żadnych funkcji wirtualnych klasy `T` ma nie wirtualnych typów podstawowych, klas wszystkich członków danych niestatycznych typu klasy mają prosta Operatory przypisania i klasy wszystkich członków danych niestatycznych tablicy typu klasy mają operatory przypisania prosta.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [<type_traits>](../standard-library/type-traits.md)



