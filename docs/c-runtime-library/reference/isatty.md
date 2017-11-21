---
title: "_isatty — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _isatty
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
f1_keywords: _isatty
dev_langs: C++
helpviewer_keywords:
- isatty function
- character device checking
- _isatty function
- checking character devices
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 39e8b9520672c676ffec470ab2e89fccdfaf3442
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="isatty"></a>_isatty
Określa, czy deskryptorów plików jest skojarzone z urządzeniem znaków.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int _isatty(  
int fd   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Deskryptorów plików, która odwołuje się do urządzenia, które ma zostać przetestowana.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_isatty`Zwraca wartość niezerową, jeśli skojarzone z urządzeniem znak deskryptora. W przeciwnym razie `_isatty` zwraca wartość 0.  
  
## <a name="remarks"></a>Uwagi  
 `_isatty` Funkcji określa, czy `fd` jest skojarzony z urządzenia znakowego (terminal, konsoli, drukarki lub portu szeregowego).  
  
 Ta funkcja weryfikuje `fd` parametru. Jeśli `fd` wskaźnik nieprawidłowego pliku, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca wartość 0 i zestawy `errno` do `EBADF`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_isatty`|\<IO.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
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
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
stdout has not been redirected to a file  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa plików](../../c-runtime-library/file-handling.md)