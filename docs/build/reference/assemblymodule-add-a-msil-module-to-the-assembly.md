---
title: /ASSEMBLYMODULE (Dodaj moduł MSIL do zestawu)
ms.date: 11/04/2016
f1_keywords:
- /assemblymodule
- VC.Project.VCLinkerTool.AddModuleNamesToAssembly
helpviewer_keywords:
- ASSEMBLYMODULE linker option
- assemblies [C++], adding modules to
- assemblies [C++]
- /ASSEMBLYMODULE linker option
- -ASSEMBLYMODULE linker option
ms.assetid: 67357da8-e4b6-49fd-932c-329a5777f143
ms.openlocfilehash: d08b5bca38f4ff590a0e1bfb8d8693c374a43444
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621510"
---
# <a name="assemblymodule-add-a-msil-module-to-the-assembly"></a>/ASSEMBLYMODULE (Dodaj moduł MSIL do zestawu)

```
/ASSEMBLYMODULE:filename
```

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Moduł, który chcesz uwzględnić w tym zestawie.

## <a name="remarks"></a>Uwagi

Opcja assemblymodule pozwala dodać odwołanie do zestawu modułu. Informacje o typie w module nie będzie dostępne dla programu zestawu, który dodaje odwołania do modułu. Jednak informacje o typie w module będzie dostępny dla dowolnego programu, który odwołuje się do zestawu.

Użyj [#using](../../preprocessor/hash-using-directive-cpp.md) do dodania odwołania modułu do zestawu i udostępnia informacje o typie modułu dla programu zestawu.

Na przykład rozważmy następujący scenariusz:

1. Utwórz moduł przy użyciu [/LN](../../build/reference/ln-create-msil-module.md).

1. Użyj assemblymodule z innego projektu, aby uwzględnić moduł w bieżącej kompilacji, które spowoduje utworzenie zestawu. Ten projekt nie zostanie wprowadzone odniesienie moduł za pomocą `#using`.

1. Jakiegokolwiek projektu, który odwołuje się do tego zestawu można teraz również używać typów z modułu.

Są także inne opcje konsolidatora, które mają wpływ na Generowanie zestawu:

- [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)

- [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

- [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

Konsolidator Visual C++ akceptuje pliki .netmodule — wejście plik wyjściowy, generowany przez konsolidator. zostanie ona zestaw lub moduł .netmodule z ma zależności środowiska wykonawczego na żadnym z modułów .netmodule, że dane wejściowe do konsolidatora.  Aby uzyskać więcej informacji, zobacz [pliki .netmodule — wejście konsolidatora](../../build/reference/netmodule-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **dane wejściowe** stronę właściwości.

1. Modyfikowanie **Dodaj moduł do zestawu** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)