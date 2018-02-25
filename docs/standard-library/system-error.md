---
title: '&lt;system_error&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <system_error>
- system_error
dev_langs:
- C++
helpviewer_keywords:
- system_error header
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efd25be1567909effaa25f984acb29bd3f52c529
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltsystemerrorgt"></a>&lt;system_error&gt;
Dołącz nagłówek `<system_error>` do definiowania klasy wyjątku `system_error` i powiązane szablony na potrzeby przetwarzania błędy niskiego poziomu systemu.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <system_error>  
```  
  
### <a name="objects"></a>Obiekty  
  
|||  
|-|-|  
|[generic_category](../standard-library/system-error-functions.md#generic_category)|Reprezentuje kategorię dla ogólnych błędów.|  
|[system_category](../standard-library/system-error-functions.md#system_category)|Reprezentuje kategorię dla błędów spowodowanych przez system niskiego poziomu przepełnienia.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[generic_errno](../standard-library/system-error-typedefs.md#generic_errno)|Typ reprezentujący wyliczenia, którego zawiera nazwy symbolicznej dla makra kod błędu zdefiniowany przez Posix w `<errno.h>`.|  
  
### <a name="functions"></a>Funkcje  
  
|||  
|-|-|  
|[make_error_code](../standard-library/system-error-functions.md#make_error_code)|Tworzy `error_code` obiektu.|  
|[make_error_condition](../standard-library/system-error-functions.md#make_error_condition)|Tworzy `error_condition` obiektu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator==](../standard-library/system-error-operators.md#op_eq_eq)|Testy, jeśli obiekt po lewej stronie operatora jest taki sam jak obiekt po prawej stronie.|  
|[operator!=](../standard-library/system-error-operators.md#op_neq)|Testy, jeśli obiekt po lewej stronie operatora nie jest taki sam jak obiekt po prawej stronie.|  
|[Operator <](../standard-library/system-error-operators.md#op_lt)|Sprawdza, czy obiekt jest mniejszy niż obiekt przekazany do porównania.|  
  
### <a name="enumerations"></a>Wyliczenia  
  
|||  
|-|-|  
|[errc](../standard-library/system-error-enums.md#errc)|Udostępnia nazwy symbolicznej makr kod błędu zdefiniowany przez Posix w `<errno.h>`.|  
  
### <a name="classes-and-structs"></a>Klasy i struktury  
  
|||  
|-|-|  
|[error_category](../standard-library/error-category-class.md)|Reprezentuje podstawę abstrakcyjna, wspólne dla obiektów opisujący kategorii kodów błędów.|  
|[error_code](../standard-library/error-code-class.md)|Reprezentuje błędy systemu niskiego poziomu, które są specyficzne dla wdrożenia.|  
|[error_condition —](../standard-library/error-condition-class.md)|Reprezentuje kody błędów zdefiniowanych przez użytkownika.|  
|[is_error_code_enum](../standard-library/is-error-code-enum-class.md)|Reprezentuje predykat typów, które sprawdza, czy [error_code — klasa](../standard-library/error-code-class.md) wyliczenia.|  
|[is_error_condition_enum](../standard-library/is-error-condition-enum-class.md)|Reprezentuje predykat typów, które sprawdza, czy [error_condition — klasa](../standard-library/error-condition-class.md) wyliczenia.|  
|[system_error](../standard-library/system-error-class.md)|Reprezentuje klasę podstawową dla wszystkich wyjątków zgłaszanych do zgłaszania przepełnienie niskiego poziomu systemu.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<system_error — >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)



