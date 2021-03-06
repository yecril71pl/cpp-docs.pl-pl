---
title: /LN (Utwórz moduł MSIL)
ms.date: 11/04/2016
f1_keywords:
- /LN
helpviewer_keywords:
- -LN compiler option [C++]
- /LN compiler option [C++]
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
ms.openlocfilehash: 2dbd5ae5ddf802185912c49caf37aa61c6a7d4c3
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446260"
---
# <a name="ln-create-msil-module"></a>/LN (Utwórz moduł MSIL)

Określa, że nie można wstawić w manifeście zestawu do pliku wyjściowego.

## <a name="syntax"></a>Składnia

```
/LN
```

## <a name="remarks"></a>Uwagi

Domyślnie **/LN** nie jest włączone (manifest zestawu jest wstawiany do pliku wyjściowego).

Gdy **/LN** jest używany, jeden z [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](clr-common-language-runtime-compilation.md) opcje musi też być używane.

Zarządzany program, który nie ma metadane zestawu w manifeście nosi nazwę modułu. Jeśli kompilujesz z opcją [/c (Kompiluj bez konsolidacji)](c-compile-without-linking.md) i **/LN**, określ [/noassembly (Utwórz moduł MSIL)](noassembly-create-a-msil-module.md) w fazie konsolidator, aby utworzyć plik wyjściowy.

Można utworzyć modułów, jeśli chcesz wykonać to oparty na komponentach podejście do tworzenia zestawów.  Oznacza to, że możesz tworzyć typy i kompilowania ich do modułów.  Następnie można wygenerować zestawu z jednego lub więcej modułów.  Aby uzyskać więcej informacji na temat tworzenia zestawów z modułów, zobacz [pliki .netmodule — wejście konsolidatora](netmodule-files-as-linker-input.md) lub [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).

Domyślnym rozszerzeniem pliku modułu jest .netmodule.

W wersjach przed Visual Studio 2005 moduł został utworzony za pomocą **/clr:noAssembly**.

Konsolidator MSVC akceptuje pliki .netmodule — wejście plik wyjściowy, generowany przez konsolidator. zostanie ona zestaw lub moduł .netmodule z ma zależności środowiska wykonawczego na żadnym z modułów .netmodule, że dane wejściowe do konsolidatora.  Aby uzyskać więcej informacji, zobacz [pliki .netmodule — wejście konsolidatora](netmodule-files-as-linker-input.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

- Określ [/noassembly (Utwórz moduł MSIL)](noassembly-create-a-msil-module.md) w fazie konsolidator, aby utworzyć plik wyjściowy.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Nie można programowo zmienić tę opcję kompilatora.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
