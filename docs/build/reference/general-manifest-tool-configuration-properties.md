---
title: Właściwości konfiguracji narzędzia manifestu (komentarze dokumentacji C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCManifestTool.MergeRulesFile
- VC.Project.VCManifestTool.UseUnicodeResponseFiles
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.UseFAT32Workaround
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
ms.openlocfilehash: 9acdb7f5c934a8cabdd1803074778ac9f01f4960
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823889"
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

## <a name="see-also"></a>Zobacz także

[Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)<br>
[Strony właściwości narzędzia manifestu](manifest-tool-property-pages.md)<br>
[Ustaw kompilator języka C++ i właściwości w programie Visual Studio kompilacji](../working-with-project-properties.md)
