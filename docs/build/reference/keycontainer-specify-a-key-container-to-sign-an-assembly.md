---
title: /KEYCONTAINER (Określ klucz kontenera, aby podpisać zestaw)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.KeyContainer
- /keycontainer
helpviewer_keywords:
- KEYCONTAINER linker option
- /KEYCONTAINER linker option
- -KEYCONTAINER linker option
ms.assetid: 94882d12-b77a-49c7-96d0-18a31aee001e
ms.openlocfilehash: 96d2f5fed0e450224f82ee909cea9d56082505fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291616"
---
# <a name="keycontainer-specify-a-key-container-to-sign-an-assembly"></a>/KEYCONTAINER (Określ klucz kontenera, aby podpisać zestaw)

```
/KEYCONTAINER:name
```

## <a name="arguments"></a>Argumenty

*Nazwa*<br/>
Kontener, który zawiera klucz. Umieścić ciąg w podwójnym cudzysłowie ("") zawiera spację.

## <a name="remarks"></a>Uwagi

Konsolidator tworzy zestawu podpisanego za pomocą przez wstawienie klucza publicznego do manifestu zestawu i podpisywanie ostateczny zestaw przy użyciu klucza prywatnego. Aby wygenerować plik klucza, wpisz [sn -k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* w wierszu polecenia. **SN -i** instaluje parę kluczy w kontenerze.

Jeśli kompilujesz z opcją [/LN](ln-create-msil-module.md), nazwę pliku klucza jest przechowywany w module i włączyć do zestawu, który jest tworzony podczas kompilowania zestawu, który zawiera jawnego odwołania do modułu, za pośrednictwem [#using](../../preprocessor/hash-using-directive-cpp.md), lub podczas łączenia z [assemblymodule](assemblymodule-add-a-msil-module-to-the-assembly.md).

Można również przekazać szyfrowania informacji do kompilatora przy użyciu [/KeyFile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md). Użyj [/DelaySign](delaysign-partially-sign-an-assembly.md) Jeśli chcesz, aby częściowo podpisany zestawu. Zobacz [zestawy o silnej nazwach (podpisywanie zestawów) (C++sposób niezamierzony)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) więcej informacji na temat podpisywania zestawu.

Są także inne opcje konsolidatora, które mają wpływ na Generowanie zestawu:

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/ NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
