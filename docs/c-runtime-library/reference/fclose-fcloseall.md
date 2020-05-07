---
title: fclose, _fcloseall
ms.date: 4/2/2020
api_name:
- fclose
- _fcloseall
- _o__fcloseall
- _o_fclose
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fclose
- _fcloseall
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: 3f8567f7bb01c519938f5a4e28bbb33bce09dffe
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920225"
---
# <a name="fclose-_fcloseall"></a>fclose, _fcloseall

Zamyka strumień (**fclose**) lub zamyka wszystkie otwarte strumienie (**_fcloseall**).

## <a name="syntax"></a>Składnia

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>Parametry

*produkcyjne*<br/>
Wskaźnik do struktury **pliku** .

## <a name="return-value"></a>Wartość zwracana

**fclose** zwraca wartość 0, jeśli strumień został pomyślnie zamknięty. **_fcloseall** zwraca łączną liczbę zamkniętych strumieni. Obie funkcje zwracają **znacznik EOF** , aby wskazać błąd.

## <a name="remarks"></a>Uwagi

Funkcja **fclose** zamknie *strumień*. Jeśli *strumień* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **fclose** ustawia **errno** na **EINVAL** i zwraca **znacznik EOF**. Zaleca się, aby wskaźnik *strumienia* zawsze był sprawdzany przed wywołaniem tej funkcji.

Aby uzyskać więcej informacji na temat tych i innych kodów błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

Funkcja **_fcloseall** zamyka wszystkie otwarte strumienie z wyjątkiem **stdin**, **stdout**, **stderr** (i w systemie MS-DOS, **_stdaux** i **_stdprn**). Powoduje także zamknięcie i usunięcie wszystkich plików tymczasowych utworzonych przez **tmpfile**. W obu funkcjach wszystkie bufory skojarzone ze strumieniem są opróżniane przed zamknięciem. Bufory przydzieloną systemowo są wydawane, gdy strumień jest zamknięty. Bufory przypisane przez użytkownika z **setbuf** i **setvbuf —** nie są automatycznie wydawane.

**Uwaga:** Gdy te funkcje są używane do zamykania strumienia, podstawowy deskryptor pliku i dojście do pliku systemu operacyjnego (lub gniazdo) są zamknięte, a także strumień. W takim przypadku, jeśli plik był pierwotnie otwarty jako dojście do pliku lub deskryptor pliku i jest zamykany przy użyciu **fclose**, nie należy również wywoływać **_close** , aby zamknąć deskryptor pliku; Nie wywołuj funkcji **CloseHandle** programu Win32, aby zamknąć dojście do pliku.

**fclose** i **_fcloseall** zawierają kod chroniący przed zakłóceniami z innych wątków. W przypadku nieblokującej wersji **fclose**należy zapoznać się z tematem **_fclose_nolock**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fclose**|\<stdio. h>|
|**_fcloseall**|\<stdio. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład dla [fopen](fopen-wfopen.md).

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
