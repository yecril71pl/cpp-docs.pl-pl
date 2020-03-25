---
title: __p__fmode
ms.date: 11/04/2016
api_name:
- __p__fmode
api_location:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__fmode
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
ms.openlocfilehash: 2364a22d52c5bc418e4499a4a639c8e06559063a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171453"
---
# <a name="__p__fmode"></a>__p__fmode

Wskazuje na `_fmode` zmienną globalną, która określa domyślny *tryb tłumaczenia plików* dla operacji we/wy pliku.

## <a name="syntax"></a>Składnia

```cpp
int* __p__fmode(
   );
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do zmiennej globalnej `_fmode`.

## <a name="remarks"></a>Uwagi

Funkcja `__p__fmode` jest używana tylko do użytku wewnętrznego i nie powinna być wywoływana z kodu użytkownika.

Tryb tłumaczenia plików określa `binary` lub `text` translacji dla operacji we/wy [_open](../c-runtime-library/reference/open-wopen.md) i [_pipe](../c-runtime-library/reference/pipe.md) . Aby uzyskać więcej informacji, zobacz [_fmode](../c-runtime-library/fmode.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|__p\__fmode|stdlib.h|
