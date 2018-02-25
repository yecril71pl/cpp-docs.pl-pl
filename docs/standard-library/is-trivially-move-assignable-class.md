---
title: Klasa is_trivially_move_assignable | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 32cfcd78cdc57e9ac0c238a3046d034d5d97f114
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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



