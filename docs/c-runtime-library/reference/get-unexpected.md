---
title: _get_unexpected — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _get_unexpected
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
- __get_unexpected
- _get_unexpected
- get_unexpected
dev_langs:
- C++
helpviewer_keywords:
- __get_unexpected function
- get_unexpected function
- _get_unexpected function
ms.assetid: a5f7a7a0-18e0-485e-953d-db291068a1e8
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd09620868f4a8a1c4f1511124dce9c871253e13
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="getunexpected"></a>_get_unexpected

Zwraca procedury zakończenia, który ma zostać wywołana przez **nieoczekiwany**.

## <a name="syntax"></a>Składnia

```C
unexpected_function _get_unexpected( void );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do funkcji zarejestrowany przez [set_unexpected —](set-unexpected-crt.md). Jeśli nie ustawiono żadnej funkcji, zwracana wartość może służyć do przywrócić domyślne zachowanie; Ta wartość może mieć wartości NULL.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_unexpected**|\<eh.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[set_terminate —](set-terminate-crt.md)<br/>
[Zakończenie](terminate-crt.md)<br/>
[Nieoczekiwany](unexpected-crt.md)<br/>
