---
title: _umask_s
ms.date: 4/2/2020
api_name:
- _umask_s
- _o__umask_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- unmask_s
- _umask_s
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
ms.openlocfilehash: d590910d5f5092a78ad64c8f9ef0aa259211e226
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362177"
---
# <a name="_umask_s"></a>_umask_s

Ustawia domyślną maskę uprawnień do plików. Wersja [_umask](umask.md) z ulepszeniami zabezpieczeń, jak opisano w [obszarze Funkcje zabezpieczeń w crt](../../c-runtime-library/security-features-in-the-crt.md).

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

*pOldMode (Tryb pOld)*<br/>
Poprzednia wartość ustawienia uprawnień.

## <a name="return-value"></a>Wartość zwracana

Zwraca kod błędu, jeśli *tryb* nie określa prawidłowego trybu lub wskaźnik *pOldMode* ma **wartość NULL**.

### <a name="error-conditions"></a>Warunki błędu

|*Tryb*|*pOldMode (Tryb pOld)*|Wartość zwracana|Zawartość *pOldMode*|
|------------|----------------|----------------------|--------------------------------|
|Wszelki|**Null**|**Einval**|nie zmodyfikowano|
|nieprawidłowy tryb|Wszelki|**Einval**|nie zmodyfikowano|

Jeśli wystąpi jeden z powyższych warunków, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametru.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **_umask_s** zwraca **wartość EINVAL** i ustawia **errno** na **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_umask_s** ustawia maskę uprawnień do pliku bieżącego procesu na tryb określony przez *tryb*. Maska uprawnień do plików modyfikuje ustawienie uprawnień nowych plików utworzonych przez **_creat** **, _open**lub **_sopen**. Jeśli bit w masce wynosi 1, odpowiedni bit w żądanej wartości uprawnień pliku jest ustawiony na 0 (niedozwolone). Jeśli nieco w masce wynosi 0, odpowiedni bit pozostaje niezmieniony. Ustawienie uprawnień dla nowego pliku nie jest ustawiane, dopóki plik nie zostanie zamknięty po raz pierwszy.

*Pmode* wyrażenia liczby całkowitej zawiera jedną lub obie z następujących stałych manifestu, zdefiniowane w SYS\STAT. H:

|*pmode*||
|-|-|
|**_S_IWRITE**|Pisanie dozwolone.|
|**_S_IREAD**|Odczyt dozwolony.|
|\| **_S_IREAD** **_S_IWRITE**|Czytanie i pisanie dozwolone.|

Gdy obie stałe są podane, są one połączone z **|** operatorem bitowym OR ( ). Jeśli argument *trybu* jest **_S_IREAD,** odczyt jest niedozwolony (plik jest tylko do zapisu). Jeśli argument *trybu* jest **_S_IWRITE,** zapisywanie jest niedozwolone (plik jest tylko do odczytu). Na przykład jeśli bit zapisu jest ustawiony w masce, wszystkie nowe pliki będą tylko do odczytu. Należy pamiętać, że w systemach MS-DOS i systemach operacyjnych Windows wszystkie pliki są czytelne; nie można udzielić uprawnień tylko do zapisu. W związku z tym ustawienie bitu odczytu z **_umask_s** nie ma wpływu na tryby pliku.

Jeśli *pmode* nie jest kombinacją jednej ze stałych manifestu lub zawiera alternatywny zestaw stałych, funkcja po prostu je zignoruje.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_umask_s**|\<io.h> i \<sys/stat.h> i \<sys/types.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_umask](umask.md)<br/>
