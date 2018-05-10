---
title: system_error — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- system_error/std::system_error
dev_langs:
- C++
helpviewer_keywords:
- system_error class
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bde8e448d54be41516e65969f60b0651cacc8ef1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="systemerror-class"></a>system_error — Klasa

Reprezentuje klasę podstawową dla wszystkich wyjątków zgłoszonych zgłosić błąd systemowy niskiego poziomu.

## <a name="syntax"></a>Składnia

```cpp
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

## <a name="see-also"></a>Zobacz także

[<system_error>](../standard-library/system-error.md)<br/>
