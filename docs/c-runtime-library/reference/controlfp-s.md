---
title: _controlfp_s
ms.date: 4/2/2020
api_name:
- _controlfp_s
- _o__controlfp_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- controlfp_s
- _controlfp_s
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
ms.openlocfilehash: 4b36cc9f5ed83b68cb15c39be91165ed7aa86d7b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348532"
---
# <a name="_controlfp_s"></a>_controlfp_s

Pobiera i ustawia słowo kontroli zmiennoprzecinkowej. Ta wersja [_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md) ma ulepszenia zabezpieczeń, zgodnie z opisem w funkcji zabezpieczeń w [CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _controlfp_s(
    unsigned int *currentControl,
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>Parametry

*prądKontrola*<br/>
Bieżąca wartość bitowa słowa kontrolnego.

*nowyKontrol*<br/>
Nowe wartości bitów słowa kontrolnego.

*maska*<br/>
Maska dla nowych bitów wyrazu kontrolnego do ustawionego.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie, lub kod błędu wartości **errno.**

## <a name="remarks"></a>Uwagi

Funkcja **_controlfp_s** jest niezależną od platformy i bezpieczniejszą wersją **_control87**, która pobiera słowo sterujące zmiennoprzecinkiem do adresu, który jest przechowywany w *currentControl* i ustawia go za pomocą *newControl*. Bity w wartościach wskazują stan sterowania zmiennoprzecinkowego. Stan sterowania zmiennoprzecinkowego umożliwia programowi zmianę precyzji, zaokrąglania i nieskończoności trybów w pakiecie matematycznym zmiennoprzecinkowych, w zależności od platformy. Można również użyć **_controlfp_s** do maskowania lub demaskowania wyjątków zmiennoprzecinkowych.

Jeśli wartość *maski* jest równa 0, **_controlfp_s** pobiera słowo kontroli zmiennoprzecinkowej i przechowuje pobraną wartość w *currentControl*.

Jeśli *maska* jest niezerowa, ustawiona jest nowa wartość słowa kontrolnego: Dla każdego bitu ustawionego (czyli równego 1) w *masce,* odpowiedni bit w *nowym* jest używany do aktualizacji słowa kontrolnego. Innymi słowy, *fpcntrl* = ((*fpcntrl* & ~*maska*) &#124; (*newControl* & *mask*)), gdzie *fpcntrl* jest słowem sterującym zmiennoprzecinkowym. W tym scenariuszu *currentControl* jest ustawiona na wartość po zakończeniu zmiany; nie jest to stara wartość bitowa słowa kontrolnego.

> [!NOTE]
> Domyślnie biblioteki w czasie wykonywania maskują wszystkie wyjątki zmiennoprzecinkowa.

**_controlfp_s** jest prawie identyczna z funkcją **_control87** na platformach Intel (x86), x64 i ARM. Jeśli kierujesz reklamy na platformy x86, x64 lub ARM, możesz użyć **_control87** lub **_controlfp_s**.

Różnica między **_control87** i **_controlfp_s** polega na tym, jak traktują wartości denormalne. W przypadku platform Intel (x86), x64 i ARM **_control87** można ustawić i wyczyścić maskę wyjątku DENORMAL OPERAND. **_controlfp_s** nie modyfikuje maski wyjątku DENORMAL OPERAND. W tym przykładzie pokazano różnicę:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Możliwe wartości stałej maski *(maska)* i nowych wartości kontrolnych (*newControl*) są wyświetlane w poniższej tabeli Wartości szesnastkowe. Użyj przenośnych stałych wymienionych poniżej **(_MCW_EM**, **_EM_INVALID**i tak dalej) jako argumenty do tych funkcji, zamiast wyraźnie dostarczać wartości szesnastkowe.

Platformy pochodne firmy Intel (x86) obsługują wartości wejściowe i wyjściowe DENORMAL w sprzęcie. Zachowanie x86 jest zachowanie wartości DENORMAL. Platforma ARM i platformy x64, które obsługują SSE2, umożliwiają opróżnianie operandów i wyników DENORMAL lub zmuszanie do zera. Funkcje **_controlfp_s** **, _controlfp**i **_control87** zapewniają maskę do zmiany tego zachowania. Poniższy przykład pokazuje użycie tej maski:

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Na platformach ARM funkcja **_controlfp_s** ma zastosowanie do rejestru FPSCR. W architekturach x64 dotyczy to tylko słowa sterującego SSE2 przechowywanego w rejestrze MXCSR. Na platformach Intel (x86) **_controlfp_s** wpływa na słowa sterujące zarówno dla x87, jak i SSE2, jeśli są obecne. Możliwe jest, że oba słowa kontrolne są ze sobą niespójne (na przykład z powodu wcześniejszego wezwania do [__control87_2);](control87-controlfp-control87-2.md) jeśli między dwoma słowami sterującymi występuje niespójność, **_controlfp_s** ustawia flagę **EM_AMBIGUOUS** w *currentControl*. Jest to ostrzeżenie, że zwrócone słowo kontrolne może nie reprezentować stan zarówno zmiennoprzecinkowych słów kontrolnych dokładnie.

W architekturach ARM i x64 zmiana trybu nieskończoności lub precyzji zmiennoprzecinkowej nie jest obsługiwana. Jeśli na platformie x64 jest używana maska sterująca precyzją, funkcja wywołuje twierdzenie, a nieprawidłowy program obsługi parametrów jest wywoływany, zgodnie z opisem w [zatwierdzeniu parametru.](../../c-runtime-library/parameter-validation.md)

Jeśli maska nie jest ustawiona poprawnie, ta funkcja generuje nieprawidłowy wyjątek parametru, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, ta funkcja zwraca **wartość EINVAL** i ustawia **errno** na **EINVAL**.

Ta funkcja jest ignorowana podczas używania [/clr (kompilacja środowiska wykonawczego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md) do kompilacji, ponieważ środowisko uruchomieniowe języka wspólnego (CLR) obsługuje tylko domyślną precyzję zmiennoprzecinkową.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="mask-constants-and-values"></a>Maskuj stałe i wartości

W przypadku maski **_MCW_EM** wyczyszczenie powoduje ustawienie wyjątku, który umożliwia wyjątek sprzętowy; ustawienie powoduje ukrycie wyjątku. Jeśli **_EM_UNDERFLOW** lub **_EM_OVERFLOW** występuje, nie wyjątek sprzętu jest zgłaszany, dopóki nie zostanie wykonana następna instrukcja zmiennoprzecinkowa. Aby wygenerować wyjątek sprzętowy natychmiast po **_EM_UNDERFLOW** lub **_EM_OVERFLOW,** należy wywołać instrukcję FWAIT MASM.

|Maska|Wartość sześciokątna|Stały|Wartość sześciokątna|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (kontrola denormalna)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (maska wyjątku przerwania)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (sterowanie nieskończonością)<br /><br /> (Nie jest obsługiwany na platformach ARM lub x64).|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (kontrola zaokrąglania)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (sterowanie precyzyjne)<br /><br /> (Nie jest obsługiwany na platformach ARM lub x64).|0x00030000|**_PC_24** (24 bity)<br /><br /> **_PC_53** (53 bity)<br /><br /> **_PC_64** (64 bity)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_controlfp_s**|\<> float.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_contrlfp_s.c
// processor: x86
// This program uses _controlfp_s to output the FP control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word;
    int err;

    // Show original FP control word and do calculation.
    err = _controlfp_s(&control_word, 0, 0);
    if ( err ) /* handle error here */;

    printf( "Original: 0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    err = _controlfp_s(&control_word, _PC_24, MCW_PC);
    if ( err ) /* handle error here */;

    printf( "24-bit:   0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    err = _controlfp_s(&control_word, _CW_DEFAULT, MCW_PC);
    if ( err ) /* handle error here */;

    printf( "Default:  0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x9001f
0.1 * 0.1 = 1.000000000000000e-002
24-bit:   0xa001f
0.1 * 0.1 = 9.999999776482582e-003
Default:  0x9001f
0.1 * 0.1 = 1.000000000000000e-002
```

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
