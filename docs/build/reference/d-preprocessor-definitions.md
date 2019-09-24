---
title: /D (Definicje preprocesora)
ms.date: 09/18/2019
f1_keywords:
- VC.Project.VCNMakeTool.PreprocessorDefinitions
- VC.Project.VCCLCompilerTool.PreprocessorDefinitions
- /d
helpviewer_keywords:
- preprocessor definition symbols
- constants, defining
- macros, compiling
- /D compiler option [C++]
- -D compiler option [C++]
- D compiler option [C++]
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
ms.openlocfilehash: b10d611d38508f5696dd3b72fb8458e9b61082c8
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230400"
---
# <a name="d-preprocessor-definitions"></a>/D (Definicje preprocesora)

Definiuje symbol przetwarzania wstępnego dla pliku źródłowego.

## <a name="syntax"></a>Składnia

> **/D** ]nazwa | [`=` *[{* Number} ]] \`#`  | \[
> **/D** \[ ]nazwa [[{`=`Number}]]  |  `"``#`  | `"`

## <a name="remarks"></a>Uwagi

Możesz użyć tego symbolu razem z `#if` lub `#ifdef` , aby warunkowo kompilować kod źródłowy. Definicja symbolu będzie obowiązywać do momentu jego ponownego zdefiniowania w kodzie lub jest niezdefiniowana w kodzie przez `#undef` dyrektywę.

**/D** ma ten sam skutek jak `#define` dyrektywa na początku pliku kodu źródłowego. Różnica polega na tym, że **/d** paski cudzysłowu w wierszu polecenia, a `#define` dyrektywa utrzymuje je. Można mieć odstęp między **/d** i symbolem. Między symbolem i znakiem równości nie mogą występować znaki odstępu lub między przypisanym znakiem równości i dodaną wartością.

Domyślnie wartość skojarzona z symbolem to 1. Na przykład `/D name` jest `/D name=1`równoważne. W przykładzie na końcu tego artykułu definicja `TEST` jest pokazywana do drukowania. `1`

Kompilowanie przy `/D name=` użyciu powoduje, że *Nazwa* symbolu nie ma skojarzonej wartości. Mimo że nadal można używać symbolu, aby warunkowo skompilować kod, szacuje się on na wartość nothing. W przykładzie, Jeśli kompilujesz przy użyciu `/DTEST=`, wystąpi błąd. Takie zachowanie jest podobne do użycia `#define` z lub bez wartości.

**/D** opcja nie obsługuje definicji makra przypominającego funkcję. Aby wstawić definicje, których nie można zdefiniować w wierszu polecenia, należy rozważyć opcję kompilatora [/Fi (nazwa wymuszonego dołączenia pliku)](fi-name-forced-include-file.md) .

Można użyć **/d** wiele razy w wierszu polecenia, aby zdefiniować dodatkowe symbole. Jeśli ten sam symbol jest zdefiniowany więcej niż raz, używana jest ostatnia definicja.

To polecenie definiuje symbol DEBUG w TEST.c:

```cmd
CL /DDEBUG TEST.C
```

To polecenie usuwa wszystkie wystąpienia słowa kluczowego `__far` w test. c:

```cmd
CL /D __far= TEST.C
```

Nie można ustawić zmiennej środowiskowej **CL** na ciąg, który zawiera znak równości. Aby użyć **/d** wraz ze zmienną środowiskową **CL** , należy określić znak numeru (`#`) zamiast znaku równości:

```cmd
SET CL=/DTEST#0
```

Podczas definiowania symbolu przetwarzania wstępnego w wierszu polecenia, należy wziąć pod uwagę reguły analizy składni zarówno kompilatora, jak i powłoki. Na przykład, aby zdefiniować symbol wstępnego przetwarzania (`%`) w programie, należy określić dwa znaki procentu (`%%`) w wierszu polecenia. Jeśli określisz tylko jeden, zostanie wyemitowany błąd analizy.

```cmd
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać więcej informacji, [Zobacz C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. W lewym okienku wybierz **Właściwości konfiguracji**, **CC++/** , **preprocesora**.

1. W prawym okienku w kolumnie po prawej stronie właściwości **Definicje preprocesora** Otwórz menu rozwijane i wybierz polecenie **Edytuj**.

1. W oknie dialogowym **Definicje preprocesora** Dodaj (po jednej na wiersz), Modyfikuj lub Usuń jedną lub więcej definicji. Wybierz **przycisk OK** , aby zapisać zmiany.

   Nie musisz zawierać prefiksu opcji "/D" w definicjach określonych w tym miejscu. Na stronie właściwości definicje są oddzielone średnikami (`;`).

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>.

## <a name="example"></a>Przykład

```cpp
// cpp_D_compiler_option.cpp
// compile with: cl /EHsc /DTEST cpp_D_compiler_option.cpp
#include <stdio.h>

int main( )
{
#ifdef TEST
    printf_s("TEST defined %d\n", TEST);
#else
    printf_s("TEST not defined\n");
#endif
}
```

```Output
TEST defined 1
```

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)\
[/FI (nazwa pliku wymuszonego dołączenia)](fi-name-forced-include-file.md)\
[/U,/u (Usuń definicje symboli)](u-u-undefine-symbols.md)\
[#undef — dyrektywa (CC++/)](../../preprocessor/hash-undef-directive-c-cpp.md)\
[#define, dyrektywa (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)
