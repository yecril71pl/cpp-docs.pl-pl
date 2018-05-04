---
title: _control87 —, _controlfp —, __control87_2 — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 098e5760718e4e2d2a9063700b09d0381e76df1f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="control87-controlfp-control872"></a>_control87, _controlfp, __control87_2

Pobiera i ustawia słowa formantu zmiennoprzecinkowych. Bezpieczniejsza wersja **_controlfp —** jest dostępna; zobacz [_controlfp_s —](controlfp-s.md).

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
Nowe wartości bitowe słowa formantu.

*Maska*<br/>
Maska nowe bity słowa formantu można ustawić.

*x86_cw*<br/>
Wypełnione słowa formantu dla x87 zmiennoprzecinkowe jednostki. Przekazywanie 0 (**NULL**) można ustawić tylko słowa formantu SSE2.

*sse2_cw*<br/>
Słowa formantu SSE jednostki zmiennoprzecinkowych. Przekazywanie 0 (**NULL**) można ustawić tylko x87 kontroli programu word.

## <a name="return-value"></a>Wartość zwracana

Aby uzyskać **_control87 —** i **_controlfp —**, usługi bits w wartości zwracane wskazują stan formantu zmiennoprzecinkowych. Dla pełnej definicji usługi bits, które są zwracane przez **_control87 —**, zobacz FLOAT. H.

Aby uzyskać **__control87_2 —**, zwracana wartość wynosi 1, co oznacza Powodzenie.

## <a name="remarks"></a>Uwagi

**_Control87 —** funkcja pobiera i ustawia słowa formantu zmiennoprzecinkowych. Słowa formantu zmiennoprzecinkowe umożliwia programowi zmienić dokładność, zaokrąglania i tryby infinity w pakiecie zmiennoprzecinkowej matematyczny, w zależności od platformy. Można również użyć **_control87 —** zamaskować lub anulować maskowanie wyjątki zmiennoprzecinkowe. Jeśli wartość *maski* jest równa 0, **_control87 —** pobiera słowa formantu zmiennoprzecinkowych. Jeśli *maski* jest różna od zera, ustawiono nową wartość dla słowa formantu: dla dowolnego bit, który znajduje się na (to znaczy równą 1) w *maski*, odpowiadający mu bit *nowe* używane do aktualizowania formantu Word. Innymi słowy **fpcntrl** = ((**fpcntrl** & ~*maski*) &#124; (*nowe* & *maski*)) gdzie **fpcntrl** słowo formantu zmiennoprzecinkowych.

> [!NOTE]
> Domyślnie biblioteki wykonawczej maski wszystkie wyjątki zmiennoprzecinkowe.

**_controlfp —** jest niezależne od platformy, przenośne wersja **_control87 —**. Jest niemal identyczna z **_control87 —** funkcja x86, x64 i platformy ARM. Jeśli ma być przeznaczona dla x86, x64 lub platformy ARM, użyj **_control87 —** lub **_controlfp —**.

Różnica między **_control87 —** i **_controlfp —** znajduje się w sposób traktują NIEZNORMALIZOWANY wartości. X86, x64 i platformy ARM **_control87 —** można ustawić i wyczyść maska wyjątek Brak reprezentacji ZMIENNOPRZECINKOWEJ argumentu operacji. **_controlfp —** nie modyfikuje maska wyjątek Brak reprezentacji ZMIENNOPRZECINKOWEJ argumentu operacji. W tym przykładzie przedstawiono różnice:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

Możliwe wartości stałej maski (*maski*) oraz nowych wartości formantu (*nowe*) są wyświetlane w tabeli poniżej wartości szesnastkowe. Użyj przenośne stałe wymienione poniżej (**_MCW_EM**, **_EM_INVALID**itd) jako argumenty do tych funkcji, zamiast dostarczanie szesnastkowym wartości jawnie.

Intel pochodnych x86 platformy obsługuje NIEZNORMALIZOWANY danych wejściowych i wyjściowych wartości na liście sprzętu. X86 zachowanie jest zachowanie Brak reprezentacji ZMIENNOPRZECINKOWEJ wartości. Platforma ARM i x64 obsługiwanych platform, które mają SSE2 Włącz argumenty NIEZNORMALIZOWANY i wyniki opróżnionych lub wymusić na zero. **_Controlfp —** i **_control87 —** funkcje umożliwiać maski, aby zmienić to zachowanie. W poniższym przykładzie pokazano użycie tej maski.

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Na platformach ARM **_control87 —** i **_controlfp —** funkcje odnoszą się do rejestru FPSCR. Na x64 architektury, tylko SSE2 kontroli słowo, które są przechowywane w MXCSR dotyczy rejestru. Na x86 platform, **_control87 —** i **_controlfp —** wpływają na słowa formantu x87 i SSE2, jeśli jest obecny. Funkcja **__control87_2 —** umożliwia zarówno x87 i SSE2 liczb zmiennoprzecinkowych jednostki, aby można było nim sterować razem lub oddzielnie. Jeśli chcesz mieć wpływ na obu jednostki przekazywanie adresów dwie liczb całkowitych na **x86_cw** i **sse2_cw**. Jeśli chcesz mieć wpływ na jedną jednostkę, podaj adres dla tego parametru, ale Podaj 0 (NULL) dla innych. Jeśli 0 jest przekazywane do jednego z tych parametrów, funkcja nie ma wpływu na tej jednostce zmiennoprzecinkowych. Ta funkcja może być przydatne w sytuacjach, w których jednostki zmiennoprzecinkowe używa x87 kodu i część innego kodu używa jednostki zmiennoprzecinkowe SSE2. Jeśli używasz **__control87_2 —** w jednej części programu i ustawić różne wartości dla słowa formantu liczb zmiennoprzecinkowych, a następnie użyj **_control87 —** lub **_controlfp —** do dalszego następnie manipulowania słowa formantu **_control87 —** i **_controlfp —** może być niemożliwe do zwrócenia wyraz jeden formant do reprezentowania stan zarówno zmiennoprzecinkowe jednostki. W takim przypadku ustawić te funkcje **EM_AMBIGUOUS** flagi wartości zwrócona liczba całkowita wskazująca, czy występuje niespójność między wyrazami dwóch formantu. To ostrzeżenie, że słowa formantu zwrócony może nie mieć stan oba słowa formantu liczb zmiennoprzecinkowych dokładnie.

Na ARM i x64 architektury, zmiana trybu infinity lub zmiennoprzecinkowe dokładność nie jest obsługiwane. Jeśli maska kontroli dokładności jest używany na x64 platformy, funkcja podnosi potwierdzenia i program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).

