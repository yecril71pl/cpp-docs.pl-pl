---
title: memmove, wmemmove
ms.date: 11/04/2016
apiname:
- memmove
- wmemmove
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- memmove
- wmemmove
helpviewer_keywords:
- wmemmove function
- memmove function
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
ms.openlocfilehash: 988af1c2678e20ea40ce4dfe331a3b6c49db0547
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210097"
---
# <a name="memmove-wmemmove"></a>memmove, wmemmove

Przenosi buforu na inny. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [memmove_s —, wmemmove_s —](memmove-s-wmemmove-s.md).

## <a name="syntax"></a>Składnia

```C
void *memmove(
   void *dest,
   const void *src,
   size_t count
);
wchar_t *wmemmove(
   wchar_t *dest,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*dest*<br/>
Obiekt docelowy.

*src*<br/>
Obiekt źródłowy.

*Liczba*<br/>
Liczba bajtów (**memmove**) ani znaków (**wmemmove —**) do skopiowania.

## <a name="return-value"></a>Wartość zwracana

Wartość *dest*.

## <a name="remarks"></a>Uwagi

Kopiuje *liczba* bajtów (**memmove**) ani znaków (**wmemmove —**) z *src* do *dest*. Niektóre regiony obszaru źródłowy i docelowy zachodziły na siebie, obie funkcje upewnij się, że oryginalne źródło bajty nakładających się są kopiowane przed zastąpieniem.

**Uwaga dotycząca zabezpieczeń** upewnij się, że bufor docelowy jest taki sam lub większy rozmiar niż bufor źródłowy. Aby uzyskać więcej informacji, zobacz [unikanie przepełnień bufora](/windows/desktop/SecBP/avoiding-buffer-overruns).

**Memmove** i **wmemmove —** funkcje zostaną wycofane tylko, jeśli stała **_CRT_SECURE_DEPRECATE_MEMORY** zdefiniowano przed instrukcji dołączania, aby funkcji, które mają być przestarzałe, tak jak w poniższym przykładzie:

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <string.h>
```

lub

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**memmove**|\<string.h>|
|**wmemmove**|\<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_memcpy.c
// Illustrate overlapping copy: memmove
// always handles it correctly; memcpy may handle
// it correctly.
//

#include <memory.h>
#include <string.h>
#include <stdio.h>

char str1[7] = "aabbcc";

int main( void )
{
   printf( "The string: %s\n", str1 );
   memcpy( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );

   strcpy_s( str1, sizeof(str1), "aabbcc" );   // reset string

   printf( "The string: %s\n", str1 );
   memmove( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );
}
```

```Output
The string: aabbcc
New string: aaaabb
The string: aabbcc
New string: aaaabb
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie buforem](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
