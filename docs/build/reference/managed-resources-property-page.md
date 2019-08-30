---
title: Strona właściwości Zarządzane zasoby
ms.date: 08/28/2019
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
helpviewer_keywords:
- Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
ms.openlocfilehash: 14802996e63392bfb5fcc22096ef5f3d9db197c2
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177523"
---
# <a name="managed-resources-property-page"></a>Strona właściwości Zarządzane zasoby

Na stronie właściwości **zarządzane zasoby** są ujawniane następujące właściwości kompilatora zarządzanych zasobów [Resgen. exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) w przypadku używania zasobów platformy .NET C++w programach/CLI:

- **Nazwa logiczna zasobu**

   Określa *nazwę logiczną* wygenerowanego pośredniego pliku Resources. Nazwa logiczna to nazwa używana do ładowania zasobu. Jeśli nie określono nazwy logicznej, nazwa pliku zasobu (. resx) jest używana jako nazwa logiczna.

- **Nazwa pliku wyjściowego**

   Określa nazwę końcowego pliku wyjściowego, do którego wchodzi plik zasobu (. resx).

- **Domyślne zlokalizowane zasoby**

   Określa, czy dany plik resx wchodzi w skład domyślnych zasobów, czy do pliku satelickiego. dll.

Aby uzyskać informacje na temat uzyskiwania dostępu do strony właściwości **zarządzane zasoby** , [Zobacz C++ Ustawianie kompilatora i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

## <a name="see-also"></a>Zobacz także

[Korzystanie z RC (wiersz polecenia RC)](/windows/win32/menurc/using-rc-the-rc-command-line-)<br>
[C++odwołanie do strony właściwości projektu](property-pages-visual-cpp.md)<br>
[/ASSEMBLYRESOURCE (Osadź zarządzany zasób)](assemblyresource-embed-a-managed-resource.md)