> [!NOTE]
> **__control87_2 —** nie jest obsługiwane dla ARM lub x64 architektury. Jeśli używasz **__control87_2 —** i kompilowania programu dla ARM lub x64 architektury, kompilator generuje błąd.

Funkcje te są ignorowane, gdy używasz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) do kompilacji, ponieważ środowisko uruchomieniowe języka wspólnego (CLR) obsługuje tylko domyślna dokładność zmiennoprzecinkowych.

**Wartości szesnastkowe**

Aby uzyskać **_MCW_EM** maska wyczyszczenie maska ustawia wyjątek, dzięki czemu wyjątek sprzętu; ustawienie maski ukrywa wyjątek. Jeśli **_EM_UNDERFLOW** lub **_EM_OVERFLOW** występuje nie sprzętu wyjątku do momentu następnej instrukcji zmiennoprzecinkowych jest wykonywana. Aby wygenerować wyjątek sprzętu natychmiast po **_EM_UNDERFLOW** lub **_EM_OVERFLOW**, wywołaj **FWAIT** MASM instrukcji.

|Maska|Wartość szesnastkowa|Stała|Wartość szesnastkowa|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (Brak reprezentacji zmiennoprzecinkowej sterowania)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (maska wyjątek przerwań)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (kontrola nieskończoności)<br /><br /> (Nie jest obsługiwane dla ARM lub x64] platformy.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (zaokrąglania sterowania)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (precyzyjną kontrolę)<br /><br /> (Nie obsługiwany na ARM lub x64 platformy.)|0x00030000|**_PC_24** (24-bitowy)<br /><br /> **_PC_53** (53-bitowy)<br /><br /> **_PC_64** (64-bitowy)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_control87 —**, **_controlfp —**, **_control87_2**|\<float.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
