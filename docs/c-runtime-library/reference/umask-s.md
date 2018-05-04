---
title: _umask_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _umask_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- unmask_s
- _umask_s
dev_langs:
- C++
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d45cb3ded6fd2c3d7a380069a7d7f3fd79619810
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="umasks"></a>_umask_s

Ustawia domyślną maskę uprawnień do pliku. Wersja [_umask —](umask.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _umask_s(
   int mode,
   int * pOldMode
);
```

### <a name="parameters"></a>Parametry

*Tryb*<br/>
Domyślne ustawienie uprawnień.

*pOldMode*<br/>
Poprzedniej wartości ustawienia uprawnień.

## <a name="return-value"></a>Wartość zwracana

Zwraca kod błędu, jeśli *tryb* nie określa prawidłowego trybu lub *pOldMode* wskaźnika jest **NULL**.

### <a name="error-conditions"></a>Warunki błędów

|*Tryb*|*pOldMode*|Wartość zwracana|Zawartość *pOldMode*|
|------------|----------------|----------------------|--------------------------------|
|wszystkie|**NULL**|**EINVAL —**|Nie zmodyfikowano|
|Nieprawidłowy tryb|wszystkie|**EINVAL —**|Nie zmodyfikowano|

Jeśli wystąpi jedno z powyższych warunków, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **_umask_s —** zwraca **einval —** i ustawia **errno** do **einval —**.

## <a name="remarks"></a>Uwagi

**_Umask_s —** funkcja ustawia maski uprawnienia pliku bieżącego procesu do trybu określonego przez *tryb*. Maska uprawnienia pliku Modyfikuje ustawienia uprawnień nowych plików utworzonych przez **_creat —**, **_otwórz**, lub **_sopen —**. Jeśli bit maski to 1, odpowiadający mu bit pliku żądane uprawnienie wartość jest równa 0 (niedopuszczalne). Jeśli bit maski to 0, odpowiadający mu bit pozostanie bez zmian. Ustawienie uprawnień dla nowego pliku nie jest ustawiona, dopóki ten plik będzie zamknięty po raz pierwszy.

Wyrażenie całkowite *pmode* zawiera co najmniej jednej z następujących stałych manifestu, zdefiniowane w SYS\STAT. H:

|*pmode*||
|-|-|
|**_S_IWRITE —**|Zapisywanie dozwolone.|
|**_S_IREAD —**|Odczytywanie dozwolone.|
|**_S_IREAD —** \| **_S_IWRITE —**|Odczytywanie i zapisywanie dozwolone.|

Gdy zarówno stałe są podane, są połączone z operator Alternatywy ( **|** ). Jeśli *tryb* argument jest **_s_iread —**, odczytu jest niedozwolony (plik jest tylko do zapisu). Jeśli *tryb* argument jest **_s_iwrite —**, zapis nie jest dozwolone. (plik jest tylko do odczytu). Na przykład jeśli ustawiono bit zapisu maski, nowe pliki będą tylko do odczytu. Pamiętaj, że wszystkie pliki z systemu MS-DOS i systemów operacyjnych Windows, jest do odczytu; nie jest możliwe nadaj uprawnienia tylko do zapisu. W związku z tym ustawienie odczytu bit z **_umask_s —** nie ma wpływu na tryby pliku.

Jeśli *pmode* nie jest kombinacją jednego z manifestu stałe lub zawiera inny zestaw stałych, funkcja będzie ignorować te.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_umask_s**|\<IO.h > i \<sys/stat.h > i \<sys/types.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_umask_s.c
/* This program uses _umask_s to set
* the file-permission mask so that all future
* files will be created as read-only files.
* It also displays the old mask.
*/

#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask, err;

   /* Create read-only files: */
   err = _umask_s( _S_IWRITE, &oldmask );
   if (err)
   {
      printf("Error setting the umask.\n");
      exit(1);
   }
   printf( "Oldmask = 0x%.4x\n", oldmask );
}
```

```Output
Oldmask = 0x0000
```

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_umask](umask.md)<br/>
