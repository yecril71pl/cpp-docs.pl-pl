---
title: _isatty — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _isatty
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _isatty
dev_langs:
- C++
helpviewer_keywords:
- isatty function
- character device checking
- _isatty function
- checking character devices
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3946ea4751b9ee654bcf24967fc5b109e14ac9b4
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="isatty"></a>_isatty

Określa, czy deskryptorów plików jest skojarzone z urządzeniem znaków.

## <a name="syntax"></a>Składnia

```C
int _isatty( int fd );
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Deskryptorów plików, która odwołuje się do urządzenia, które ma zostać przetestowana.

## <a name="return-value"></a>Wartość zwracana

**_isatty —** zwraca wartość niezerową, jeśli skojarzone z urządzeniem znak deskryptora. W przeciwnym razie **_isatty —** zwraca wartość 0.

## <a name="remarks"></a>Uwagi

**_Isatty —** funkcji określa, czy *fd* jest skojarzony z urządzenia znakowego (terminal, konsoli, drukarki lub portu szeregowego).

Ta funkcja weryfikuje *fd* parametru. Jeśli *fd* wskaźnik nieprawidłowego pliku, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca wartość 0 i zestawy **errno** do **ebadf —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_isatty**|\<io.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_isatty.c
/* This program checks to see whether
* stdout has been redirected to a file.
*/

#include <stdio.h>
#include <io.h>

int main( void )
{
   if( _isatty( _fileno( stdout ) ) )
      printf( "stdout has not been redirected to a file\n" );
   else
      printf( "stdout has been redirected to a file\n");
}
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
stdout has not been redirected to a file
```

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
