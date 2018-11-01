---
title: _CrtIsValidPointer
ms.date: 11/04/2016
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
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
ms.openlocfilehash: 64197d460cdb7dd26d22196c08151be09df48573
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429257"
---
# <a name="crtisvalidpointer"></a>_CrtIsValidPointer

Sprawdza, czy wskaźnik nie jest zerowa. W wersjach biblioteki wykonawczej C przed Visual Studio 2010 sprawdza, czy zakres określony pamięci jest prawidłowy dla odczytu i zapisu (tylko wersja debugowania).

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

*Dostęp do*<br/>
Dostępność odczytu/zapisu do określenia dla określonego zakresu pamięci.

## <a name="return-value"></a>Wartość zwracana

**_Crtisvalidpointer —** zwraca wartość PRAWDA, jeśli określony wskaźnik nie jest null. W wersjach biblioteki CRT przed Visual Studio 2010 zwraca wartość PRAWDA, jeśli zakres pamięci jest nieprawidłowa dla określonej operacji. W przeciwnym razie funkcja zwraca wartość FALSE.

## <a name="remarks"></a>Uwagi

Począwszy od biblioteki CRT w programie Visual Studio 2010 *rozmiar* i *dostępu* parametry są ignorowane, i **_crtisvalidpointer —** tylko sprawdza, czy określony *adres* nie ma wartości null. Ponieważ ten test jest łatwe do wykonania samodzielnie, zaleca się używania tej funkcji. W wersjach starszych niż program Visual Studio 2010, funkcja sprawdza, czy zakres pamięci, rozpoczynając od *adres* i rozszerzanie dla *rozmiar* bajtów jest prawidłowa dla dostępności określonej operacji. Gdy *dostępu* jest ustawiona na wartość TRUE, zakres pamięci jest sprawdzane pod kątem Odczyt i zapis. Gdy *dostępu* ma wartość FAŁSZ, zakres pamięci zweryfikowaniu się tylko do odczytu. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_crtisvalidpointer —** są usuwane podczas przetwarzania wstępnego.

Ponieważ ta funkcja zwraca wartość PRAWDA lub FAŁSZ, mogą być przekazywane do jednego z [_ASSERT](assert-asserte-assert-expr-macros.md) makra, aby utworzyć prosty błąd debugowania mechanizm obsługi. Poniższy przykład powoduje błąd potwierdzenia, jeśli zakres pamięci nie nadaje się do zarówno operacji odczytu i zapisu:

```C
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );
```

Aby uzyskać więcej informacji o tym, jak **_crtisvalidpointer —** mogą być używane z innych funkcji debugowania i makr, zobacz [makra dla raportowania](/visualstudio/debugger/macros-for-reporting). Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtIsValidPointer**|\<crtdbg.h>|

**_Crtisvalidpointer —** jest rozszerzeniem firmy Microsoft. Aby uzyskać informacje o zgodności – zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Zobacz przykład [_crtisvalidheappointer —](crtisvalidheappointer.md) tematu.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
