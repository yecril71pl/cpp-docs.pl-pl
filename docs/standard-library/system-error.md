---
title: '&lt;system_error&gt;'
ms.date: 03/15/2019
f1_keywords:
- <system_error>
- system_error
helpviewer_keywords:
- system_error header
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
ms.openlocfilehash: e6eef7152e45e8177c451fc25592fab85c58ccb5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449753"
---
# <a name="ltsystemerrorgt"></a>&lt;system_error&gt;

Dołącz nagłówek \<system_error >, aby zdefiniować klasę `system_error` wyjątku i powiązane szablony służące do przetwarzania błędów systemu niskiego poziomu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<system_error >

**Przestrzeń nazw:** std

## <a name="members"></a>Elementy członkowskie

### <a name="objects"></a>Obiekty

|||
|-|-|
|[generic_category](../standard-library/system-error-functions.md#generic_category)|Przedstawia kategorię błędów ogólnych.|
|[is_error_code_enum_v](../standard-library/system-error-functions.md#is_error_code_enum_v)||
|[is_error_condition_enum_v](../standard-library/system-error-functions.md#is_error_condition_enum_v)||
|[system_category](../standard-library/system-error-functions.md#system_category)|Reprezentuje kategorię błędów spowodowanych przepełnieniem systemu niskiego poziomu.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[make_error_code](../standard-library/system-error-functions.md#make_error_code)|Tworzy `error_code` obiektu.|
|[make_error_condition](../standard-library/system-error-functions.md#make_error_condition)|Tworzy `error_condition` obiektu.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator==](../standard-library/system-error-operators.md#op_eq_eq)|Testuje, czy obiekt po lewej stronie operatora jest równy obiektowi po prawej stronie.|
|[operator!=](../standard-library/system-error-operators.md#op_neq)|Testuje, czy obiekt po lewej stronie operatora nie jest równy obiektowi po prawej stronie.|
|[< operatora](../standard-library/system-error-operators.md#op_lt)|Sprawdza, czy obiekt jest mniejszy niż obiekt przekazany do porównania.|
|[< operatora <](../standard-library/system-error-operators.md#op_ostream)||

### <a name="enums"></a>Wyliczenia

|||
|-|-|
|[ERRC —](../standard-library/system-error-enums.md#errc)|Zawiera nazwy symboliczne dla wszystkich makr kodu błędu zdefiniowanych przez POSIX w `<errno.h>`.|

### <a name="classes-and-structs"></a>Klasy i struktury

|||
|-|-|
|[error_category](../standard-library/error-category-class.md)|Reprezentuje abstrakcyjną, popularną bazę dla obiektów, która opisuje kategorię kodów błędów.|
|[error_code](../standard-library/error-code-class.md)|Reprezentuje błędy systemu niskiego poziomu, które są specyficzne dla implementacji.|
|[error_condition](../standard-library/error-condition-class.md)|Reprezentuje kody błędów zdefiniowane przez użytkownika.|
|[skrótu](../standard-library/hash-structure.md#system_error)||
|[is_error_code_enum](../standard-library/is-error-code-enum-class.md)|Reprezentuje predykat typu, który testuje Wyliczenie [klasy error_code](../standard-library/error-code-class.md) .|
|[is_error_condition_enum](../standard-library/is-error-condition-enum-class.md)|Reprezentuje predykat typu, który testuje Wyliczenie [klasy error_condition](../standard-library/error-condition-class.md) .|
|[system_error](../standard-library/system-error-class.md)|Reprezentuje klasę bazową dla wszystkich wyjątków zgłoszonych w celu zgłaszania przepełnienia systemu niskiego poziomu.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
