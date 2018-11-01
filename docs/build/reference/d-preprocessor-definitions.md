---
title: /D (Definicje preprocesora)
ms.date: 11/04/2016
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
ms.openlocfilehash: 21836d2842427581cc5019a42c563a78356d1ec2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620509"
---
# <a name="d-preprocessor-definitions"></a>/D (Definicje preprocesora)

Definiuje symbol przetwarzania wstępnego dla pliku źródłowego.

## <a name="syntax"></a>Składnia

```
/Dname[= | # [{string | number}] ]
```

## <a name="remarks"></a>Uwagi

Można użyć tego symbolu wraz z `#if` lub `#ifdef` aby warunkowo skompilować kod źródłowy. Definicja symbolu pozostaje, dopóki zostanie ponownie zdefiniowana w kodzie lub nie jest zdefiniowana w kodzie przez `#undef` dyrektywy.

**/D** ma taki sam skutek jak `#define` dyrektywę na początku pliku kodu źródłowego, chyba że **/D** usuwa znaki cudzysłowu w wierszu polecenia i `#define` je zachowuje.

Domyślnie wartość skojarzona z symbolem to 1. Na przykład **/D** `name` jest odpowiednikiem **/D**`name`**= 1**. W przykładzie na końcu tego artykułu, definicja **testu** jest wyświetlany na drukowanie `1`.

Kompilowanie za pomocą **/D** `name` **=** powoduje, że symbol nie ma żadnej skojarzonej wartości. Mimo że nadal można używać symbolu, aby warunkowo skompilować kod, szacuje się on na wartość nothing. W tym przykładzie, jeśli kompilujesz przy użyciu **/DTEST =**, wystąpi błąd. To zachowanie jest podobne do stosowania `#define` z lub bez wartości.

To polecenie definiuje symbol DEBUG w TEST.c:

**CL /DDEBUG TEST. C**

To polecenie usuwa wszystkie wystąpienia słowa kluczowego `__far` w TEST.c:

**CL /D__far = TEST. C**

**CL** zmienna środowiskowa nie można ustawić na ciąg, który zawiera znaku równości. Aby użyć **/D** wraz z **CL** środowiska zmiennych, należy określić znak numeru zamiast znaku równości:

```
SET CL=/DTEST#0
```

Podczas definiowania symbolu przetwarzania wstępnego w wierszu polecenia, należy wziąć pod uwagę reguły analizy składni zarówno kompilatora, jak i powłoki. Na przykład, aby zdefiniować w programie symbol wstępnego przetwarzania znaku procenta (%), określ dwa znaki procenta (%%) w wierszu polecenia: Jeśli określisz tylko jeden, zostanie wygenerowany błąd analizy składni.

```
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. W okienku po lewej stronie wybierz **właściwości konfiguracji**, **C/C++**, **preprocesora**.

1. W okienku po prawej stronie, w kolumnie po prawej stronie **definicje preprocesora** właściwości, otwórz menu rozwijane i wybierz polecenie **Edytuj**.

1. W **definicje preprocesora** okno dialogowe Dodawanie (po jednej na wiersz), zmodyfikować lub usunąć jedną lub więcej definicji. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>.

## <a name="example"></a>Przykład

```
// cpp_D_compiler_option.cpp
// compile with: /DTEST
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

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[/U, /u (Usuń definicje symboli)](../../build/reference/u-u-undefine-symbols.md)<br/>
[#undef, dyrektywa (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br/>
[#define, dyrektywa (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)