---
title: '&lt;system_error&gt;'
ms.date: 03/15/2019
f1_keywords:
- <system_error>
- system_error
helpviewer_keywords:
- system_error header
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
ms.openlocfilehash: 4365f0aaf8fdd4d43159b78acf6dcffa4fcbe428
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246546"
---
# <a name="ltsystemerrorgt"></a>&lt;system_error&gt;

Dołącz nagłówek \<system_error > Aby zdefiniować klasę wyjątku `system_error` i powiązane szablony na potrzeby przetwarzania błędy niskiego poziomu systemu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<system_error >

**Namespace:** standardowe

## <a name="members"></a>Elementy członkowskie

### <a name="objects"></a>Obiekty

|||
|-|-|
|[generic_category](../standard-library/system-error-functions.md#generic_category)|Reprezentuje kategorię dla ogólnych błędów.|
|[is_error_code_enum_v](../standard-library/system-error-functions.md#is_error_code_enum_v)||
|[is_error_condition_enum_v](../standard-library/system-error-functions.md#is_error_condition_enum_v)||
|[system_category](../standard-library/system-error-functions.md#system_category)|Reprezentuje kategorię dla błędów spowodowanych przez system niskiego poziomu przepełnienia.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[make_error_code](../standard-library/system-error-functions.md#make_error_code)|Tworzy `error_code` obiektu.|
|[make_error_condition](../standard-library/system-error-functions.md#make_error_condition)|Tworzy `error_condition` obiektu.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator==](../standard-library/system-error-operators.md#op_eq_eq)|Sprawdza, czy obiekt po lewej stronie operatora jest równy obiektowi po prawej stronie.|
|[operator!=](../standard-library/system-error-operators.md#op_neq)|Sprawdza, czy obiekt po lewej stronie operatora nie jest równy obiektowi po prawej stronie.|
|[Operator <](../standard-library/system-error-operators.md#op_lt)|Sprawdza, czy obiekt jest mniejszy niż obiekt przekazany do porównania.|
|[Operator <<](../standard-library/system-error-operators.md#op_ostream)||

### <a name="enums"></a>Wyliczenia

|||
|-|-|
|[errc —](../standard-library/system-error-enums.md#errc)|Dostarcza symbolicznych nazw dla wszystkich makr kod błędu zdefiniowany przez Posix w `<errno.h>`.|

### <a name="classes-and-structs"></a>Klasy i struktury

|||
|-|-|
|[error_category](../standard-library/error-category-class.md)|Reprezentuje podstawę abstrakcyjne, wspólne dla obiektów opisująca kategorię kody błędów.|
|[error_code —](../standard-library/error-code-class.md)|Reprezentuje błędy niskiego poziomu systemu, które są specyficzne dla implementacji.|
|[error_condition —](../standard-library/error-condition-class.md)|Reprezentuje kody błędów zdefiniowanych przez użytkownika.|
|[Skrót](../standard-library/hash-structure.md#system_error)||
|[is_error_code_enum](../standard-library/is-error-code-enum-class.md)|Reprezentuje typu predykatu, który sprawdza, czy [error_code — klasa](../standard-library/error-code-class.md) wyliczenia.|
|[is_error_condition_enum](../standard-library/is-error-condition-enum-class.md)|Reprezentuje typu predykatu, który sprawdza, czy [error_condition — klasa](../standard-library/error-condition-class.md) wyliczenia.|
|[system_error](../standard-library/system-error-class.md)|Reprezentuje klasę bazową dla wszystkich wyjątków generowanych do zgłaszania przepełnienie system niskiego poziomu.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
