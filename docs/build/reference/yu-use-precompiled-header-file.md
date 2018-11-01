---
title: /Yu (Korzystaj z prekompilowanego pliku nagłówka)
ms.date: 11/04/2016
f1_keywords:
- /yu
helpviewer_keywords:
- Yu compiler option [C++]
- /Yu compiler option [C++]
- -Yu compiler option [C++]
- PCH files, use existing
- .pch files, use existing
- precompiled header files, use existing
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
ms.openlocfilehash: 8d2b02c378179ac2603ec095efe89ce78f9f1afa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505352"
---
# <a name="yu-use-precompiled-header-file"></a>/Yu (Korzystaj z prekompilowanego pliku nagłówka)

Instruuje kompilator, aby użyć istniejącego pliku prekompilowanego pliku nagłówkowego (.pch) w bieżącej kompilacji.

## <a name="syntax"></a>Składnia

```
/Yu[filename]
```

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Nazwa pliku nagłówkowego, który jest dostępny w pliku źródłowego używająca **#include** dyrektywy preprocesora.

## <a name="remarks"></a>Uwagi

Nazwa dołączanego pliku musi być takie same dla obu **/Yc** opcji, która tworzy prekompilowany plik nagłówkowy i wszystkich kolejnych **/Yu** opcję rezygnacji z używaniem prekompilowanego nagłówka.

Dla **/Yc**, `filename` określa punkt, w które wstępnej kompilacji zatrzymuje; kompilator jednak wstępnie kompiluje kod wszystkich `filename` i wynikowy prekompilowanego pliku nagłówkowego, przy użyciu podstawowej nazwy dołączanego pliku i rozszerzenie nazwy z .pch.

Plik .pch muszą zostać utworzone za pomocą **/Yc**.

Kompilator traktuje cały kod przed plik .h jako wstępnie skompilowane. Pomija można po prostu wykorzystywane **#include** dyrektywy skojarzone z plikiem .h używa kod zawarty w pliku .pch, a następnie kompiluje cały kod po `filename`.

W wierszu polecenia nie może być spacji między **/Yu** i `filename`.

Po określeniu **/Yu** opcji bez nazwy pliku, program źródłowy musi zawierać [#pragma hdrstop](../../preprocessor/hdrstop.md) pragma, który określa nazwę pliku prekompilowanego pliku nagłówkowego pliku .pch. W tym przypadku kompilator będzie używał prekompilowanego pliku nagłówkowego (pliku .pch) o nazwie określonej przez  [ /FP (nazwa. Plik pch)](../../build/reference/fp-name-dot-pch-file.md). Kompilator pomija do lokalizacji pragmy tego przywraca stan kompilacji z prekompilowanego pliku nagłówkowego określone przez dyrektywę i następnie kompiluje kod, który następuje po pragmie. Jeśli **#pragma hdrstop** nie określa nazwę pliku, kompilator szuka pliku o nazwie pochodzące z podstawowej nazwy pliku źródłowego z rozszerzeniem .pch. Można również użyć **/FP** opcję, aby określić plik .pch różne.

Jeśli określisz **/Yu** opcji bez nazwy pliku i nie można określić **hdrstop** pragma, generowany jest komunikat o błędzie i kompilacja zakończy się niepowodzeniem.

Jeśli **/Yc** `filename` i **/Yu** `filename` opcji wystąpiły na tym samym wierszu polecenia i zarówno odwoływać się do tej samej nazwie pliku, **/Yc** `filename` przyjmuje pierwszeństwo, do wstępnej kompilacji całego kodu, w tym wskazanego pliku. Ta funkcja ułatwia zapisywanie plików reguł programu make.

Ponieważ .pch — pliki zawierają informacje o środowisku komputera, a także informacji na temat programu, informacje o adresie pamięci, należy używać tylko plik pch na komputerze, w której został utworzony.

Aby uzyskać więcej informacji na temat wstępnie skompilowanych nagłówków zobacz:

- [/Y (Prekompilowane nagłówki)](../../build/reference/y-precompiled-headers.md)

- [Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Określ [/Yc (Utwórz prekompilowany plik nagłówkowy)](../../build/reference/yc-create-precompiled-header-file.md) pliku .cpp w projekcie.

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **prekompilowanych nagłówków** stronę właściwości.

1. Modyfikowanie **Utwórz/Użyj PCH za pośrednictwem pliku** właściwości lub **Utwórz/użycie Prekompilowanego nagłówka** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.

## <a name="examples"></a>Przykłady

Jeśli następujący kod:

```
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
...
```

jest skompilowany przy użyciu wiersza polecenia `CL /YuMYAPP.H PROG.CPP`, kompilator nie może przetwarzać trzy obejmują instrukcji, ale używa wstępnie skompilowany kod z MYAPP.pch, a tym samym zapisywanie czasu zaangażowanych w przetwarzaniu wstępnym wszystkie trzy pliki (i wszystkie pliki, mogą one obejmować).

Możesz użyć  [ /FP (nazwa. Plik pch)](../../build/reference/fp-name-dot-pch-file.md) z opcją **/Yu** opcję, aby określić nazwę pliku .pch, jeśli nazwa jest inna niż albo argument nazwy pliku do **/Yc** lub podstawowej nazwy pliku źródłowego, jak następujące:

```
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP
```

To polecenie Określa prekompilowany plik nagłówka o nazwie MYPCH.pch. Kompilator używa jego zawartość w celu przywrócenia stanu wstępnie skompilowane, wszystkie pliki nagłówkowe do i łącznie MYAPP.h. Kompilator następnie kompiluje kod, który następuje po MYAPP.h **obejmują** instrukcji.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)