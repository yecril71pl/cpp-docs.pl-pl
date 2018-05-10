---
title: '&lt;system_error —&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
helpviewer_keywords:
- std::generic_category
- std::make_error_code
- std::make_error_condition
- std::system_category
ms.openlocfilehash: 6135a3dc51b372c85545f01f52c70cbc6f236e64
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltsystemerrorgt-functions"></a>&lt;system_error —&gt; funkcji

||||
|-|-|-|
|[generic_category](#generic_category)|[make_error_code](#make_error_code)|[make_error_condition](#make_error_condition)|
|[system_category](#system_category)|

## <a name="generic_category"></a>  generic_category

Reprezentuje kategorię dla ogólnych błędów.

```cpp
extern const error_category& generic_category();
```

### <a name="remarks"></a>Uwagi

`generic_category` Obiektu jest implementacją [error_category —](../standard-library/error-category-class.md).

## <a name="make_error_code"></a>  make_error_code —

Tworzy obiekt kod błędu.

```cpp
error_code make_error_code(generic_errno _Errno);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`_Errno`|Wartość wyliczenia mają być przechowywane w obiekcie kod błędu.|

### <a name="return-value"></a>Wartość zwracana

Obiekt kodu błędu.

### <a name="remarks"></a>Uwagi

## <a name="make_error_condition"></a>  make_error_condition —

Tworzy obiekt warunek błędu.

```cpp
error_condition make_error_condition(generic_errno _Errno);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`_Errno`|Wartość wyliczenia mają być przechowywane w obiekcie warunek błędu.|

### <a name="return-value"></a>Wartość zwracana

Obiekt warunek błędu.

### <a name="remarks"></a>Uwagi

## <a name="system_category"></a>  system_category

Reprezentuje kategorię dla błędów spowodowanych przez system niskiego poziomu przepełnienia.

```cpp
extern const error_category& system_category();
```

### <a name="remarks"></a>Uwagi

`system_category` Obiektu jest implementacją [error_category —](../standard-library/error-category-class.md).

## <a name="see-also"></a>Zobacz także

[<system_error>](../standard-library/system-error.md)<br/>
