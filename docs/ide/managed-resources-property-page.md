---
title: Strona właściwości zasobów zarządzanych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
dev_langs:
- C++
helpviewer_keywords:
- Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 687203787bdab69751aabf0672fe1269974b3014
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399612"
---
# <a name="managed-resources-property-page"></a>Strona właściwości Zarządzane zasoby

Umożliwia ustawień dla kompilatora zasobów.

**Zarządzanych zasobów** strona właściwości zawiera następujące właściwości:

- **Nazwa logiczna zasobu**

   Określa *Nazwa logiczna* pliku wygenerowanego pośredniego .resources. Nazwa logiczna jest nazwa służąca do załadowania zasobu. Jeśli nazwa logiczne, nie zostanie określona, nazwy pliku zasobów (.resx) jest używana jako nazwa logiczna.

- **Nazwa pliku wyjściowego**

   Określa nazwę pliku wyjściowego, który plik zasobów (.resx), którzy przyczyniają się do.

- **Domyślnie lokalizowane zasoby**

   Określa, czy plik danego .resx jest częścią domyślnych zasobów lub satelitarnej biblioteki dll.

Aby uzyskać informacje dotyczące uzyskiwania dostępu do **zarządzanych zasobów** strony właściwości, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).

## <a name="see-also"></a>Zobacz też

[Za pomocą RC (RC wiersza polecenia)](/windows/desktop/menurc/using-rc-the-rc-command-line-)<br>
[Strony właściwości](../ide/property-pages-visual-cpp.md)<br>
[/ASSEMBLYRESOURCE (Osadź zarządzany zasób)](../build/reference/assemblyresource-embed-a-managed-resource.md)