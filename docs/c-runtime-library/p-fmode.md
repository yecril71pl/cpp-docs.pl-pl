---
title: __p__fmode
ms.date: 4/2/2020
api_name:
- __p__fmode
- _o___p__fmode
api_location:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__fmode
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
ms.openlocfilehash: aecba640099719f90db8bbd5dbe386ea99aae45d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349249"
---
# <a name="__p__fmode"></a>__p__fmode

Wskazuje zmienną globalną, `_fmode` która określa domyślny tryb *translacji plików* dla operacji we/wy pliku.

## <a name="syntax"></a>Składnia

```cpp
int* __p__fmode(
   );
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do `_fmode` zmiennej globalnej.

## <a name="remarks"></a>Uwagi

Funkcja `__p__fmode` jest tylko do użytku wewnętrznego i nie powinny być wywoływane z kodu użytkownika.

Tryb tłumaczenia plików `binary` określa `text` albo tłumaczenie dla [_open](../c-runtime-library/reference/open-wopen.md) i [_pipe](../c-runtime-library/reference/pipe.md) operacji we/wy. Aby uzyskać więcej informacji, zobacz [_fmode](../c-runtime-library/fmode.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|__p\__fmode|stdlib.h|
