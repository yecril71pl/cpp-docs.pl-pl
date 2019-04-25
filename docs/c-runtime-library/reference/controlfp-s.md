---
title: _controlfp_s
ms.date: 04/05/2018
apiname:
- _controlfp_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 0624cbfb4870ca87efebac01a8de682b588a4ca3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335388"
---
# <a name="controlfps"></a>_controlfp_s

Pobiera i ustawia słowo sterujące zmiennoprzecinkowe. Ta wersja [_control87 —, _controlfp, \__control87_2](control87-controlfp-control87-2.md) ma wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _controlfp_s(
    unsigned int *currentControl,
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>Parametry

*currentControl*<br/>
Bieżąca wartość bitowa słowa kontrolnego.

*newControl*<br/>
Nowe wartości bitowe słowa sterującego.

*Maska*<br/>
Maska dla nowych bitów słowa kontrolującego do ustawienia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli kończy się pomyślnie, lub moduł **errno** kod błędu.

## <a name="remarks"></a>Uwagi

**_Controlfp_s —** funkcja jest niezależny od platformy i bezpieczniejszej wersji **_control87 —**, która pobiera słowo sterujące zmiennoprzecinkowe na adres który jest przechowywany w  *currentControl* i ustawia je za pomocą *newControl*. Bity w wartości wskazują stan sterowania zmiennoprzecinkowego. Stan sterowania zmiennoprzecinkowego Włącza program do zmiany precyzji, zaokrąglania oraz trybu nieskończoności w pakiecie zmiennoprzecinkowym zapisu matematycznego, w zależności od platformy. Można również użyć **_controlfp_s —** do zamaskowania lub usunięcia wyjątki zmiennoprzecinkowe.

Jeśli wartość *maski* jest równa 0, **_controlfp_s —** pobiera słowo sterujące zmiennoprzecinkowe i przechowuje pobraną wartość w *currentControl*.

Jeśli *maski* jest różna od zera, ustawiono nową wartość dla słowa sterującego: Dla dowolnego bit, który jest ustawiony (czyli wynosi 1) w *maski*, odpowiadający mu bit w *nowe* służy do aktualizacji słowa sterującego. Innymi słowy *fpcntrl* = ((*fpcntrl* & ~*maski*) &#124; (*newControl* & *maski* )) gdzie *fpcntrl* jest słowem sterującym zmiennoprzecinkowym. W tym scenariuszu *currentControl* jest ustawiona na wartość po zakończeniu zmiany; nie jest stara wartość bitowa słowa kontrolnego.

> [!NOTE]
> Domyślnie bibliotek środowiska uruchomieniowego maskują wszystkie wyjątki zmiennoprzecinkowe.

**_controlfp_s —** jest prawie identyczna **_control87 —** działa na procesorze Intel (x86) x64 i platformami ARM. Jeśli obiektem docelowym x86, x64 lub platformy ARM, można użyć **_control87 —** lub **_controlfp_s —**.

Różnica między **_control87 —** i **_controlfp_s —** to w jaki sposób traktuje wartości denormal. Dla komputerów Intel (x86), x 64 i platform ARM **_control87 —** można ustawić lub wyczyścić maskę wyjątku ZDENORMALIZOWANY OPERAND. **_controlfp_s —** nie modyfikuje maski wyjątku DENORMALIZACJA OPERANDU. Ten przykład ilustruje różnicę:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Możliwe wartości dla stałej maski (*maski*) i nowe wartości formantu (*newControl*) są wyświetlane w poniższej tabeli wartości szesnastkowych. Używanie przenośnych stałych wymienionych poniżej (**_MCW_EM**, **_EM_INVALID**i tak dalej) jako argumenty tych funkcji, a nie dostarczanie szesnastkowych wartości jawnie.

Intel (x86)-platformy obsługuje danych wejściowych DENORMAL i wyjściowych wartości na liście sprzętu. X86 ma zachować wartości DENORMAL. Platforma ARM i x64 obsługiwanych platform, które mają SSE2 Włącz DENORMAL i wyników do należy, lub wymuszają zero. **_Controlfp_s —**, **_controlfp**, i **_control87 —** funkcje zapewniają maskę, aby zmienić to zachowanie. Poniższy przykład pokazuje użycie tej maski:

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Na platformach ARM **_controlfp_s —** funkcja odnosi się do rejestru fpscr. Na x64 architektury, tylko wyraz kontroli SSE2, który jest przechowywany w mxcsr rejestru ma wpływ. Na platformach firmy Intel (x86) **_controlfp_s —** wpływa na wyrazy sterowania zarówno dla x87 i SSE2, jeśli jest obecny. Istnieje możliwość, że dwoma słowami sterującymi będą sprzeczne ze sobą (ze względu na poprzednie wywołanie [__control87_2](control87-controlfp-control87-2.md), na przykład); Jeśli istnieje niespójność między dwoma słowami sterującymi, **_controlfp_s —** ustawia **obiekt EM_AMBIGUOUS** znacznik w *currentControl*. To ostrzeżenie, że wyraz zwróconego formantu może reprezentują dokładnie stanu obu wyrazów zmiennoprzecinkowych formantu.

Na ARM i x64 architektury, zmiana trybu nieskończoności lub Zwiększanie dokładności nie jest obsługiwane. Jeśli używana jest maska kontroli dokładności, na x64 platformy, funkcja wywołuje potwierdzenie i procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md).

Jeśli maska nie jest ustawiona poprawnie, funkcja ta wytwarza wyjątek nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca **EINVAL** i ustawia **errno** do **EINVAL**.

Ta funkcja jest ignorowane, gdy używasz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) do kompilacji ponieważ środowisko uruchomieniowe języka wspólnego (CLR) obsługuje tylko domyślną precyzję zmiennoprzecinkową.

### <a name="mask-constants-and-values"></a>Stałe maski i wartości

Aby uzyskać **_MCW_EM** maska, czyszczenie ustawia wyjątek, który umożliwia wyjątek sprzętowy; ustawienie jej ukrywa wyjątek. Jeśli **_EM_UNDERFLOW** lub **_EM_OVERFLOW** problem wystąpi, żaden wyjątek sprzętowy nie jest zgłaszany do momentu następnej instrukcji zmiennoprzecinkowej jest wykonywany. Do generowania wyjątków sprzętowych natychmiast po **_EM_UNDERFLOW** lub **_EM_OVERFLOW**, wywołaj instrukcję FWAIT masm.

|Maska|Wartość szesnastkowa|Stała|Wartość szesnastkowa|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (formant zdenormalizowany)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (maska wyjątku przerwania)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (formant nieskończoność)<br /><br /> (Nie obsługiwany na ARM lub x64 platformy.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (formant zaokrąglenia)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (formant precyzji)<br /><br /> (Nie obsługiwany na ARM lub x64 platformy.)|0x00030000|**_PC_24** (24 bity)<br /><br /> **_PC_53** (53-bitowy)<br /><br /> **_PC_64** (64-bitowy)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_controlfp_s**|\<float.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
