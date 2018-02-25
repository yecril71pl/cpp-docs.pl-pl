---
title: "system_error — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- system_error/std::system_error
dev_langs:
- C++
helpviewer_keywords:
- system_error class
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dfa7927cf8039397f62b7510cdc4a0c84af66cf0
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="systemerror-class"></a>system_error — Klasa
Reprezentuje klasę podstawową dla wszystkich wyjątków zgłoszonych zgłosić błąd systemowy niskiego poziomu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class system_error : public runtime_error {  
public:  
    explicit system_error(error_code _Errcode,
    const string& _Message = "");

    system_error(error_code _Errcode,
    const char *_Message);

    system_error(error_code::value_type _Errval,  
    const error_category& _Errcat,
    const string& _Message);

    system_error(error_code::value_type _Errval,  
    const error_category& _Errcat,
    const char *_Message);
const error_code& code() const throw();
const error_code& code() const throw();

 };  
```  
  
## <a name="remarks"></a>Uwagi  
 Wartość zwrócona przez `what` w klasie [wyjątek](../standard-library/exception-class.md) jest tworzony z `_Message` i przechowywane obiektu typu [error_code —](../standard-library/error-code-class.md) (albo `code` lub `error_code(_Errval, _Errcat)`).  
  
 Funkcja członkowska `code` zwraca zapisana [error_code —](../standard-library/error-code-class.md) obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<system_error — >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [<system_error>](../standard-library/system-error.md)

