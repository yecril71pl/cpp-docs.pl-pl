---
title: Strona właściwości ogólnych (plik) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
dev_langs:
- C++
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ad4689c15e14ba0bbac61c8c3b28148536b9057
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715471"
---
# <a name="general-property-page-file"></a>Ogólna strona właściwości (plik)

Po wybraniu pliku w **Eksploratora rozwiązań**, **ogólne** strony właściwości w obszarze **właściwości konfiguracji** węzła zawiera następujące właściwości:

- **Wyklucz z kompilacji**

   Określa, czy plik powinien znajdować się w kompilacji w bieżącej konfiguracji.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>.

- **Narzędzie**

   Narzędzie, które będą służyć do tworzenia tego pliku. Zobacz [Określanie niestandardowego narzędzia kompilacji](../ide/specifying-custom-build-tools.md) Aby uzyskać więcej informacji.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>.

Aby uzyskać informacje dotyczące uzyskiwania dostępu do **ogólne** strony właściwości w obszarze **właściwości konfiguracji** węzła, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).

Dla projektów innych niż Windows, zobacz [dokumentacja strony właściwości C++ Linux](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->.

## <a name="see-also"></a>Zobacz także

[Strony właściwości](../ide/property-pages-visual-cpp.md)  