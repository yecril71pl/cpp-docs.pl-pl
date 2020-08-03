---
title: /RTC (Sprawdzanie błędów czasu wykonywania)
ms.date: 07/31/2020
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
ms.openlocfilehash: eefec0956bebe9f72324f3cbc61fccbc5e2e24d7
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520541"
---
# <a name="rtc-run-time-error-checks"></a>`/RTC`(Sprawdzanie błędów czasu wykonywania)

Służy do włączania i wyłączania funkcji sprawdzania błędów czasu wykonywania w połączeniu z [runtime_checks](../../preprocessor/runtime-checks.md) pragma.

## <a name="syntax"></a>Składnia

> **`/RTC1`**\
> **`/RTCc`**\
> **`/RTCs`**\
> **`/RTCu`**

## <a name="arguments"></a>Argumenty

**`/RTC1`**<br/>
Odpowiednik **`/RTCsu`** .

**`/RTCc`**<br/>
Raportuje, gdy wartość jest przypisana do mniejszego typu danych i powoduje utratę danych. Na przykład raport jest zgłaszany, jeśli **`short`** wartość typu `0x0101` jest przypisana do zmiennej typu **`char`** .

Ta opcja może raportować sytuacje, w których zamierzasz obciąć. Na przykład, jeśli chcesz, aby pierwsze 8 bitów **`int`** zwrócone jako **`char`** . Ponieważ **`/RTCc`** powoduje błąd czasu wykonywania, jeśli przypisanie powoduje utratę informacji, najpierw należy zamaskować informacje, które są potrzebne, aby uniknąć błędu czasu wykonywania. Na przykład:

```C
#include <crtdbg.h>

char get8bits(unsigned value, int position) {
   _ASSERT(position < 32);
   return (char)(value >> position);
   // Try the following line instead:
   // return (char)((value >> position) & 0xff);
}

int main() {
   get8bits(12341235,3);
}
```

Ponieważ **`/RTCc`** odrzuca kod, który jest zgodny ze standardem, nie jest obsługiwany przez standardową bibliotekę języka C++. Kod, który używa **`/RTCc`** i biblioteki standardowej języka C++ może spowodować błąd kompilatora [C1189](../../error-messages/compiler-errors-1/fatal-error-c1189.md). Można zdefiniować, `_ALLOW_RTCc_IN_STL` Aby wyciszyć ostrzeżenie i użyć **`/RTCc`** opcji.

**`/RTCs`**<br/>
Włącza sprawdzanie błędów czasu wykonywania ramki stosu w następujący sposób:

- Inicjalizacja zmiennych lokalnych na wartość różną od zera. Ta opcja pomaga identyfikować usterki, które nie są wyświetlane podczas działania w trybie debugowania. Istnieje większa szansa, że zmienne stosu nadal mają wartość zerową w kompilacji debugowania w porównaniu do kompilacji wydania. Jest to spowodowane optymalizacją kompilatora zmiennych stosu w kompilacji wydania. Gdy program używa obszaru jego stosu, nigdy nie jest resetowany do 0 przez kompilator. Oznacza to, że wszelkie Niezainicjowane zmienne stosu, które wystąpiły w celu użycia tego samego obszaru stosu później, mogą zwrócić wartości pozostawione przed wcześniejszym użyciem tej pamięci stosu.

- Wykrywanie przekroczeń i niedziałających zmiennych lokalnych, takich jak tablice. **`/RTCs`** nie wykrywa przekroczeń podczas uzyskiwania dostępu do pamięci, która wynika z dopełnienia kompilatora w obrębie struktury. Uzupełnienie może wystąpić przy użyciu [`align`](../../cpp/align-cpp.md) , [ `/Zp` (wyrównanie składowej struktury)](zp-struct-member-alignment.md), lub [`pack`](../../preprocessor/pack.md) , lub jeśli planujesz elementy struktury w taki sposób, aby wymagało, aby kompilator dodał uzupełnienie.

- Weryfikacja wskaźnika stosu, która wykrywa uszkodzenie wskaźnika stosu. Uszkodzenie wskaźnika stosu może być spowodowane niezgodnością konwencji wywoływania. Na przykład przy użyciu wskaźnika funkcji można wywołać funkcję w bibliotece DLL, która jest eksportowana jako, [`__stdcall`](../../cpp/stdcall.md) ale deklaruje wskaźnik do funkcji jako [`__cdecl`](../../cpp/cdecl.md) .

**`/RTCu`**<br/>
Raportuje, gdy zmienna jest używana bez zainicjowania. Na przykład instrukcja generująca ostrzeżenie C4701 może również generować błąd czasu wykonywania w ramach **`/RTCu`** . Wszystkie instrukcje, które generują [Ostrzeżenie kompilatora (poziom 1 i poziom 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) wygenerują błąd w czasie wykonywania **`/RTCu`** .

Jednak Rozważmy następujący fragment kodu:

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

Jeśli zmienna mogła zostać zainicjowana, nie jest raportowana w czasie wykonywania przez **`/RTCu`** . Na przykład gdy zmienna jest aliasem za pośrednictwem wskaźnika, kompilator nie śledzi zmiennej i nie zainicjowano użycia. W efekcie można zainicjować zmienną, przyjmując jej adres. **`&`** Operator działa jak operator przypisania w tej sytuacji.

## <a name="remarks"></a>Uwagi

Kontrole błędów czasu wykonywania są sposobem na znalezienie problemów w uruchomionym kodzie; Aby uzyskać więcej informacji, zobacz [jak: korzystanie z natywnych testów w czasie wykonywania](/visualstudio/debugger/how-to-use-native-run-time-checks).

W wierszu polecenia można określić więcej niż jedną **`/RTC`** opcję. Argumenty opcji mogą być połączone; na przykład **`/RTCcu`** jest taka sama jak **`/RTCc /RTCu`** .

Jeśli kompilujesz program w wierszu polecenia przy użyciu dowolnej **`/RTC`** opcji kompilatora, wszelkie instrukcje pragma [`optimize`](../../preprocessor/optimize.md) w kodzie dyskretnie kończą się niepowodzeniem. Wynika to z faktu, że sprawdzanie błędów czasu wykonywania nie jest prawidłowe w kompilacji wersji (zoptymalizowanej).

Używane **`/RTC`** na potrzeby kompilacji programistycznych; Nie używaj **`/RTC`** w przypadku kompilacji wydania. **`/RTC`** nie można używać z optymalizacjami kompilatora ([ `/O` Opcje (Optymalizuj kod)](o-options-optimize-code.md)). Utworzony obraz programu **`/RTC`** jest nieco większy i nieco wolniejszy od obrazu skompilowanego **`/Od`** (do 5 procent wolniej niż **`/Od`** Kompilacja).

`__MSVC_RUNTIME_CHECKS`Dyrektywa preprocesora zostanie zdefiniowana w przypadku użycia dowolnej **`/RTC`** opcji lub [`/GZ`](gz-enable-stack-frame-run-time-error-checking.md) .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja**generowania kodu** **C/C++**.  

1. Zmodyfikuj jedną lub obie następujące właściwości: **podstawowe testy środowiska uruchomieniowego** lub **mniejszego typu**.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> właściwości.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Instrukcje: korzystanie z macierzystego sprawdzania w trakcie wykonywania](/visualstudio/debugger/how-to-use-native-run-time-checks)
