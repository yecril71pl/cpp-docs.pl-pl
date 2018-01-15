---
title: "is_trivially_default_constructible — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_trivially_default_constructible
dev_langs: C++
helpviewer_keywords: is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6b936e6cfa3557591a5be9ec2cafda36920039c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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



