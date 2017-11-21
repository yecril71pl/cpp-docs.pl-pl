---
title: "is_rvalue_reference — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_rvalue_reference
dev_langs: C++
helpviewer_keywords:
- is_rvalue_reference class
- is_rvalue_reference
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ce3e2f42eef2ac77e26ea851bac849b2ac2e352b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="isrvaluereference-class"></a>is_rvalue_reference — Klasa
Testy, jeśli typ jest odwołanie do r-wartości.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Ty>
struct is_rvalue_reference;
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienia tego typu predykatu przechowuje wartość PRAWDA, jeśli typ `Ty` jest [odwołania do wartości](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)



