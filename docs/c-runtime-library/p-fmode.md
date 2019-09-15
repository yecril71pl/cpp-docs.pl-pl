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
ms.openlocfilehash: 6f7676fc5c9958be3d0567e6bf22a11367094150
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939986"
---
# <a name="__p__fmode"></a>__p__fmode

Wskazuje na `_fmode` zmienną globalną, która określa domyślny *tryb tłumaczenia plików* dla operacji we/wy pliku.

## <a name="syntax"></a>Składnia

```cpp
int* __p__fmode(
   );
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik na `_fmode` zmienną globalną.

## <a name="remarks"></a>Uwagi

`__p__fmode` Funkcja jest tylko do użytku wewnętrznego i nie powinna być wywoływana z kodu użytkownika.

Tryb tłumaczenia plików określa albo `binary` `text` tłumaczenie dla operacji we/wy [_open](../c-runtime-library/reference/open-wopen.md) i [_pipe](../c-runtime-library/reference/pipe.md) . Aby uzyskać więcej informacji, zobacz [_fmode](../c-runtime-library/fmode.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|__p\__fmode|stdlib.h|