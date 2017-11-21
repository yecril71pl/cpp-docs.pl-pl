---
title: Klasa is_trivially_copy_assignable | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_trivially_copy_assignable
dev_langs: C++
helpviewer_keywords: is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bfb7ce01e8d20f1accc30d09e24f84a7f059e8b1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [< type_traits >](../standard-library/type-traits.md)



