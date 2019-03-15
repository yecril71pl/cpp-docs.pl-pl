---
title: /NOASSEMBLY (Utwórz moduł MSIL)
ms.date: 11/04/2016
f1_keywords:
- /NOASSEMBLY
- VC.Project.VCLinkerTool.TurnOffAssemblyGeneration
helpviewer_keywords:
- assemblies [C++]
- -NOASSEMBLY linker option
- /NOASSEMBLY linker option
- NOASSEMBLY linker option
- assemblies [C++], not creating an assembly
ms.assetid: 3cea4e70-f451-4395-a626-1930b1b127fe
ms.openlocfilehash: 3350aa10dc7ae3b6f584394c01644c1af2abd2b4
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822395"
---
# <a name="noassembly-create-a-msil-module"></a>/NOASSEMBLY (Utwórz moduł MSIL)

```
/NOASSEMBLY
```

## <a name="remarks"></a>Uwagi

Opcja/noassembly informuje konsolidator, aby utworzył obraz dla bieżącego pliku wyjściowego bez zestawu .NET Framework. Plik wyjściowy MSIL bez manifest zestawu nosi nazwę modułu.

Domyślnie jest tworzony zestaw. Można również użyć [/LN (Utwórz moduł MSIL)](ln-create-msil-module.md) opcję kompilatora, aby utworzyć moduł.

Są także inne opcje konsolidatora, które mają wpływ na Generowanie zestawu:

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/ DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/ KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **zaawansowane** stronę właściwości.

1. Modyfikowanie **Włącz Wyłącz Generowanie zestawu** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TurnOffAssemblyGeneration%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
