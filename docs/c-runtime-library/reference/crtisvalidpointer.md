---
title: _Crtisvalidpointer — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtIsValidPointer
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
- CrtlsValidPointer
- _CrtIsValidPointer
dev_langs:
- C++
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb78f8dee494fd213df6db16e2800cb9090bdf3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397277"
---
# <a name="crtisvalidpointer"></a>_CrtIsValidPointer

Sprawdza, czy wskaźnik nie jest zerowa. W wersji biblioteki wykonawcze języka C przed Visual Studio 2010 sprawdza, czy pamięci określony zakres jest nieprawidłowy do odczytu i zapisu (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
int _CrtIsValidPointer(
   const void *address,
   unsigned int size,
   int access
);
```

### <a name="parameters"></a>Parametry

*Adres*<br/>
Wskazuje początek zakresu pamięci, aby sprawdzić poprawność.

*Rozmiar*<br/>
Rozmiar pamięci określony zakres (w bajtach).

*Dostęp*<br/>
Ułatwienia dostępu odczytu i zapisu do określenia zakresu pamięci.

## <a name="return-value"></a>Wartość zwracana

**_Crtisvalidpointer —** zwraca wartość PRAWDA, jeśli określony wskaźnik nie jest zerowa. W wersjach biblioteki CRT przed Visual Studio 2010 zwraca wartość PRAWDA, jeśli zakres pamięci jest nieprawidłowa dla określonej operacji. W przeciwnym razie funkcja zwraca wartość FALSE.

## <a name="remarks"></a>Uwagi

Począwszy od biblioteki CRT w programie Visual Studio 2010, *rozmiar* i *dostępu* parametry są ignorowane, i **_crtisvalidpointer —** tylko sprawdza, czy określony *adres* nie jest zerowa. Ponieważ ten test jest łatwe do wykonania samodzielnie, nie zaleca się, że aby użyć tej funkcji. W wersjach przed Visual Studio 2010, funkcja sprawdza, czy zakres pamięci, rozpoczynając od *adres* i rozszerzanie dla *rozmiar* bajtów jest prawidłowa dla dostępności określonej operacji. Gdy *dostępu* jest ustawiony na wartość TRUE, zakresu pamięci jest weryfikowany na odczytywanie i zapisywanie. Gdy *dostępu* ma wartość FALSE, zakresu pamięci uwierzytelnieniu się tylko do odczytu. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań **_crtisvalidpointer —** są usuwane podczas przetwarzania wstępnego.

Ponieważ ta funkcja zwraca wartość PRAWDA lub FAŁSZ, mogą być przekazywane do jednego z [_ASSERT](assert-asserte-assert-expr-macros.md) makra, aby utworzyć prosty błąd debugowania mechanizmu obsługi. Poniższy przykład powoduje błąd potwierdzenia, jeśli zakres pamięci nie jest prawidłowy dla odczytywanie i zapisywanie operacji:

```C
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );
```

Aby uzyskać więcej informacji o tym, jak **_crtisvalidpointer —** może być używany z innymi funkcje debugowania i makra, zobacz [makra dla raportowania](/visualstudio/debugger/macros-for-reporting). Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtIsValidPointer**|\<crtdbg.h>|

**_Crtisvalidpointer —** to rozszerzenie firmy Microsoft. Aby uzyskać informacje dotyczące zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Zobacz przykład [_crtisvalidheappointer —](crtisvalidheappointer.md) tematu.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
