---
title: srand — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/02/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- srand
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- srand
dev_langs:
- C++
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a01e56159bf4f04f2c8a53f39e3fcd1e7dd450b5
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="srand"></a>srand

Ustawia wartość początkową inicjatora dla generatora liczb pseudolosowych używane przez **rand** funkcji.

## <a name="syntax"></a>Składnia

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>Parametry

*seed* inicjatora dla Generowanie liczb pseudolosowych

## <a name="remarks"></a>Uwagi

**Srand —** funkcja określa punkt początkowy generowania serii liczb pseudolosowych w bieżącym wątku. Aby ponownie zainicjować generatora, aby utworzyć taką samą sekwencję wyników, należy wywołać **srand —** funkcji i używać tego samego *inicjatora* argument ponownie. Wszystkie inne wartości *inicjatora* ustawia generator do innego punktu początkowego pseudolosowych sekwencji. **RAND** pobiera liczb pseudolosowych, które zostały wygenerowane. Wywoływanie **rand** przed wywołaniem dowolnej **srand —** generuje takiej samej kolejności, co wywołanie **srand —** z *inicjatora* przekazany jako 1.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [rand](rand.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
