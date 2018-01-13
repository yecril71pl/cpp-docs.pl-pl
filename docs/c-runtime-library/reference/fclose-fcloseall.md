---
title: "fclose —, _fcloseall — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fclose
- _fcloseall
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
- fclose
- _fcloseall
dev_langs: C++
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2d670ead8214f54323cf9f6b284eaaef9a582757
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fclose-fcloseall"></a>fclose, _fcloseall
Zamyka strumienia (`fclose`) lub zamyka wszystkie otwarte strumieni (`_fcloseall`).  
  
## <a name="syntax"></a>Składnia  
  
```  
int fclose(   
   FILE *stream   
);  
int _fcloseall( void );  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 `fclose`Zwraca wartość 0, jeśli strumień jest zamknięty pomyślnie. `_fcloseall`Zwraca łączną liczbę strumieni, zamknięty. Obie funkcje zwracają `EOF` wystąpił błąd.  
  
## <a name="remarks"></a>Uwagi  
 `fclose` Funkcji zamknięciu `stream`. Jeśli `stream` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `fclose` ustawia `errno` do `EINVAL` i zwraca `EOF`. Zalecane jest `stream` wskaźnika zawsze można sprawdzić przed wywołaniem tej funkcji.  
  
 Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędów.  
  
 `_fcloseall` Funkcji spowoduje zamknięcie wszystkich otwartych strumieni z wyjątkiem `stdin`, `stdout`, `stderr` (i w MS-DOS, `_stdaux` i `_stdprn`). Również zamyka i usuwa wszystkie tymczasowe pliki tworzone przez `tmpfile`. W obu tych funkcji wszystkie bufory skojarzone z strumienia są opróżniany przed zamknięciem. Bufory przydzielone systemu są wydawane, gdy strumień jest zamknięty. Bufory przypisanego przez użytkownika z `setbuf` i `setvbuf` nie są zwalniane automatycznie.  
  
 **Uwaga:** w przypadku używania tych funkcji można zamknąć strumienia deskryptorów plików i systemu operacyjnego dojście do pliku (lub podstawowej gniazda) są zamknięte, a także strumień. W związku z tym jeśli pierwotnie został otwarty plik jako plik obsługi lub pliku deskryptora i są zamknięte `fclose`, czy nie również wywołania `_close` do zamknąć deskryptorów plików; nie należy wywoływać funkcji Win32 `CloseHandle` zamknąć dojście do pliku.  
  
 `fclose`i `_fcloseall` zawiera kod, aby zapewnić ochronę przed zakłóceniami z innych wątków. Dla wersji — blokowanie z `fclose`, zobacz `_fclose_nolock`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`fclose`|\<stdio.h >|  
|`_fcloseall`|\<stdio.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [fopen —](../../c-runtime-library/reference/fopen-wfopen.md).  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [_zamknij](../../c-runtime-library/reference/close.md)   
 [_fdopen —, _wfdopen —](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fflush —](../../c-runtime-library/reference/fflush.md)   
 [fopen —, _wfopen —](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, _wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)