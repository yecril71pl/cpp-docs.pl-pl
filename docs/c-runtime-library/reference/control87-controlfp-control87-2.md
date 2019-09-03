---
title: _control87, _controlfp, __control87_2
ms.date: 08/29/2019
apiname:
- _control87
- _controlfp
- __control87_2
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
- _control87
- __control87_2
- control87
- _controlfp
- controlfp
- control87_2
- _control87_2
helpviewer_keywords:
- floating-point numbers, control word
- _control87 function
- control87 function
- controlfp function
- _controlfp function
- __control87_2 function
- floating-point functions, setting control word
- floating-point functions
- EM_AMBIGUOUS
- control87_2 function
ms.assetid: 0d09729d-d9a0-43d6-864c-43ff25e7e0c5
ms.openlocfilehash: 75b2870543ec3ddd20d445a492ad4270b91e80d7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218417"
---
# <a name="_control87-_controlfp-__control87_2"></a>_control87, _controlfp, __control87_2

Pobiera i ustawia słowo sterujące zmiennoprzecinkowe. Dostępna jest bezpieczniejsza wersja **_controlfp** ; Zobacz [_controlfp_s](controlfp-s.md).

## <a name="syntax"></a>Składnia

```C
unsigned int _control87(
   unsigned int new,
   unsigned int mask
);
unsigned int _controlfp(
   unsigned int new,
   unsigned int mask
);
int __control87_2(
   unsigned int new,
   unsigned int mask,
   unsigned int* x86_cw,
   unsigned int* sse2_cw
);
```

### <a name="parameters"></a>Parametry

*Nowy*\
Nowe wartości bitowe programu Control-Word.

*bitowa*\
Maska dla nowego tekstu kontrolki do ustawienia.

*x86_cw*\
Wypełniane za pomocą słowa Control dla jednostki zmiennoprzecinkowej x87. Przekaż wartość 0 (**null**), aby ustawić tylko słowo SSE2 Control.

*sse2_cw*\
Słowo kontrolne dla jednostki zmiennoprzecinkowej SSE. Przekaż wartość 0 (**null**), aby ustawić tylko słowo x87 Control.

## <a name="return-value"></a>Wartość zwracana

W przypadku **_control87** i **_controlfp**bity w zwracanej wartości wskazują stan kontroli zmiennoprzecinkowej. Aby uzyskać pełną definicję bitów, które są zwracane przez **_control87**, zobacz float. C.

Dla **__control87_2**wartość zwracana wynosi 1, co oznacza powodzenie.

## <a name="remarks"></a>Uwagi

