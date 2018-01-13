---
title: "is_lvalue_reference — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_lvalue_reference
dev_langs: C++
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e095638f11ebf34181928d3708de62f8d0cf0289
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="islvaluereference-class"></a>is_lvalue_reference — Klasa
Testy, jeśli typ odwołania do wartości.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Ty>
struct is_lvalue_reference;
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienia tego typu predykatu przechowuje wartość PRAWDA, jeśli typ `Ty` jest odwołaniem do obiektu lub funkcji, w przeciwnym razie posiada wartość false. Należy pamiętać, że `Ty` nie może być odwołaniem wartościowanym prawostronnie. Aby uzyskać więcej informacji o rvalues, zobacz [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)



