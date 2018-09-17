---
title: -KEYCONTAINER (Określ klucz kontenera, aby podpisać zestaw) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.KeyContainer
- /keycontainer
dev_langs:
- C++
helpviewer_keywords:
- KEYCONTAINER linker option
- /KEYCONTAINER linker option
- -KEYCONTAINER linker option
ms.assetid: 94882d12-b77a-49c7-96d0-18a31aee001e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 850a8173dba3e69eaf52fdf174674e1dba58a4d8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723765"
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

Jeśli kompilujesz z opcją [/LN](../../build/reference/ln-create-msil-module.md), nazwę pliku klucza jest przechowywany w module i włączyć do zestawu, który jest tworzony podczas kompilowania zestawu, który zawiera jawnego odwołania do modułu, za pośrednictwem [#using](../../preprocessor/hash-using-directive-cpp.md), lub podczas łączenia z [assemblymodule](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md).

Można również przekazać szyfrowania informacji do kompilatora przy użyciu [/KeyFile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md). Użyj [/DelaySign](../../build/reference/delaysign-partially-sign-an-assembly.md) Jeśli chcesz, aby częściowo podpisany zestawu. Zobacz [zestawy o silnej nazwach (podpisywanie zestawów) (C + +/ CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) więcej informacji na temat podpisywania zestawu.

Są także inne opcje konsolidatora, które mają wpływ na Generowanie zestawu:

- [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)