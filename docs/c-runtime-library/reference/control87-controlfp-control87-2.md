---
title: _control87, _controlfp, __control87_2
ms.date: 04/05/2018
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
ms.openlocfilehash: e2ebfdc80a451ebf02563f78a62dd08618f92bcd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340420"
---
# <a name="control87-controlfp-control872"></a>_control87, _controlfp, __control87_2

Pobiera i ustawia słowo sterujące zmiennoprzecinkowe. Bardziej bezpieczna wersja **_controlfp** jest dostępna; zobacz [_controlfp_s —](controlfp-s.md).

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

*new*<br/>
Nowe wartości bitowe słowa sterującego.

*Maska*<br/>
Maska dla nowych bitów słowa kontrolującego do ustawienia.

*x86_cw*<br/>
Wypełniony wyrazem sterującym dla x87 jednostki zmiennoprzecinkowej. Przenieść 0 (**NULL**) można ustawić tylko wyraz kontroli SSE2.

*sse2_cw*<br/>
Słowo sterujące dla jednostki zmiennoprzecinkowej SSE. Przenieść 0 (**NULL**) można ustawić x87 słowo sterujące.

## <a name="return-value"></a>Wartość zwracana

Aby uzyskać **_control87 —** i **_controlfp**, bity w wartości zwracanej, wskazują stan sterowania zmiennoprzecinkowego. Aby uzyskać pełną definicję bitów, które są zwracane przez **_control87 —**, zobacz FLOAT. H.

Aby uzyskać **__control87_2**, wartość zwracana wynosi 1, co wskazuje sukces.

## <a name="remarks"></a>Uwagi

**_Control87 —** funkcja pobiera i ustawia słowo sterujące zmiennoprzecinkowe. Słowo sterowania zmiennoprzecinkowego Włącza program do zmiany precyzji, zaokrąglania oraz trybu nieskończoności w pakiecie zmiennoprzecinkowym zapisu matematycznego, w zależności od platformy. Można również użyć **_control87 —** do zamaskowania lub usunięcia wyjątki zmiennoprzecinkowe. Jeśli wartość *maski* jest równa 0, **_control87 —** pobiera słowo sterujące zmiennoprzecinkowe. Jeśli *maski* jest różna od zera, ustawiono nową wartość dla słowa sterującego: Dla dowolnego bit, który znajduje się na (czyli wynosi 1) w *maski*, odpowiadający mu bit w *nowe* służy do aktualizacji słowa sterującego. Innymi słowy **fpcntrl** = ((**fpcntrl** & ~*maski*) &#124; (*nowe* & *maski*)) gdzie **fpcntrl** jest słowem sterującym zmiennoprzecinkowym.

> [!NOTE]
> Domyślnie bibliotek środowiska uruchomieniowego maskują wszystkie wyjątki zmiennoprzecinkowe.

**_controlfp** jest niezależny od platformy, przenośną wersją **_control87 —**. Jest prawie identyczna **_control87 —** funkcji na platformach ARM, x64 i x86. Jeśli obiektem docelowym x86, x64 lub platformy ARM, użyj **_control87 —** lub **_controlfp**.

Różnica między **_control87 —** i **_controlfp** znajduje się w jaki sposób traktuje wartości DENORMAL. X86, x64 i platform ARM **_control87 —** można ustawić lub wyczyścić maskę wyjątku ZDENORMALIZOWANY OPERAND. **_controlfp** nie modyfikuje maski wyjątku DENORMALIZACJA OPERANDU. Ten przykład ilustruje różnicę:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

Możliwe wartości dla stałej maski (*maski*) i nowe wartości formantu (*nowe*) są wyświetlane w poniższej tabeli wartości szesnastkowych. Używanie przenośnych stałych wymienionych poniżej (**_MCW_EM**, **_EM_INVALID**, i tak dalej) jako argumenty tych funkcji, a nie dostarczanie szesnastkowych wartości jawnie.

Intel x86-platformy obsługuje danych wejściowych DENORMAL i wyjściowych wartości na liście sprzętu. X86 ma zachować wartości DENORMAL. Platforma ARM i x64 obsługiwanych platform, które mają SSE2 Włącz DENORMAL i wyników do należy, lub wymuszają zero. **_Controlfp** i **_control87 —** funkcje zapewniają maskę, aby zmienić to zachowanie. Poniższy przykład demonstruje użycie tej maski.

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Na platformach ARM **_control87 —** i **_controlfp** funkcje odnoszą się do rejestru fpscr. Na x64 architektury, tylko wyraz kontroli SSE2, który jest przechowywany w mxcsr rejestru ma wpływ. Na x86 platformach **_control87 —** i **_controlfp** wpływa na wyrazy sterowania zarówno dla x87 i SSE2, jeśli jest obecny. Funkcja **__control87_2** umożliwia x87 i jednostki zmiennoprzecinkowej SSE2 będą kontrolowane, razem lub oddzielnie. Jeśli chcesz mieć wpływ na obie jednostki, przejdź w adresach dwóch liczb całkowitych do **x86_cw** i **sse2_cw**. Jeśli chcesz mieć wpływ na jedną jednostkę, Przekaż adres dla tego parametru, ale Przekaż 0 (**NULL**) dla siebie. Jeśli dla jednego z tych parametrów jest przekazywane 0, funkcja nie ma wpływu na tę jednostkę zmiennoprzecinkową. Ta funkcja może być przydatna w sytuacjach, gdzie jednostka zmiennoprzecinkowa używa x87 kodu i innego część kodu używa jednostki zmiennoprzecinkowej SSE2. Jeśli używasz **__control87_2** w jednej części programu i ustawiasz różne wartości dla słów sterujących zmiennoprzecinkowych, a następnie użyj **_control87 —** lub **_controlfp** , aby bardziej szczegółowo następnie manipulować słowo sterujące **_control87 —** i **_controlfp** może nie być w stanie zwrócić pojedynczego słowa sterującego do reprezentowania stanu obu jednostek zmiennoprzecinkowych. W takim przypadku te funkcje ustawiają **obiekt EM_AMBIGUOUS** flagi w zwracanej wartości liczby całkowitej do wskazania, że występuje niespójność między dwoma słowami sterującymi. To ostrzeżenie, że wyraz zwróconego formantu może reprezentują dokładnie stanu obu wyrazów zmiennoprzecinkowych formantu.

Na ARM i x64 architektury, zmiana trybu nieskończoności lub Zwiększanie dokładności nie jest obsługiwane. Jeśli używana jest maska kontroli dokładności, na x64 platformy, funkcja wywołuje potwierdzenie i procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md).

