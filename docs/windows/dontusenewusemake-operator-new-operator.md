---
title: DontUseNewUseMake::operator nowy Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs:
- C++
helpviewer_keywords:
- operator new operator
ms.assetid: 6af07a0d-2271-430c-9d9b-5a4223fed049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9785ea27c79ff0a118ff3697a22804c520b265ee
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873683"
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
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)