Funkcja **_control87** pobiera i ustawia słowo sterujące zmiennoprzecinkowe. Słowo sterujące zmiennoprzecinkowe umożliwia programowi zmianę dokładności, zaokrąglenie i nieskończoność, w zależności od platformy. Można również użyć **_control87** do maskowania lub usuwania wyjątków zmiennoprzecinkowych. Jeśli wartość *maska* jest równa 0, **_control87** pobiera słowo sterujące zmiennoprzecinkowe. Jeśli *maska* jest różna od zera, ustawiana jest nowa wartość dla słowa sterującego: Dla każdego bitu, który jest włączony (to jest równe 1) w *masce*, odpowiedni bit w *nowym* jest używany do aktualizacji słowa sterującego. Innymi słowy, **fpcntrl** = ((**fpcntrl** & ~*Mask*) &#124; (*Nowa* & *maska*)), gdzie **fpcntrl** to słowo sterujące zmiennoprzecinkowe.

> [!NOTE]
> Domyślnie biblioteki czasu wykonywania maskuje wszystkie wyjątki zmiennoprzecinkowe.

**_controlfp** to niezależna od platformy, Przenośna wersja **_control87** , która jest niemal identyczna z funkcją **_control87** . Jeśli Twój kod ma więcej niż jedną platformę, użyj **_controlfp** lub **_controlfp_s**. Różnica między **_control87** i **_controlfp** polega na tym, jak traktują wartości nienormalne. W przypadku platform x86, x64, ARM i ARM64, **_control87** może ustawić i wyczyścić maskę wyjątku operandu. **_controlfp** nie modyfikuje maski wyjątku operandu. Ten przykład ilustruje różnicę:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

Możliwe wartości dla stałej maski (*maski*) i nowe wartości kontrolki (*nowe*) są wyświetlane w tabeli formantów maski i wartości programu Word. Używaj przenośnych stałych wymienionych poniżej ( **_MCW_EM**, **_EM_INVALID**i tak dalej) jako argumenty tych funkcji, zamiast podawać wartości szesnastkowe jawnie.

Platformy Intel x86 obsługują nienormalne wartości wejściowe i wyjściowe ze sprzętem. Zachowanie architektury x86 polega na zachowywaniu wartości nienormalnych. Platformy ARM i ARM64 oraz platformy x64 z obsługą SSE2 umożliwiają nienormalne operandy i wyniki, które mają być opróżniane lub wymuszane jako równe zero. Funkcje **_controlfp** i **_control87** zapewniają maskę, aby zmienić to zachowanie. Poniższy przykład demonstruje użycie tej maski.

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Na platformach ARM i ARM64 funkcje **_control87** i **_CONTROLFP** dotyczą rejestru rejestru FPSCR. Na platformach x64 mają mieć miejsce tylko wyrazy SSE2 Control, które są przechowywane w rejestrze MXCSR. Na platformach x86 **_control87** i **_controlfp** wpływają na słowa kontrolne zarówno dla x87, jak i dla SSE2, jeśli istnieją.

Funkcja **__control87_2** umożliwia bezpośrednie sterowanie jednostkami zmiennoprzecinkowymi X87 i SSE2. Aby mieć wpływ na obie jednostki, należy przekazać adresy dwóch liczb całkowitych do **x86_cw** i **sse2_cw**. Jeśli chcesz mieć wpływ tylko na jedną jednostkę, Przekaż adres dla tego parametru, ale przekaż wartość 0 (**null**). Jeśli dla jednego z tych parametrów zostanie przesłana wartość 0, funkcja nie ma wpływu na jednostkę zmiennoprzecinkową. Jest przydatne, gdy część kodu używa jednostki zmiennoprzecinkowej x87, a inna część używa jednostki zmiennoprzecinkowej SSE2.

Jeśli używasz **__control87_2** do ustawiania różnych wartości dla słów kontrolnych zmiennoprzecinkowych, wówczas **_control87** lub **_controlfp** może nie być w stanie zwrócić pojedynczego wyrazu kontrolki do reprezentowania stanu obu jednostek zmiennoprzecinkowych. W takim przypadku te funkcje ustawiają flagę **EM_AMBIGUOUS** w zwracanej wartości całkowitej, aby wskazać niespójność między dwoma wyrazami kontrolnymi. Flaga **EM_AMBIGUOUS** jest ostrzeżeniem, że zwrócone słowo sterujące może nie reprezentować stanu obu słów sterujących zmiennoprzecinkowych.

Na platformach ARM, ARM64 i x64 zmiana trybu nieskończoności lub precyzji zmiennoprzecinkowej nie jest obsługiwana. Jeśli Maska kontroli dokładności jest używana na platformie x64, funkcja wywołuje potwierdzenie i zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w walidacji [parametru](../../c-runtime-library/parameter-validation.md).

> [!NOTE]
> **__control87_2** nie jest obsługiwana na platformach ARM, arm64 lub x64. W przypadku korzystania z **__control87_2** i kompilowania programu dla platform ARM, arm64 lub x64 kompilator generuje błąd.

Te funkcje są ignorowane w przypadku kompilowania przy użyciu opcji [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md) . Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje tylko domyślną precyzję zmiennoprzecinkową.

### <a name="control-word-masks-and-values"></a>Kontrolowanie masek i wartości w programie Word

W przypadku maski **_MCW_EM** czyszczenie maski ustawia wyjątek, który umożliwia wyjątek sprzętowy; ustawienie maski ukrywa wyjątek. Jeśli wystąpi **_EM_UNDERFLOW** lub **_EM_OVERFLOW** , żaden wyjątek sprzętowy nie jest zgłaszany do momentu wykonania następnej instrukcji zmiennoprzecinkowej. Aby wygenerować wyjątek sprzętowy bezpośrednio po **_EM_UNDERFLOW** lub **_EM_OVERFLOW**, wywołaj instrukcję **FWAIT** MASM.

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
|**_control87**, **_controlfp**, **_control87_2**|\<float.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_cntrl87.c
// processor: x86
// compile by using: cl /W4 /arch:IA32 crt_cntrl87.c
// This program uses __control87_2 to output the x87 control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word_x87 = 0;
    int result;

    // Show original x87 control word and do calculation.
    result = __control87_2(0, 0, &control_word_x87, 0 );
    printf( "Original: 0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    result = __control87_2(_PC_24, MCW_PC, &control_word_x87, 0 );
    printf( "24-bit:   0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    result = __control87_2( _CW_DEFAULT, MCW_PC, &control_word_x87, 0 );
    printf( "Default:  0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
24-bit:   0x000a001f
0.1 * 0.1 = 9.999999776482582e-03
Default:  0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
```

## <a name="see-also"></a>Zobacz także

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)\
[_clear87, _clearfp](clear87-clearfp.md)\
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)\
[_controlfp_s](controlfp-s.md)
