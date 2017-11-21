---
title: "_controlfp_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _controlfp_s
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
dev_langs: C++
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
caps.latest.revision: "28"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e5f1f82f5d7ae8899d1045280f24c7af405c64b6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="controlfps"></a>_controlfp_s
Pobiera i ustawia słowa formantu zmiennoprzecinkowych. Ta wersja [_control87 —, _controlfp —, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) zawiera ulepszenia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _controlfp_s(  
    unsigned int *currentControl,  
    unsigned int newControl,  
    unsigned int mask  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `currentControl`  
 Bieżąca wartość bitowa słowa formantu.  
  
 `newControl`  
 Nowe wartości bitowe słowa formantu.  
  
 `mask`  
 Maska nowe bity słowa formantu można ustawić.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zera w razie powodzenia lub jako `errno` wartość Kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 `_controlfp_s` Funkcji jest niezależne od platformy i bezpieczniejsze wersja `_control87`, który pobiera słowa formantu zmiennoprzecinkowych na adres, który jest przechowywany w `currentControl` i ustawia go za pomocą `newControl`. Bity w wartości wskazują stan formantu zmiennoprzecinkowych. Stan kontrolki zmiennoprzecinkowe umożliwia programowi zmienić dokładność, zaokrąglania i tryby infinity w pakiecie zmiennoprzecinkowej matematyczny, w zależności od platformy. Można również użyć `_controlfp_s` zamaskować lub anulować maskowanie wyjątki zmiennoprzecinkowe.  
  
 Jeśli wartość `mask` jest równa 0, `_controlfp_s` pobiera słowa formantu zmiennoprzecinkowych i zapisuje pobranej wartości w `currentControl`.  
  
 Jeśli `mask` jest różna od zera, ustawiono nową wartość dla słowa formantu: dla dowolnego bit, który jest ustawiony (to znaczy równą 1) w `mask`, odpowiadający mu bit `new` używane do aktualizowania słowa formantu. Innymi słowy `fpcntrl` `=` ((`fpcntrl` `& ~mask`) &#124; (`new & mask`)) gdzie `fpcntrl` jest słowa formantu zmiennoprzecinkowych. W tym scenariuszu `currentControl` ma ustawioną wartość po ukończeniu zmieniania; nie jest stara wartość bitowa słowa formantu.  
  
> [!NOTE]
>  Domyślnie biblioteki wykonawczej maski wszystkie wyjątki zmiennoprzecinkowe.  
  
 `_controlfp_s`jest niemal identyczna z `_control87` funkcja na Intel (x86), [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]i platformy ARM. Jeśli aplikacja jest przeznaczona dla x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], albo użyć platformy ARM `_control87` lub `_controlfp_s`.  
  
 Różnica między `_control87` i `_controlfp_s` znajduje się w sposób Traktuj `DENORMAL` wartości. Dla komputerów Intel (x86) [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], platformy ARM i `_control87` można ustawić i wyczyść maska wyjątek Brak reprezentacji ZMIENNOPRZECINKOWEJ argumentu operacji. `_controlfp_s`nie modyfikować maska wyjątek Brak reprezentacji ZMIENNOPRZECINKOWEJ argumentu operacji. W tym przykładzie przedstawiono różnice:  
  
```C  
_control87( _EM_INVALID, _MCW_EM );   
// DENORMAL is unmasked by this call.  
unsigned int current_word = 0;  
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );   
// DENORMAL exception mask remains unchanged.  
```  
  
 Możliwe wartości stałej maski (`mask`) oraz nowych wartości formantu (`newControl`) są wyświetlane w tabeli poniżej wartości szesnastkowe. Użyj przenośne stałe wymienione poniżej (`_MCW_EM`, `_EM_INVALID`i tak dalej) jako argumenty do tych funkcji, zamiast dostarczanie szesnastkowym wartości jawnie.  
  
 Intel pochodnych (x86) platformy obsługuje NIEZNORMALIZOWANY danych wejściowych i wyjściowych wartości na liście sprzętu. X86 zachowanie jest zachowanie Brak reprezentacji ZMIENNOPRZECINKOWEJ wartości. Platforma ARM i [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] platformy, które obsługują SSE2 Włącz argumenty NIEZNORMALIZOWANY i wyniki opróżnione, lub na zero. `_controlfp_s`, `_controlfp`, I `_control87` funkcje umożliwiać maski, aby zmienić to zachowanie. Poniższy przykład przedstawia użycie ta maska:  
  
```C  
unsigned int current_word = 0;  
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);     
// Denormal values preserved on ARM platforms and on x64 processors with  
// SSE2 support. NOP on x86 platforms.  
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);     
// Denormal values flushed to zero by hardware on ARM platforms   
// and x64 processors with SSE2 support. Ignored on other x86 platforms.  
```  
  
 Na platformach ARM `_controlfp_s` funkcja ma zastosowanie do rejestru FPSCR. Na [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architektury, tylko SSE2 kontroli słowo, które są przechowywane w MXCSR dotyczy rejestru. Na platformach firmy Intel (x86) `_controlfp_s` wpływa na słowa formantu x87 i SSE2, jeśli jest obecny. Istnieje możliwość słowa kontrolny jest niespójny ze sobą (ze względu na poprzednie wywołanie [__control87_2 —](../../c-runtime-library/reference/control87-controlfp-control87-2.md), na przykład); Jeśli występuje niespójność między wyrazami kontrolny `_controlfp_s` ustawia `EM_AMBIGUOUS`oflagowane w `currentControl`. To ostrzeżenie, że słowa formantu zwrócony może nie mieć stan oba słowa formantu liczb zmiennoprzecinkowych dokładnie.  
  
 Na ARM i [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architektury, zmiana trybu infinity lub zmiennoprzecinkowe dokładność nie jest obsługiwane. Jeśli maska kontroli dokładności jest używany w [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] platformy, funkcja podnosi potwierdzenia i program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).  
  
 Jeśli maska nie jest poprawnie ustawiona, ta funkcja generuje wyjątek nieprawidłowy parametr zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca `EINVAL` i ustawia `errno` do `EINVAL`.  
  
 Ta funkcja jest ignorowana, korzystając z [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) do kompilacji, ponieważ środowisko uruchomieniowe języka wspólnego (CLR) obsługuje tylko domyślna dokładność zmiennoprzecinkowych.  
  
### <a name="mask-constants-and-values"></a>Stałe maski i wartości  
  
 Aby uzyskać `_MCW_EM` maska wyczyszczeniem ustawia wyjątek, dzięki czemu wyjątek sprzętu; ustawieniem dla niego ukrywa wyjątek. Jeśli `_EM_UNDERFLOW` lub `_EM_OVERFLOW` występuje nie sprzętu wyjątku do momentu następnej instrukcji zmiennoprzecinkowych jest wykonywana. Aby wygenerować wyjątek sprzętu natychmiast po `_EM_UNDERFLOW` lub `_EM_OVERFLOW`, wywołać instrukcji FWAIT MASM.  
  
|Maska|Wartość szesnastkowa|Stała|Wartość szesnastkowa|  
|----------|---------------|--------------|---------------|  
|`_MCW_DN`(Brak reprezentacji zmiennoprzecinkowej sterowania)|0x03000000|`_DN_SAVE`<br /><br /> `_DN_FLUSH`|0x00000000<br /><br /> 0x01000000|  
|`_MCW_EM`(Wyjątek maska przerwań)|0x0008001F|`_EM_INVALID`<br /><br /> `_EM_DENORMAL`<br /><br /> `_EM_ZERODIVIDE`<br /><br /> `_EM_OVERFLOW`<br /><br /> `_EM_UNDERFLOW`<br /><br /> `_EM_INEXACT`|0x00000010<br /><br /> 0X00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|  
|`_MCW_IC`(Kontrola nieskończoności)<br /><br /> (Nieobsługiwane w ARM lub [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] platformy.)|0X00040000|`_IC_AFFINE`<br /><br /> `_IC_PROJECTIVE`|0X00040000<br /><br /> 0x00000000|  
|`_MCW_RC`(Kontrola zaokrąglania)|0x00000300|`_RC_CHOP`<br /><br /> `_RC_UP`<br /><br /> `_RC_DOWN`<br /><br /> `_RC_NEAR`|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|  
|`_MCW_PC`(Kontrola dokładności)<br /><br /> (Nieobsługiwane w ARM lub [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] platformy.)|0x00030000|`_PC_24`(24-bitowy)<br /><br /> `_PC_53`(53-bitowy)<br /><br /> `_PC_64`(64-bitowy)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_controlfp_s`|\<float.h — >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
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
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [_clear87 —, _clearfp —](../../c-runtime-library/reference/clear87-clearfp.md)   
 [_status87 —, _statusfp —, _statusfp2 —](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)   
 [_control87 —, _controlfp —, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)