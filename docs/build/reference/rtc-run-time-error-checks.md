---
title: -RTC (sprawdzanie błędów czasu wykonywania) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /rtc
- VC.Project.VCCLCompilerTool.SmallerTypeCheck
- VC.Project.VCCLCompilerTool.UninitializedVariableCheck
- VC.Project.VCCLCompilerTool.StackFrameCheck
- VC.Project.VCCLCompilerTool.BasicRuntimeChecks
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a135c9c4e32ea7a54c45719eff503ff99509d3e7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378460"
---
# <a name="rtc-run-time-error-checks"></a>/RTC (Sprawdzanie błędów czasu wykonywania)
Umożliwia włączanie i wyłączanie funkcji Sprawdzanie błędów czasu wykonywania w połączeniu z [runtime_checks](../../preprocessor/runtime-checks.md) pragma.  
  
## <a name="syntax"></a>Składnia  
  
```  
/RTC1  
/RTCc  
/RTCs  
/RTCu  
```  
  
## <a name="arguments"></a>Argumenty  
 `1`  
 Odpowiednik **/RTC**`su`.  
  
 `c`  
 Informuje, kiedy wartość jest przypisany do na mniejszy typ danych i powoduje utratę danych. Na przykład, jeśli wartość typu `short 0x101` jest przypisany do zmiennej typu `char`.  
  
 Ta opcja raporty sytuacje, w których mają być truncate, na przykład, jeśli chcesz, aby pierwszych 8 bitów `int` zwracane jako `char`. Ponieważ **/RTC** `c` powoduje błąd wykonania, jeśli wszystkie informacje zostaną utracone w wyniku przypisania, można zamaskować poza informacje potrzebne, aby uniknąć błędów czasu wykonywania w **/RTC** `c`. Na przykład:  
  
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
  
 `s`  
 Umożliwia ramki błędów czasu wykonywania sprawdzania stosu, w następujący sposób:  
  
-   Inicjowanie zmiennych lokalnych jako wartość niezerową. Dzięki temu można zidentyfikować usterki, które nie są wyświetlane w trybie debugowania. Istnieje duże prawdopodobieństwo, że zmienne stosu będą nadal zero w kompilację debugowania w porównaniu do kompilacji wydania z powodu optymalizacji kompilatora zmiennych stosu w kompilacji wydania. Gdy program został użyty obszar jego stosu, jego jest przez kompilator nigdy nie zresetowana do 0. W związku z tym stosu kolejne, niezainicjowanych zmiennych, które się zdarzyć, aby użyć tego samego obszaru stosu może zwracać wartości pozostawione z wcześniejszego użycia tej pamięci stosu.  
  
-   Wykrywanie przepełnienia i underruns zmiennych lokalnych, takich jak tablic. **/ RTC** `s` nie wykrywa przepełnienia podczas uzyskiwania dostępu do pamięci, która jest wynikiem kompilatora uzupełnienia wewnątrz struktury. Dopełnienie może wystąpić przy użyciu [Dopasuj](../../cpp/align-cpp.md), [/Zp (wyrównanie członka struktury)](../../build/reference/zp-struct-member-alignment.md), lub [pakietu](../../preprocessor/pack.md), lub jeśli porządkowania elementów struktury w taki sposób, aby wymagać kompilator, aby dodać dopełnienie.  
  
-   Weryfikacji wskaźnik stosu, który wykryje uszkodzenie wskaźnika stosu. Uszkodzenie wskaźnika stosu może być spowodowane niezgodnością konwencji wywoływania. Na przykład przy użyciu wskaźnik funkcji, należy wywołać funkcję w bibliotece DLL, który został wyeksportowany jako [__stdcall](../../cpp/stdcall.md) , ale zadeklarować wskaźnika do funkcji jako [__cdecl](../../cpp/cdecl.md).  
  
 `u`  
 Informuje, kiedy zmienna jest używana bez zainicjowania. Na przykład instrukcji, które generuje `C4701` może także wygenerować błąd w czasie wykonywania w obszarze **/RTC**`u`. Żadnych instrukcji, które generuje [C4700 ostrzeżenie kompilatora (poziom 1 i 4)](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) wygeneruje błąd czasu wykonywania w obszarze **/RTC**`u`.  
  
 Jednak wziąć pod uwagę następującego fragmentu kodu:  
  
```cpp  
int a, *b, c;  
if ( 1 )  
b = &a;  
c = a;  // No run-time error with /RTCu  
```  
  
 Jeśli zmienna może została zainicjowana, nie będzie zgłaszane w czasie wykonywania przez **/RTC**`u`. Na przykład po zmienna jest aliasem za pomocą wskaźnika, kompilator będzie nie śledzić zmiennej i raport używa niezainicjowany. W efekcie można zainicjować zmiennej przez pobranie jego adresu. & Operator działa, takich jak operatora przypisania w takiej sytuacji.  
  
## <a name="remarks"></a>Uwagi  
 Sprawdzanie błędów czasu wykonywania jest sposób odnajdywania problemów w kodzie uruchomionych; Aby uzyskać więcej informacji, zobacz [porady: Użyj natywnego Run-Time sprawdza](/visualstudio/debugger/how-to-use-native-run-time-checks).  
  
 Jeśli kompilacja programu w wierszu polecenia przy użyciu dowolnego **/RTC** — opcje kompilatora, wszelkie pragma [zoptymalizować](../../preprocessor/optimize.md) instrukcje kod w trybie dyskretnym nie powiedzie się. Jest to spowodowane sprawdzanie błędów czasu wykonywania nie są dozwolone w kompilacji wydania (zoptymalizowana).  
  
 Należy używać **/RTC** dla rozwoju kompilacji; **/RTC** nie powinna być używana dla kompilacji sprzedaży detalicznej. **/ RTC** nie można używać z optymalizacji kompilatora ([/O opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)). Obraz programu skompilowanej za pomocą **/RTC** będzie nieco większy i przebiegać wolniej niż obrazu skompilowanego za pomocą **/Od** (5 procent wolniej niż **/Od** kompilacji).  
  
 Dyrektywy preprocesora __msvc_runtime_checks — zostanie zdefiniowana, jeśli korzystasz z dowolnych **/RTC** opcji lub [GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **generowania kodu** strony właściwości.  
  
4.  Zmodyfikuj jedną lub obie następujące właściwości: **podstawowe Sprawdzanie czasu wykonania** lub **mniejszych Sprawdź typ**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Porady: Użyj macierzystego sprawdzania w trakcie wykonywania](/visualstudio/debugger/how-to-use-native-run-time-checks)