> [!NOTE]
> **__control87_2** nie jest obsługiwana na ARM lub x64 architektury. Jeśli używasz **__control87_2** i kompilujesz program dla ARM lub x64 architektury, kompilator generuje błąd.

Funkcje te są ignorowane, gdy używasz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) do kompilacji ponieważ środowisko uruchomieniowe języka wspólnego (CLR) obsługuje tylko domyślną precyzję zmiennoprzecinkową.

**Wartości szesnastkowe**

Aby uzyskać **_MCW_EM** maska, czyszczenie maski ustawia wyjątek, który umożliwia wyjątek sprzętowy; ustawienie maski ukrywa wyjątek. Jeśli **_EM_UNDERFLOW** lub **_EM_OVERFLOW** problem wystąpi, żaden wyjątek sprzętowy nie jest zgłaszany do momentu następnej instrukcji zmiennoprzecinkowej jest wykonywany. Do generowania wyjątków sprzętowych natychmiast po **_EM_UNDERFLOW** lub **_EM_OVERFLOW**, wywołaj **FWAIT** instrukcji MASM.

|Maska|Wartość szesnastkowa|Stała|Wartość szesnastkowa|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (formant zdenormalizowany)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (maska wyjątku przerwania)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (formant nieskończoność)<br /><br /> (Nie jest obsługiwana na ARM lub x64] platformy.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (formant zaokrąglenia)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (formant precyzji)<br /><br /> (Nie obsługiwany na ARM lub x64 platformy.)|0x00030000|**_PC_24** (24 bity)<br /><br /> **_PC_53** (53-bitowy)<br /><br /> **_PC_64** (64-bitowy)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_control87**, **_controlfp**, **_control87_2**|\<float.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_cntrl87.c
// processor: x86
// This program uses __control87_2 to output the x87 control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word_x87;

    // Show original x87 control word and do calculation.
    control_word_x87 = __control87_2(0, 0,
                                     &control_word_x87, 0);
    printf( "Original: 0x%.4x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    control_word_x87 = __control87_2(_PC_24, MCW_PC,
                                     &control_word_x87, 0);
    printf( "24-bit:   0x%.4x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    control_word_x87 = __control87_2( _CW_DEFAULT, MCW_PC,
                                     &control_word_x87, 0 );
    printf( "Default:  0x%.4x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x0001
0.1 * 0.1 = 1.000000000000000e-002
24-bit:   0x0001
0.1 * 0.1 = 9.999999776482582e-003
Default:  0x0001
0.1 * 0.1 = 1.000000000000000e-002
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
