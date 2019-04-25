---
title: nothrow_t — Struktura
ms.date: 11/04/2016
f1_keywords:
- nothrow_t
helpviewer_keywords:
- nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
ms.openlocfilehash: 2313c436a1fd25149fa7ea72f122a6f323b40028
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223626"
---
# <a name="nothrowt-structure"></a>nothrow_t — Struktura

Struktura służy jako parametru funkcji, operatorów nowych do wskazania, że funkcja powinna zwrócić wskaźnik o wartości null do raportu wystąpił błąd alokacji, a nie zgłasza wyjątku.

## <a name="syntax"></a>Składnia

```cpp
struct std::nothrow_t {};
```

## <a name="remarks"></a>Uwagi

Struktura pomaga kompilatora, aby wybrać poprawną wersję konstruktora. [nothrow](../standard-library/new-functions.md#nothrow) jest synonimem dla obiektów typu `std::nothrow_t`.

## <a name="example"></a>Przykład

Zobacz [nowy operator](../standard-library/new-operators.md#op_new) i [nowy operator&#91; &#93; ](../standard-library/new-operators.md#op_new_arr) przykładów dotyczących sposobów `std::nothrow_t` jest używany jako parametr funkcji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<nowe >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
