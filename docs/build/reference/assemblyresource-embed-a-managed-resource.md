---
title: /ASSEMBLYRESOURCE (Osadź zarządzany zasób)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.EmbedManagedResourceFile
- /ASSEMBLYRESOURCE
helpviewer_keywords:
- ASSEMBLYRESOURCE linker option
- assemblies [C++]
- -ASSEMBLYRESOURCE linker option
- assemblies [C++], linking resource files
- /ASSEMBLYRESOURCE linker option
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
ms.openlocfilehash: 1eac489ffd01f6bd79fc8c5bbda23adb751c9486
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822655"
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE (Osadź zarządzany zasób)

```
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]
```

## <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Zarządzanego zasobu, który ma zostać osadzony w tym zestawie.

*Nazwa*<br/>
Opcjonalna. Nazwa logiczna zasobu; Nazwa używana do ładowania zasobów. Wartość domyślna to nazwa pliku.

Opcjonalnie można określić, jeśli plik powinien znajdować się prywatne w manifeście zestawu. Domyślnie *nazwa* jest publiczna w zestawie.

## <a name="remarks"></a>Uwagi

Opcja linkowany do osadzenia zasobu w zestawie.

Zasoby są publiczne w zestawie, gdy utworzone za pomocą konsolidatora. Konsolidator nie pozwalają na Zmień nazwę zasobu w zestawie.

Jeśli *filename* jest plikiem zasobów (Resources) środowiska .NET Framework, utworzonym na przykład przez [Resource File Generator (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator) lub w środowisku deweloperskim, jest dostępny za pomocą elementów członkowskich w **System.Resources** przestrzeni nazw (zobacz [System.Resources.ResourceManager](/dotnet/api/system.resources.resourcemanager) Aby uzyskać więcej informacji). W przypadku wszystkich innych zasobów, użyj **GetManifestResource** \* metody **System.Reflection.Assembly** klasy, aby uzyskać dostęp do zasobu w czasie wykonywania.

Są także inne opcje konsolidatora, które mają wpływ na Generowanie zestawu:

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/ KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/ NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **dane wejściowe** stronę właściwości.

1. Modyfikowanie **Osadź plik zasobu zarządzanego** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
