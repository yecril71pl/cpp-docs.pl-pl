---
title: Manifestu, właściwości konfiguracji narzędzia (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.MergeRulesFile
- VC.Project.VCManifestTool.UseUnicodeResponseFiles
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.UseFAT32Workaround
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
dev_langs:
- C++
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf3fe573ff2a71c2a53e946655300219f190b4c8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447716"
---
# <a name="general-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Ogólne, narzędzie manifestu, właściwości konfiguracji &lt;Projectname&gt; okno dialogowe strony właściwości

Użyj tego okna dialogowego, aby określić ogólne opcje [Mt.exe](https://msdn.microsoft.com/library/aa375649).

Aby uzyskać dostęp do tego okna dialogowego strony właściwości, otwórz strony właściwości dla projektu lub arkuszu właściwości. Rozwiń **narzędziu manifestu** węźle **właściwości konfiguracji**, a następnie wybierz pozycję **ogólne**.

## <a name="uielement-list"></a>Lista elementów UI

- **Pomijaj transparent startowy**

   **Tak (/ nologo)** Określa, że po uruchomieniu narzędzia manifestu powoduje ukrycie standardowych danych o prawach autorskich firmy Microsoft. Użyj tej opcji, aby pominąć niechciane dane wyjściowe w plikach dziennika, po uruchomieniu mt.exe jako część procesu kompilacji lub ze środowiska kompilacji.

- **Pełne dane wyjściowe**

   **Tak (/ verbose)** Określa, że informacje o dodatkowych kompilacji będzie wyświetlany podczas generowania manifestu.

- **Tożsamość zestawu**

   Używa opcji /identity, aby określić ciąg tożsamości, która składa się z wartości atrybutów [ \<assemblyIdentity > Element](/visualstudio/deployment/assemblyidentity-element-clickonce-application). Ciąg tożsamości zaczyna się od wartości dla `name` atrybutów i następuje *atrybut* = *wartość* pary. Atrybuty w ciąg tożsamości są rozdzielone przecinkami.

   Poniżej przedstawiono przykładowy ciąg tożsamości:

   `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="see-also"></a>Zobacz też

[Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)<br>
[Strony właściwości narzędzia manifestu](../ide/manifest-tool-property-pages.md)<br>
[Praca z właściwościami projektu](../ide/working-with-project-properties.md)