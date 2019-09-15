---
title: memcpy, wmemcpy
ms.date: 11/04/2016
api_name:
- memcpy
- wmemcpy
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemcpy
- memcpy
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
ms.openlocfilehash: e9d947dc4e9ecea654e8cb16e957887fe4360161
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951855"
---
# <a name="memcpy-wmemcpy"></a>memcpy, wmemcpy

Kopiuje bajty między buforami. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [memcpy_s, wmemcpy_s](memcpy-s-wmemcpy-s.md).

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
Nowy bufor.

*SRC*<br/>
Bufor do skopiowania.

*liczbą*<br/>
Liczba znaków do skopiowania.

## <a name="return-value"></a>Wartość zwracana

Wartość miejsca *docelowego*.

## <a name="remarks"></a>Uwagi

**memcpy** kopiuje *liczbę* bajtów z *src* do miejsca *docelowego*; **wmemcpy** kopiuje *znaki* szerokie (dwa bajty). Jeśli źródło i miejsce docelowe nakładają się na siebie, zachowanie **memcpy** jest niezdefiniowane. Użyj **memmove** , aby obsłużyć nakładające się regiony.

> [!IMPORTANT]
> Upewnij się, że bufor docelowy ma ten sam rozmiar lub większy niż bufor źródłowy. Aby uzyskać więcej informacji, zobacz [unikanie przekroczeń buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

> [!IMPORTANT]
> Ze względu na to, że wiele przepełnień buforu i w związku z tym potencjalne luki w zabezpieczeniach zostały prześledzone w niewłaściwy sposób przy użyciu **memcpy**, ta funkcja jest wymieniona wśród funkcji "zakazane" w ramach cyklu projektowania zabezpieczeń (SDL).  Można zauważyć, że niektóre klasy bibliotek VC + + nadal używają **memcpy**.  Ponadto można zauważyć, że optymalizator kompilatora VC + + czasami emituje wywołania do **memcpy**.  Produkt wizualny C++ jest opracowywany zgodnie z procesem SDL i w ten sposób użycie tej funkcji jest ściśle oceniane.  W przypadku użycia biblioteki, wywołania zostały starannie scrutinized, aby zapewnić, że przepełnienia buforu nie będą dozwolone za pomocą tych wywołań.  W przypadku kompilatora czasami pewne wzorce kodu są rozpoznawane jako identyczne z wzorcem **memcpy**i są w ten sposób zastępowane wywołaniem funkcji.  W takich przypadkach użycie **memcpy** nie jest ryzykowne niż oryginalne instrukcje byłyby; zostały one po prostu zoptymalizowane pod kątem wywołania funkcji **memcpy** dostrajania wydajności.  Tak samo jak korzystanie z funkcji CRT "Safe" nie gwarantuje bezpieczeństwa (po prostu utrudnia to ich niebezpieczeństwo), korzystanie z funkcji "zabronione" nie gwarantuje niebezpieczeństwa (po prostu wymagają większej kontroli, aby zapewnić bezpieczeństwo).
>
> Ponieważ **memcpy** użycie przez kompilator i biblioteki VC + + zostało tak starannie scrutinized, te wywołania są dozwolone w kodzie, który jest w inny sposób zgodny z SDL.  wywołania **memcpy** wprowadzone w kodzie źródłowym aplikacji są zgodne z IDENTYFIKATORem SDL, gdy takie użycie zostało sprawdzone przez ekspertów ds. zabezpieczeń.

Funkcje **memcpy** i **wmemcpy** będą przestarzałe, jeśli stała **_CRT_SECURE_DEPRECATE_MEMORY** jest zdefiniowana przed instrukcją dołączenia, aby funkcje były przestarzałe, na przykład w poniższym przykładzie:

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
|**memcpy**|\<> pamięci. h > \<lub String. h|
|**wmemcpy**|\<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz [memmove](memmove-wmemmove.md) , aby uzyskać przykład korzystania z **memcpy**.

## <a name="see-also"></a>Zobacz także

[Manipulowanie buforem](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
