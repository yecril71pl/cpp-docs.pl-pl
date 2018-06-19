---
title: nothrow_t — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- nothrow_t
dev_langs:
- C++
helpviewer_keywords:
- nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a34d9b4e87e2a9036afe7dc12b85fa6d4354209
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852640"
---
# <a name="nothrowt-structure"></a>nothrow_t — Struktura

Struktury jest używany jako parametr funkcji operatora nowe wskazująca, że funkcja powinna zwrócić pustego wskaźnika, aby zgłosić błąd alokacji, zamiast zgłosić wyjątek.

## <a name="syntax"></a>Składnia

```cpp
struct std::nothrow_t {};
```

## <a name="remarks"></a>Uwagi

Struktura pomaga kompilator, aby wybrać prawidłową wersję konstruktora. [nothrow](../standard-library/new-functions.md#nothrow) jest synonimem dla obiektów typu `std::nothrow_t`.

## <a name="example"></a>Przykład

Zobacz [nowy operator](../standard-library/new-operators.md#op_new) i [nowy operator&#91; &#93; ](../standard-library/new-operators.md#op_new_arr) przykłady `std::nothrow_t` jest używany jako parametr funkcji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<nowy >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
