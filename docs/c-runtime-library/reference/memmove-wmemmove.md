---
title: memmove —, wmemmove — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- memmove
- wmemmove
dev_langs:
- C++
helpviewer_keywords:
- wmemmove function
- memmove function
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cd65c2fc73a20c45338348f05736bb71c1f6b772
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="memmove-wmemmove"></a>memmove, wmemmove

Przenosi buforu na inny. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [memmove_s —, wmemmove_s —](memmove-s-wmemmove-s.md).

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
Liczba bajtów (**memmove —**) ani znaków (**wmemmove —**) do skopiowania.

## <a name="return-value"></a>Wartość zwracana

Wartość *dest*.

## <a name="remarks"></a>Uwagi

Kopie *liczba* bajtów (**memmove —**) ani znaków (**wmemmove —**) z *src* do *dest*. Nakładania się pewnych regionach obszar źródłowy i docelowy, funkcjami upewnij się, że oryginalne źródło bajty nakładających się są kopiowane przed zastąpieniem.

**Uwaga dotycząca zabezpieczeń** upewnij się, że bufor docelowy jest taki sam lub większy rozmiar niż bufor źródłowy. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).

**Memmove —** i **wmemmove —** funkcje zostaną wycofane tylko, jeśli stała **_CRT_SECURE_DEPRECATE_MEMORY** zdefiniowano przed instrukcji włączenia Aby Funkcje przestarzałe, takich jak pokazano w przykładzie poniżej:

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
|**memmove —**|\<string.h>|
|**wmemmove —**|\<WChar.h >|

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
