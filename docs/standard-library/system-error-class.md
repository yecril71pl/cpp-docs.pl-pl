---
title: system_error — Klasa
ms.date: 11/04/2016
f1_keywords:
- system_error/std::system_error
helpviewer_keywords:
- system_error class
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
ms.openlocfilehash: bad260e5372965c35517986da8feb2cfa3c0e1d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412231"
---
# <a name="systemerror-class"></a>system_error — Klasa

Reprezentuje klasę bazową dla wszystkich wyjątków generowanych, aby zgłosić błąd systemowy niskiego poziomu.

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

Wartość zwrócona przez obiekt `what` w klasie [wyjątek](../standard-library/exception-class.md) jest zbudowany z `_Message` i przechowywany obiekt typu [error_code](../standard-library/error-code-class.md) (albo `code` lub `error_code(_Errval, _Errcat)`).

Funkcja elementu członkowskiego `code` zwraca przechowywaną [error_code](../standard-library/error-code-class.md) obiektu.

## <a name="requirements"></a>Wymagania

**Header:** \<system_error>

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<system_error>](../standard-library/system-error.md)<br/>
