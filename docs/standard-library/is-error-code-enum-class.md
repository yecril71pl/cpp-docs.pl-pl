---
title: "is_error_code_enum — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: system_error/std::is_error_code_enum
dev_langs: C++
helpviewer_keywords: is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 56f402c938d3e481e9d859d66f383b5f8886df61
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="iserrorcodeenum-class"></a>is_error_code_enum — Klasa
Reprezentuje predykat typów, które sprawdza, czy [error_code —](../standard-library/error-code-class.md) wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```
template <_Enum>
class is_error_code_enum;
```  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie tego elementu [predykatu typów](../standard-library/type-traits.md) blokad wartość true, jeśli typ `_Enum` jest wartością wyliczenia odpowiedniego do przechowywania w obiekcie typu `error_code`.  
  
 Jest dozwolone, aby dodać specjalizacje do tego typu dla typów zdefiniowanych przez użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<system_error — >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [<system_error>](../standard-library/system-error.md)



