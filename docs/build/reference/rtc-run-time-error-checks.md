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
ms.openlocfilehash: 49f0e4bace5f3dd199b58854e838204bd2cd5f3b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222020"
---
# <a name="rtc-run-time-error-checks"></a>/RTC (Sprawdzanie błędów czasu wykonywania)

Służy do włączania i wyłączania funkcji sprawdzania błędów czasu wykonywania w połączeniu z [runtime_checks](../../preprocessor/runtime-checks.md) pragma.

## <a name="syntax"></a>Składnia

```
/RTC1
/RTCc
/RTCs
/RTCu
```

## <a name="arguments"></a>Argumenty

**1**<br/>
Odpowiednik **/RTC** `su` .

**s**<br/>
Raportuje, gdy wartość jest przypisana do mniejszego typu danych i powoduje utratę danych. Na przykład jeśli wartość typu `short 0x101` jest przypisana do zmiennej typu **`char`** .

Ta opcja zgłasza sytuacje, w których zamierzasz obciąć, na przykład jeśli chcesz, aby pierwsze osiem bitów **`int`** zwrócone jako **`char`** . Ponieważ **/RTC** `c` powoduje błąd czasu wykonywania, jeśli dowolna informacja zostanie utracona w wyniku przypisania, można zamaskować informacje, które są potrzebne, aby uniknąć błędu czasu wykonywania w wyniku **/RTC** `c` . Na przykład:

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

**wolumin**<br/>
Włącza sprawdzanie błędów czasu wykonywania ramki stosu w następujący sposób:

- Inicjalizacja zmiennych lokalnych na wartość różną od zera. Ułatwia to zidentyfikowanie usterek, które nie są wyświetlane podczas działania w trybie debugowania. Istnieje większa szansa, że zmienne stosu nadal będą zerem w kompilacji debugowania w porównaniu do kompilacji wydania z powodu optymalizacji kompilatora zmiennych stosu w kompilacji wydania. Gdy program używa obszaru jego stosu, nigdy nie jest resetowany do 0 przez kompilator. W związku z tym kolejne Niezainicjowane zmienne stosu, które wystąpiły w celu użycia tego samego obszaru stosu, mogą zwracać wartości pozostawione przez poprzednie użycie tej pamięci stosu.

- Wykrywanie przekroczeń i niedziałających zmiennych lokalnych, takich jak tablice. **/RTC** `s` nie wykrywa przekroczeń podczas uzyskiwania dostępu do pamięci, która wynika z dopełnienia kompilatora w obrębie struktury. Dopełnienie może wystąpić przy użyciu [align](../../cpp/align-cpp.md), [/ZP (wyrównanie składowej struktury)](zp-struct-member-alignment.md)lub [Pack](../../preprocessor/pack.md), lub jeśli planujesz elementy struktury w taki sposób, aby wymagało, aby kompilator dodał uzupełnienie.

- Weryfikacja wskaźnika stosu, która wykrywa uszkodzenie wskaźnika stosu. Uszkodzenie wskaźnika stosu może być spowodowane niezgodnością konwencji wywoływania. Na przykład przy użyciu wskaźnika funkcji można wywołać funkcję w bibliotece DLL, która jest eksportowana jako [__stdcall](../../cpp/stdcall.md) ale deklaruje wskaźnik do funkcji jako [__cdecl](../../cpp/cdecl.md).

**'t**<br/>
Raportuje, gdy zmienna jest używana bez zainicjowania. Na przykład instrukcja, która generuje `C4701` może również generować błąd czasu wykonywania w obszarze **/RTC** `u` . Wszystkie instrukcje, które generują [Ostrzeżenie kompilatora (poziom 1 i poziom 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) wygenerują błąd czasu wykonywania w obszarze **/RTC** `u` .

Jednak Rozważmy następujący fragment kodu:

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

Jeśli zmienna mogła zostać zainicjowana, nie będzie raportowana w czasie wykonywania przez **/RTC** `u` . Na przykład po zastosowaniu aliasu zmiennej przez wskaźnik kompilator nie śledzi zmiennej i nie zainicjowano użycia. W efekcie można zainicjować zmienną, przyjmując jej adres. Operator & działa jak operator przypisania w tej sytuacji.

## <a name="remarks"></a>Uwagi

Kontrole błędów czasu wykonywania są sposobem na znalezienie problemów w uruchomionym kodzie; Aby uzyskać więcej informacji, zobacz [jak: korzystanie z natywnych testów w czasie wykonywania](/visualstudio/debugger/how-to-use-native-run-time-checks).

Jeśli kompilujesz program w wierszu polecenia przy użyciu dowolnych opcji kompilatora **/RTC** , wszelkie dyrektywy pragma [optymalizują](../../preprocessor/optimize.md) instrukcje w kodzie w trybie dyskretnym. Wynika to z faktu, że testy błędów czasu wykonywania nie są prawidłowe w kompilacji wersji (zoptymalizowanej).

Należy używać **/RTC** na potrzeby kompilacji programistycznych; **/RTC** nie należy używać w przypadku kompilacji detalicznej. **/RTC** nie można używać z optymalizacjami kompilatora ([/O opcje (Optymalizuj kod)](o-options-optimize-code.md)). Obraz programu utworzony za pomocą **/RTC** będzie nieco większy i nieco wolniejszy od obrazu skompilowanego z **/od** (do 5 procent wolniej niż kompilacja **/od** ).

Dyrektywa preprocesora __MSVC_RUNTIME_CHECKS zostanie zdefiniowana w przypadku używania dowolnej opcji **/RTC** lub [/GZ](gz-enable-stack-frame-run-time-error-checking.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **C/C++** .

1. Kliknij stronę właściwości **generowanie kodu** .

1. Zmodyfikuj jedną lub obie następujące właściwości: **podstawowe testy środowiska uruchomieniowego** lub **mniejszego typu**.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> właściwości.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Instrukcje: korzystanie z natywnych testów w czasie wykonywania](/visualstudio/debugger/how-to-use-native-run-time-checks)
