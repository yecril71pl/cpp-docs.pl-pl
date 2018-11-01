---
title: /RTC (Sprawdzanie błędów czasu wykonywania)
ms.date: 11/04/2016
f1_keywords:
- /rtc
- VC.Project.VCCLCompilerTool.SmallerTypeCheck
- VC.Project.VCCLCompilerTool.UninitializedVariableCheck
- VC.Project.VCCLCompilerTool.StackFrameCheck
- VC.Project.VCCLCompilerTool.BasicRuntimeChecks
helpviewer_keywords:
- /RTCs compiler option [C++]
- -RTC1 compiler option [C++]
- run-time errors, error checks
- -RTCu compiler option [C++]
- /RTC1 compiler option [C++]
- /RTCc compiler option [C++]
- /RTCu compiler option [C++]
- __MSVC_RUNTIME_CHECKS macro
- -RTCs compiler option [C++]
- RTCs compiler option
- RTC1 compiler option
- run-time errors, run-time checks
- run-time checks, /RTC option
- RTCu compiler option
- RTCc compiler option
- -RTCc compiler option [C++]
ms.assetid: 9702c558-412c-4004-acd5-80761f589368
ms.openlocfilehash: 77dc97ee07499b7df37a115dafafddd71acb7bb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655005"
---
# <a name="rtc-run-time-error-checks"></a>/RTC (Sprawdzanie błędów czasu wykonywania)

Używane do włączania i wyłączania funkcji Sprawdzanie błędów czasu wykonywania w połączeniu z [runtime_checks](../../preprocessor/runtime-checks.md) pragmy.

## <a name="syntax"></a>Składnia

```
/RTC1
/RTCc
/RTCs
/RTCu
```

## <a name="arguments"></a>Argumenty

**1**<br/>
Odpowiada to **usunęliśmy**`su`.

**c**<br/>
Informuje, kiedy wartość jest przypisana do mniejszego typu danych oraz powoduje utratę danych. Na przykład, jeśli wartość typu `short 0x101` jest przypisany do zmiennej typu `char`.

Ta opcja zgłasza sytuacje, w których ma być obcięta, na przykład, jeśli chcesz, aby pierwsze osiem bitów `int` zwracane jako `char`. Ponieważ **usunęliśmy** `c` powoduje błąd czasu wykonywania, jeśli wszystkie informacje są tracone w wyniku przypisania, można zamaskować off potrzebne informacje znajdziesz w celu uniknięcia błędów czasu wykonywania, na **usunęliśmy** `c`. Na przykład:

```
#include <crtdbg.h>

char get8bits(int value, int position) {
   _ASSERT(position < 32);
   return (char)(value >> position);
   // Try the following line instead:
   // return (char)((value >> position) & 0xff);
}

int main() {
   get8bits(12341235,3);
}
```

**s**<br/>
Włącza ramki błąd w czasie wykonywania sprawdzania stosu, w następujący sposób:

- Inicjalizacja zmiennych lokalnych na wartość różną od zera. Pomaga to identyfikować błędy, które nie są wyświetlane podczas pracy w trybie debugowania. Istnieje duże prawdopodobieństwo, że zmiennych stosu będą nadal zero do kompilacji debugowanej, ze względu na optymalizacje kompilatora zmiennych stosu w kompilacji wydania w porównaniu do kompilacji wydania. Gdy program został użyty obszar swój stos, nigdy nie zresetowaniu 0 przez kompilator. W związku z tym zmiennych stosu kolejne, niezainicjowanej, które zdarzają się używać tego samego obszaru stosu mogą zwracać pozostawione przez wcześniejsze korzystanie z tej pamięci stosu.

- Wykrywanie przepełnienia i underruns zmiennych lokalnych, takich jak tablice. **/ RTC** `s` nie wykrywa przepełnienia podczas uzyskiwania dostępu do pamięci, która wynika z kompilatora uzupełnienia w ramach struktury. Dopełnienie mogą wystąpić przy użyciu [wyrównać](../../cpp/align-cpp.md), [/ZP (wyrównanie członka struktury)](../../build/reference/zp-struct-member-alignment.md), lub [pakiet](../../preprocessor/pack.md), lub jeśli porządkowania elementów struktury w taki sposób, aby wymagać kompilator, aby dodać dopełnienia.

- Weryfikacja wskaźnik stosu, które wykrywa uszkodzenie wskaźnik stosu. Uszkodzenie wskaźnika stosu może być spowodowany niezgodnością konwencji wywoływania. Na przykład za pomocą wskaźnika funkcji, należy wywołać funkcję w bibliotece DLL, która jest eksportowana jako [__stdcall](../../cpp/stdcall.md) , ale deklaruje wskaźnik, aby działały jak [__cdecl](../../cpp/cdecl.md).

**u**<br/>
Raporty, gdy zmienna jest używana bez zainicjowania. Na przykład instrukcja, która generuje `C4701` mogą również generować błędów czasu wykonywania, w obszarze **usunęliśmy**`u`. Żadnych instrukcji, która generuje [ostrzeżenie kompilatora (poziom 1 i 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) wygeneruje błąd czasu wykonywania w ramach **usunęliśmy**`u`.

Jednakże należy wziąć pod uwagę następujący fragment kodu:

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

Jeśli zmienna może zostać zainicjowany, nie zostanie on zgłoszony w czasie wykonywania przez **usunęliśmy**`u`. Na przykład po zmiennej jest aliasowany przez wskaźnik, kompilator będzie nie śledzenie zmiennej i raport używa niezainicjowany. W efekcie można zainicjować zmienną przez pobranie jego adresu. & — Operator działa jak operator przypisania w takiej sytuacji.

## <a name="remarks"></a>Uwagi

Sprawdzanie błędów czasu wykonywania to sposób odnajdywania problemów w kodzie uruchomiona; Aby uzyskać więcej informacji, zobacz [porady: użycie macierzystego sprawdzania w trakcie wykonywania](/visualstudio/debugger/how-to-use-native-run-time-checks).

Jeśli kompilujesz program w wierszu polecenia przy użyciu dowolnej z **usunęliśmy** opcje kompilatora, wszelkie pragma [zoptymalizować](../../preprocessor/optimize.md) po cichu nie będzie zgodnie z instrukcjami w kodzie. Jest to spowodowane sprawdzanie błędów czasu wykonywania nie są dozwolone w kompilacji wydania (zoptymalizowany).

Należy używać **usunęliśmy** dla rozwoju kompilacji; **Usunęliśmy** nie powinny być używane dla kompilacji detalicznej. **/ RTC** nie można używać z optymalizacje kompilatora ([/O opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)). Obraz programu utworzonych za pomocą **usunęliśmy** będzie nieco większy przebiegać wolniej niż obrazu skompilowanego za pomocą **/Od** (5 procent wolniej niż **/Od** kompilacji).

Dyrektywy preprocesora __MSVC_RUNTIME_CHECKS zostanie zdefiniowana, jeśli używasz jakiejkolwiek **usunęliśmy** opcji lub [GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **generowania kodu** stronę właściwości.

1. Zmodyfikuj jedną lub obie następujące właściwości: **podstawowe sprawdzenia środowiska uruchomieniowego** lub **sprawdzania mniejszych typów**.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> właściwości.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[Instrukcje: korzystanie z macierzystego sprawdzania w trakcie wykonywania](/visualstudio/debugger/how-to-use-native-run-time-checks)