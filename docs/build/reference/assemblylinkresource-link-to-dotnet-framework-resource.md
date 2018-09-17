---
title: -ASSEMBLYLINKRESOURCE (Link do zasobów .NET Framework) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ASSEMBLYLINKRESOURCE
- VC.Project.VCLinkerTool.AssemblyLinkResource
dev_langs:
- C++
helpviewer_keywords:
- -ASSEMBLYLINKRESOURCE linker option
- ASSEMBLYLINKRESOURCE linker option
- /ASSEMBLYLINKRESOURCE linker option
ms.assetid: 8b6ad184-1b33-47a4-8513-4803cf915b64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36f8f6adcfe5d67b3d27b8557627725ba7295829
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704148"
---
# <a name="assemblylinkresource-link-to-net-framework-resource"></a>/ASSEMBLYLINKRESOURCE (Łącze do Zasobów .NET Framework)

```
/ASSEMBLYLINKRESOURCE:filename
```

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Plik zasobów .NET Framework, z którym chcesz się połączyć z zestawu.

## <a name="remarks"></a>Uwagi

Opcja assemblylinkresource tworzy łącze do zasobu .NET Framework w pliku wyjściowym; plik zasobu nie zostanie umieszczony w pliku wyjściowym. [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md) osadza plik zasobów w pliku wyjściowym.

Połączone zasoby są publiczne w zestawie, gdy utworzone za pomocą konsolidatora.

/ ASSEMBLYLINKRESOURCE wymaga, że kompilacja obejmują [/CLR](../../build/reference/clr-common-language-runtime-compilation.md); [/LN](../../build/reference/ln-create-msil-module.md) lub [/noassembly](../../build/reference/noassembly-create-a-msil-module.md) nie jest dozwolona z assemblylinkresource.

Jeśli *filename* jest plikiem zasobów .NET Framework, utworzonym na przykład przez [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) lub w środowisku deweloperskim, jest dostępny za pomocą elementów członkowskich w **System.Resources** przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [System.Resources.ResourceManager](https://msdn.microsoft.com/library/system.resources.resourcemanager.aspx). W przypadku wszystkich innych zasobów, użyj **GetManifestResource** \* metody **System.Reflection.Assembly** klasy, aby uzyskać dostęp do zasobu w czasie wykonywania.

*Nazwa pliku* może być dowolnym formacie pliku. Na przykład można wprowadzić natywną DLL częścią zestawu, dzięki czemu mogą być zainstalowane w globalnej pamięci podręcznej zestawów i dostępne z kodu zarządzanego w zestawie.

Są także inne opcje konsolidatora, które mają wpływ na Generowanie zestawu:

- [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)

- [/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

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