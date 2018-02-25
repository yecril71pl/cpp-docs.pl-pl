---
title: "is_trivially_default_constructible — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd0b63b1f088eadf2ba2a253083d0f2878c2b751
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible — klasa
Testy, jeśli typ ma konstruktora domyślnego prosta.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Ty>
struct is_trivially_default_constructible;
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` jest klasa, która ma trivial Konstruktor, w przeciwnym razie posiada wartość false.  
  
 Domyślny konstruktor dla klasy `Ty` jest prosta jeśli:  
  
-   jest niejawnie zadeklarowany Konstruktor domyślny  
  
-   Klasa `Ty` ma żadnych funkcji wirtualnych  
  
-   Klasa `Ty` ma nie wirtualnych typów podstawowych  
  
-   wszystkie bezpośrednio podstawowych klasy `Ty` mieć konstruktorów prosta  
  
-   klasy wszystkich członków danych niestatycznych typu klasy mają trivial konstruktorów  
  
-   klasy wszystkich członków danych niestatycznych tablicy typu klasy mają trivial konstruktorów  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [<type_traits>](../standard-library/type-traits.md)



