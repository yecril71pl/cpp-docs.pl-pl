---
title: fclose —, _fcloseall — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71b98a239cd1a6504611bf436533e7b5fbe1302c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400242"
---
# <a name="fclose-fcloseall"></a>fclose, _fcloseall

Zamyka strumienia (**fclose —**) lub zamyka wszystkie otwarte strumieni (**_fcloseall —**).

## <a name="syntax"></a>Składnia

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>Parametry

*Strumień*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

**fclose —** zwraca wartość 0, jeśli strumień jest zamknięty pomyślnie. **_fcloseall —** zwraca łączną liczbę strumieni, zamknięty. Obie funkcje zwracają **EOF** wystąpił błąd.

## <a name="remarks"></a>Uwagi

**Fclose —** funkcji zamknięciu *strumienia*. Jeśli *strumienia* jest **NULL**, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **fclose —** ustawia **errno** do **einval —** i zwraca **EOF**. Zalecane jest *strumienia* wskaźnika zawsze można sprawdzić przed wywołaniem tej funkcji.

Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędów.

**_Fcloseall —** funkcji spowoduje zamknięcie wszystkich otwartych strumieni z wyjątkiem **stdin**, **stdout**, **stderr** (i w MS-DOS, **_stdaux**  i **_stdprn**). Również zamyka i usuwa wszystkie tymczasowe pliki tworzone przez **tmpfile —**. W obu tych funkcji wszystkie bufory skojarzone z strumienia są opróżniany przed zamknięciem. Bufory przydzielone systemu są wydawane, gdy strumień jest zamknięty. Bufory przypisanego przez użytkownika z **setbuf** i **setvbuf —** nie są zwalniane automatycznie.

**Uwaga:** w przypadku używania tych funkcji można zamknąć strumienia deskryptorów plików i systemu operacyjnego dojście do pliku (lub podstawowej gniazda) są zamknięte, a także strumień. W związku z tym jeśli pierwotnie został otwarty plik jako plik obsługi lub pliku deskryptora i są zamknięte **fclose —**, czy nie również wywołania **_zamknij** do zamknąć deskryptorów plików; nie należy wywoływać funkcji Win32  **Funkcji CloseHandle** zamknąć dojście do pliku.

**fclose —** i **_fcloseall —** zawiera kod, aby zapewnić ochronę przed zakłóceniami z innych wątków. Dla wersji — blokowanie z **fclose —**, zobacz **_fclose_nolock —**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fclose —**|\<stdio.h>|
|**_fcloseall —**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [fopen —](fopen-wfopen.md).

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
