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
ms.openlocfilehash: 728e8a84ff8d1afac99f99dbb975c7fd9360bcc1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815258"
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

1. Utwórz moduł przy użyciu [/LN](ln-create-msil-module.md).

1. Użyj assemblymodule z innego projektu, aby uwzględnić moduł w bieżącej kompilacji, które spowoduje utworzenie zestawu. Ten projekt nie zostanie wprowadzone odniesienie moduł za pomocą `#using`.

1. Jakiegokolwiek projektu, który odwołuje się do tego zestawu można teraz również używać typów z modułu.

Są także inne opcje konsolidatora, które mają wpływ na Generowanie zestawu:

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/ DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/ NOASSEMBLY](noassembly-create-a-msil-module.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/ KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

Konsolidator MSVC akceptuje pliki .netmodule — wejście plik wyjściowy, generowany przez konsolidator. zostanie ona zestaw lub moduł .netmodule z ma zależności środowiska wykonawczego na żadnym z modułów .netmodule, że dane wejściowe do konsolidatora.  Aby uzyskać więcej informacji, zobacz [pliki .netmodule — wejście konsolidatora](netmodule-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **dane wejściowe** stronę właściwości.

1. Modyfikowanie **Dodaj moduł do zestawu** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
