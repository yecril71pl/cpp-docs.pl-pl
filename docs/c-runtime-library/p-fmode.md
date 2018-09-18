---
title: __p__fmode | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __p__fmode
apilocation:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- __p__fmode
dev_langs:
- C++
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c4dcea9e3f35bf5fd8dbfbed9273562ac3db551
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056342"
---
# <a name="pfmode"></a>__p__fmode

Wskazuje `_fmode` zmienna globalna, która określa domyślny *tryb tłumaczenia pliku* dla operacji We/Wy pliku.

## <a name="syntax"></a>Składnia

```cpp
int* __p__fmode(
   );
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do `_fmode` zmiennej globalnej.

## <a name="remarks"></a>Uwagi

`__p__fmode` Funkcji jest tylko do użytku wewnętrznego i nie powinna być wywoływana z kodu użytkownika.

Tryb tłumaczenia pliku określa albo `binary` lub `text` Translacja [_otwórz](../c-runtime-library/reference/open-wopen.md) i [_pipe —](../c-runtime-library/reference/pipe.md) operacji We/Wy. Aby uzyskać więcej informacji, zobacz [_fmode](../c-runtime-library/fmode.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|__p\__fmode|stdlib.h|