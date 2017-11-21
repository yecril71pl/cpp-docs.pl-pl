---
title: DontUseNewUseMake::operator nowy Operator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs: C++
helpviewer_keywords: operator new operator
ms.assetid: 6af07a0d-2271-430c-9d9b-5a4223fed049
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5424108692bd97bdea890aff85ab7428276dd430
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="dontusenewusemakeoperator-new-operator"></a>DontUseNewUseMake::operator nowy operator
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
void* operator new(  
   size_t,  
   _In_ void* placement  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `__unnamed0`  
 Parametr nienazwany określająca liczbę bajtów pamięci do przydzielenia.  
  
 `placement`  
 Typ do przydzielenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zapewnia sposób, aby przekazać dodatkowe argumenty, jeśli przeciążenia operatora `new`.  
  
## <a name="remarks"></a>Uwagi  
 Overloads operator `new` i uniemożliwia użycie w runtimeclass —.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Dontusenewusemake — klasa](../windows/dontusenewusemake-class.md)   
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)