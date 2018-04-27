---
title: Nieoczekiwany (CRT) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- unexpected
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
apitype: DLLExport
f1_keywords:
- unexpected
dev_langs:
- C++
helpviewer_keywords:
- unexpected function
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3fce88dd7b2fdb821fc015130d25e54701c3e467
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="unexpected-crt"></a>nieoczekiwany (CRT)

Wywołania **przerwanie** lub można ją określić za pomocą funkcji **set_unexpected —**.

## <a name="syntax"></a>Składnia

```C
void unexpected( void );
```

## <a name="remarks"></a>Uwagi

**Nieoczekiwany** procedura nie jest używany z bieżąca implementacja C++, obsługa wyjątków. **Nieoczekiwany** wywołania **przerwanie** domyślnie. To zachowanie domyślne można zmienić, pisanie funkcji niestandardowych zakończenia i wywołanie **set_unexpected —** z nazwą funkcji jako jej argument. **Nieoczekiwany** wywołuje ostatniej podany jako argument do funkcji **set_unexpected —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Nieoczekiwany**|\<eh.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate —](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Zakończenie](terminate-crt.md)<br/>
