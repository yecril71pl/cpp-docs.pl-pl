---
title: Klasa is_trivially_move_assignable | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_trivially_move_assignable
dev_langs: C++
helpviewer_keywords: is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 267314b73bfdf2d408038836bc3c4eac8e3317ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable — klasa
Sprawdza, czy typ ma operator przypisania przenoszenia prosta.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Ty>
struct is_trivially_move_assignable;
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` jest klasa, która ma trivial operator przypisania przenoszenia, w przeciwnym razie posiada wartość false.  
  
 Operator przypisania przenoszenia, dla klasy `Ty` jest prosta jeśli:  
  
 niejawnie podano  
  
 Klasa `Ty` ma żadnych funkcji wirtualnych  
  
 Klasa `Ty` ma nie wirtualnych typów podstawowych  
  
 klasy wszystkich członków danych niestatycznych typu klasy mają trivial przenoszące operatory przypisania  
  
 klasy wszystkich członków danych niestatycznych tablicy typu klasy mają trivial przenoszące operatory przypisania  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [<type_traits>](../standard-library/type-traits.md)



