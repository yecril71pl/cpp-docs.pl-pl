---
title: _controlfp_s
ms.date: 04/05/2018
api_name:
- _controlfp_s
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
ms.openlocfilehash: 0d12c139f305a3c66419a4e27905ac9f73345f4d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942881"
---
# <a name="_controlfp_s"></a>_controlfp_s

Pobiera i ustawia słowo sterujące zmiennoprzecinkowe. Ta wersja [_control87, _controlfp \_, _control87_2](control87-controlfp-control87-2.md) zawiera ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Bieżąca wartość bitu kontrolki.

*newControl*<br/>
Nowe wartości bitowe programu Control-Word.

*bitowa*<br/>
Maska dla nowego tekstu kontrolki do ustawienia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli kończy się pomyślnie lub kod błędu wartości **errno** .

## <a name="remarks"></a>Uwagi

Funkcja **_controlfp_s** to niezależna od platformy i bezpieczniejsza wersja **_control87**, która pobiera słowo sterujące zmiennoprzecinkowe do adresu przechowywanego w *currentControl* i ustawia je za pomocą *newControl*. Bity w wartości wskazują stan sterowania zmiennoprzecinkowego. Stan kontroli zmiennoprzecinkowej umożliwia programowi zmianę precyzji, zaokrąglania i nieskończoności w pakiecie funkcji matematycznych zmiennoprzecinkowych, w zależności od platformy. Można również użyć **_controlfp_s** do maskowania lub usuwania wyjątków zmiennoprzecinkowych.

Jeśli wartość *maska* jest równa 0, **_controlfp_s** pobiera słowo sterujące zmiennoprzecinkowe i przechowuje pobraną wartość w *currentControl*.

Jeśli *maska* jest różna od zera, ustawiana jest nowa wartość dla słowa sterującego: Dla dowolnego bitu, który jest ustawiony (to jest równe 1) w *masce*, odpowiedni bit w *nowym* jest używany do aktualizacji słowa sterującego. Innymi słowy, *fpcntrl* = ((*fpcntrl* & ~*Mask*) &#124; (*newControl* & *Mask*)), gdzie *fpcntrl* jest słowem kontrolnym zmiennoprzecinkowym. W tym scenariuszu *currentControl* jest ustawiona na wartość po zakończeniu zmiany; nie jest to stara wartość bitu kontrolki.

> [!NOTE]
> Domyślnie biblioteki czasu wykonywania maskuje wszystkie wyjątki zmiennoprzecinkowe.

**_controlfp_s** jest niemal identyczna z funkcją **_Control87** na platformach Intel (x86), x64 i ARM. W przypadku docelowych platform x86, x64 lub ARM można użyć **_control87** lub **_controlfp_s**.

Różnica między **_control87** i **_controlfp_s** polega na tym, jak traktują wartości nienormalne. W przypadku platform Intel (x86), x64 i ARM **_control87** może ustawiać i czyścić nienormalną maskę wyjątku operandu. **_controlfp_s** nie modyfikuje maski wyjątku dla nienormalnego operandu. Ten przykład ilustruje różnicę:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Możliwe wartości dla stałej maski (*maski*) i nowe wartości kontrolki (*newControl*) są pokazane w poniższej tabeli wartości szesnastkowych. Używaj przenośnych stałych wymienionych poniżej ( **_MCW_EM**, **_EM_INVALID**itd.) jako argumenty tych funkcji, zamiast podawać wartości szesnastkowe jawnie.

Intel (x86) — platformy pochodne obsługują nienormalne wartości wejściowe i wyjściowe na sprzęcie. Zachowanie architektury x86 polega na zachowywaniu wartości nienormalnych. Platforma ARM i platformy x64, które mają obsługę SSE2, umożliwiają przełączenie nieznormalizowanych operandów i wyników do opróżnienia lub wymuszone zero. Funkcje **_controlfp_s**, **_controlfp**i **_control87** zapewniają maskę, aby zmienić to zachowanie. Poniższy przykład demonstruje użycie tej maski:

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Na platformach ARM funkcja **_controlfp_s** ma zastosowanie do rejestru rejestru FPSCR. Na architekturach x64 ma to dotyczyć tylko Word SSE2, który jest przechowywany w rejestrze MXCSR. Na platformach firmy Intel (x86) **_controlfp_s** wpływa na słowa kontrolne zarówno dla x87, jak i SSE2, jeśli istnieją. Istnieje możliwość, że dwa słowa kontrolne mają być niespójne ze sobą (ze względu na poprzednie wywołanie [__control87_2](control87-controlfp-control87-2.md), na przykład); Jeśli występuje niespójność między dwoma słowami sterującymi, **_controlfp_s** ustawia flagę **EM_AMBIGUOUS** w *currentControl*. Jest to ostrzeżenie, że zwrócone słowo sterujące może nie reprezentować stanu obu słów sterujących zmiennoprzecinkowych.

W przypadku architektur ARM i x64 zmiana trybu nieskończoności lub precyzji zmiennoprzecinkowej nie jest obsługiwana. Jeśli Maska kontroli dokładności jest używana na platformie x64, funkcja wywołuje potwierdzenie i zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md).

Jeśli maska nie jest ustawiona poprawnie, ta funkcja generuje wyjątek nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca **EINVAL** i ustawia **errno** na **EINVAL**.

Ta funkcja jest ignorowana w przypadku użycia opcji [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md) do kompilowania, ponieważ środowisko uruchomieniowe języka wspólnego (CLR) obsługuje tylko domyślną precyzję zmiennoprzecinkową.

### <a name="mask-constants-and-values"></a>Stałe i wartości masek

W przypadku maski **_MCW_EM** czyszczenie ustawia wyjątek, który umożliwia wyjątek sprzętowy; ustawienie ukrywa wyjątek. Jeśli wystąpi **_EM_UNDERFLOW** lub **_EM_OVERFLOW** , żaden wyjątek sprzętowy nie jest zgłaszany do momentu wykonania następnej instrukcji zmiennoprzecinkowej. Aby wygenerować wyjątek sprzętowy bezpośrednio po **_EM_UNDERFLOW** lub **_EM_OVERFLOW**, wywołaj instrukcję FWAIT MASM.

|Bitowa|Wartość szesnastkowa|Stała|Wartość szesnastkowa|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (Kontrolka niezwykła)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (Maska wyjątku przerwania)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (Formant nieskończoność)<br /><br /> (Nieobsługiwane na platformach ARM lub x64).|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (Formant zaokrąglania)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (Formant dokładności)<br /><br /> (Nieobsługiwane na platformach ARM lub x64).|0x00030000|**_PC_24** (24 bity)<br /><br /> **_PC_53** (53 bitów)<br /><br /> **_PC_64** (64 bitów)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_controlfp_s**|\<float.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
