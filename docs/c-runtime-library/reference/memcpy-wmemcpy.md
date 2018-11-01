---
title: memcpy, wmemcpy
ms.date: 11/04/2016
apiname:
- memcpy
- wmemcpy
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
- wmemcpy
- memcpy
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
ms.openlocfilehash: 0c71bd7b1a661a0964576e831e008d23692d4c2e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611188"
---
# <a name="memcpy-wmemcpy"></a>memcpy, wmemcpy

Kopiuje bajtów między buforów. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [memcpy_s —, wmemcpy_s —](memcpy-s-wmemcpy-s.md).

## <a name="syntax"></a>Składnia

```C
void *memcpy(
   void *dest,
   const void *src,
   size_t count
);
wchar_t *wmemcpy(
   wchar_t *dest,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*dest*<br/>
Bufor nowego.

*src*<br/>
Bufor do skopiowania.

*Liczba*<br/>
Liczba znaków do skopiowania.

## <a name="return-value"></a>Wartość zwracana

Wartość *dest*.

## <a name="remarks"></a>Uwagi

**memcpy** kopie *liczba* bajtów z *src* do *dest*; **wmemcpy —** kopie *liczba* znaków dwubajtowych (dwa bajty). Jeśli źródłowe i docelowe nakładają się, zachowanie **memcpy** jest niezdefiniowana. Użyj **memmove** do obsługi nakładających się regionów.

> [!IMPORTANT]
> Upewnij się, że bufor docelowy jest taki sam lub większy rozmiar niż bufor źródłowy. Aby uzyskać więcej informacji, zobacz [unikanie przepełnień bufora](/windows/desktop/SecBP/avoiding-buffer-overruns).

> [!IMPORTANT]
> Ponieważ tak wiele przepełnienia buforu, a zatem potencjalnych lukami w zabezpieczeniach, że znaczniki zostały dodane niewłaściwy użytkowania **memcpy**, ta funkcja jest na liście funkcji "zabronione" przez cykl projektowania zabezpieczeń (SDL).  Można zaobserwować, że niektóre klasy biblioteki VC ++ w dalszym ciągu używać **memcpy**.  Ponadto, można zauważyć, że optymalizator kompilatora VC ++ czasami emituje wywołania do **memcpy**.  Produkt Visual C++ jest opracowany zgodnie z procesu SDL, a ten sposób korzystanie z tej funkcji zakazanych ściśle ocenie.  W przypadku biblioteki z niej korzystać, wywołania została starannie kontroli aby upewnić się, że przepełnienia buforu nie będzie można za pomocą tych wywołań.  W przypadku kompilatora, czasami niektórych wzorców kodu są rozpoznawane jako taka sama, jak wzorzec **memcpy**i dlatego są zastępowane przy użyciu wywołania funkcji.  W takich przypadkach użycia **memcpy** jest nie więcej niebezpieczne niż oryginalna byłby instrukcje; po prostu zostały one zoptymalizowane do wywołania wydajność dostosowana **memcpy** funkcji.  Tak samo jak użycie "bezpieczne" funkcje CRT nie gwarantuje bezpieczeństwa (one po prostu utrudnić jako niebezpieczny) Użyj funkcji "zabronione" nie gwarantuje zagrożenia (po prostu wymagają większej kontroli w celu zapewnienia bezpieczeństwa).
>
> Ponieważ **memcpy** więc dobrze kontroli wykorzystania przez VC ++ kompilatora i bibliotek, te wywołania są dozwolone w ramach kodu, które w przeciwnym razie jest zgodne z SDL.  **memcpy** wywołania wprowadzone w kodzie źródłowym aplikacji są zgodne z SDL tylko, gdy używające zostało przejrzane przez ekspertów ds. bezpieczeństwa.

**Memcpy** i **wmemcpy —** funkcje zostaną wycofane tylko, jeśli stała **_CRT_SECURE_DEPRECATE_MEMORY** zdefiniowano przed instrukcji dołączania, aby funkcji, które mają być przestarzałe, tak jak w poniższym przykładzie:

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <memory.h>
```

lub

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**memcpy**|\<Memory.h > lub \<string.h >|
|**wmemcpy**|\<WChar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz [memmove](memmove-wmemmove.md) przykład sposobu użycia **memcpy**.

## <a name="see-also"></a>Zobacz także

[Manipulowanie buforem](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
