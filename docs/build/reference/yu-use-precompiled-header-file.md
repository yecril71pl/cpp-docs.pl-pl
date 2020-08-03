---
title: /Yu (Korzystaj z prekompilowanego pliku nagłówka)
ms.date: 07/31/2020
f1_keywords:
- /Yu
helpviewer_keywords:
- Yu compiler option [C++]
- /Yu compiler option [C++]
- -Yu compiler option [C++]
- PCH files, use existing
- .pch files, use existing
- precompiled header files, use existing
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
ms.openlocfilehash: 8cccce39949f23e4ceb72807ecaef3597ab733c4
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520465"
---
# <a name="yu-use-precompiled-header-file"></a>`/Yu`(Użyj prekompilowanego pliku nagłówkowego)

Instruuje kompilator, aby używał istniejącego prekompilowanego pliku nagłówkowego ( *`.pch`* ) w bieżącej kompilacji.

## <a name="syntax"></a>Składnia

> **`/Yu`**\[*Nazwa pliku*]

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Nazwa pliku nagłówkowego, który jest zawarty w pliku źródłowym przy użyciu `#include` dyrektywy preprocesora.

## <a name="remarks"></a>Uwagi

Nazwa pliku dołączanego musi być taka sama dla **`/Yc`** opcji, która tworzy prekompilowany nagłówek i dla każdej późniejszej **`/Yu`** opcji, która wskazuje użycie prekompilowanego nagłówka.

W **`/Yc`** polu *Nazwa pliku* określa punkt, w którym prekompilowanie zostało zatrzymane; Kompilator kompiluje cały kod, chociaż *filename* i nazwij otrzymany prekompilowany nagłówek przy użyciu podstawowej nazwy pliku dołączanego i rozszerzenia *`.pch`* .

*`.pch`* Plik musi zostać utworzony przy użyciu **`/Yc`** .

Kompilator traktuje cały kod występujący przed plikiem. h jako wstępnie skompilowany. Pominie to tuż poza `#include` dyrektywą skojarzoną z *`.h`* plikiem, używa kodu zawartego w *`.pch`* pliku, a następnie kompiluje cały kod po *nazwie pliku*.

W wierszu polecenia nie jest dozwolone żadne miejsce między **`/Yu`** i *filename*.

Jeśli określisz **`/Yu`** opcję bez nazwy pliku, program źródłowy musi zawierać [`#pragma hdrstop`](../../preprocessor/hdrstop.md) pragmę, która określa nazwę pliku prekompilowanego nagłówka, *`.pch`* pliku. W takim przypadku kompilator będzie używać prekompilowanego nagłówka ( *`.pch`* pliku) o nazwie [`/Fp (Name .pch file)`](fp-name-dot-pch-file.md) . Kompilator pomija lokalizację tej dyrektywy pragma i przywraca skompilowany stan z określonego prekompilowanego pliku nagłówkowego. Następnie kompiluje tylko kod, który następuje po pragmie. Jeśli `#pragma hdrstop` Nazwa pliku nie zostanie określona, kompilator szuka pliku o nazwie pochodzącej od podstawowej nazwy pliku źródłowego z *`.pch`* rozszerzeniem. Można również użyć opcji, **`/Fp`** Aby określić inny *`.pch`* plik.

W przypadku określenia **`/Yu`** opcji bez nazwy pliku i niepowodzenia określenia `hdrstop` dyrektywy pragma zostanie wygenerowany komunikat o błędzie i kompilacja zakończy się niepowodzeniem.

Jeśli opcje **`/Yc`** _filename_ i **`/Yu`** _filename_ są wykonywane w tym samym wierszu polecenia i obie odwołują się do tej samej nazwy pliku, **`/Yc`** _filename_ ma pierwszeństwo, wstępne Kompilowanie całego kodu do i łącznie z nazwanym plikiem. Ta funkcja upraszcza pisanie plików reguł programu make.

Ponieważ *`.pch`* pliki zawierają informacje o środowisku komputera i informacje o adresie pamięci dotyczące programu, należy użyć tylko *`.pch`* pliku na komputerze, na którym został utworzony.

Aby uzyskać więcej informacji na temat prekompilowanych nagłówków, zobacz:

- [`/Y`(Prekompilowane nagłówki)](y-precompiled-headers.md)

- [Pliki prekompilowanego nagłówka](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Określ [ `/Yc` (Utwórz prekompilowany plik nagłówkowy)](yc-create-precompiled-header-file.md) w pliku. cpp w projekcie.

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości**C/C++**  >  **prekompilowanego nagłówka** C/C++ właściwości konfiguracji.

1. Zmodyfikuj właściwość **prekompilowanego nagłówka** , właściwość **Utwórz/Użyj PCH przez plik** lub **Utwórz/Użyj prekompilowanego nagłówka** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A> .

## <a name="example"></a>Przykład

Jeśli Poniższy kod:

```cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
...
```

jest kompilowany przy użyciu wiersza polecenia `CL /YuMYAPP.H PROG.CPP` kompilator nie przetwarza trzech instrukcji INCLUDE. Zamiast tego używa wstępnie skompilowanego kodu z *`MYAPP.pch`* , co oszczędza czas związany z przetwarzaniem wszystkich trzech plików (oraz wszelkich plików, które mogą zawierać).

Możesz użyć [`/Fp (Name .pch file)`](fp-name-dot-pch-file.md) opcji z **`/Yu`** opcją, aby określić nazwę *`.pch`* pliku, jeśli nazwa różni się od argumentu *filename* **`/Yc`** lub nazwa podstawowa pliku źródłowego, jak w poniższym przykładzie:

```cmd
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP
```

To polecenie określa prekompilowany plik nagłówkowy o nazwie *`MYPCH.pch`* . Kompilator używa jego zawartości, aby przywrócić wstępnie skompilowany stan wszystkich plików nagłówkowych, do i włącznie *`MYAPP.h`* . Następnie Kompilator kompiluje kod, który występuje po `#include "MYAPP.h"` dyrektywie *.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
