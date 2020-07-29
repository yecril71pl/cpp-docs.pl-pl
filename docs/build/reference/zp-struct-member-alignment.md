---
title: /Zp (Wyrównanie członka struktury)
ms.date: 04/04/2019
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
ms.openlocfilehash: c78e670303bde68299725e18c6f588f5e410a971
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234305"
---
# <a name="zp-struct-member-alignment"></a>/Zp (Wyrównanie członka struktury)

Kontroluje sposób pakowania elementów członkowskich struktury do pamięci i określa to samo pakowanie dla wszystkich struktur w module.

## <a name="syntax"></a>Składnia

> **`/Zp`**[**`1`**|**`2`**|**`4`**|**`8`**|**`16`**]

## <a name="remarks"></a>Uwagi

**`/ZpN`** Opcja informuje kompilator, gdzie ma być przechowywany każdy element członkowski struktury. Kompilator przechowuje elementy członkowskie po pierwszej stronie na granicy, która jest mniejsza od rozmiaru typu elementu członkowskiego lub granicy *N*-bajtowej.

Dostępne wartości pakowania są opisane w poniższej tabeli:

|/ZP — argument|Efekt|
|-|-|
|1|Struktury pakietów na 1-bajtowych granicach. Analogicznie jak **`/Zp`** .|
|2|Struktury pakietów przy 2-bajtowych granicach.|
|4|Struktury pakietów przy 4-bajtowych granicach.|
|8|Struktury pakietów na 8-bajtowych granicach (domyślnie dla procesorów x86, ARM i ARM64).|
|16| Struktury pakietów na 16-bajtowych granicach (domyślnie dla architektury x64).|

Nie należy używać tej opcji, chyba że są określone wymagania dotyczące wyrównania.

> [!WARNING]
> Nagłówki C++ w zestawie Windows SDK i zakładają **`/Zp8`** wewnętrznie pakowanie. Może wystąpić uszkodzenie pamięci, jeśli **`/Zp`** ustawienie zostanie zmienione wewnątrz nagłówków Windows SDK. W nagłówkach nie ma wpływu żadna **`/Zp`** opcja ustawiona w wierszu polecenia.

Można również użyć [`pack`](../../preprocessor/pack.md) do kontroli pakowania struktury. Aby uzyskać więcej informacji na temat wyrównania, zobacz:

- [`align`](../../cpp/align-cpp.md)

- [`alignof`Zakład](../../cpp/alignof-operator.md)

- [`__unaligned`](../../cpp/unaligned.md)

- [`/ALIGN`(Wyrównanie sekcji)](align-section-alignment.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja generowania kodu**C/C++**  >  **Code Generation** .

1. Zmodyfikuj właściwość **wyrównania elementu członkowskiego struktury** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md) \
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
