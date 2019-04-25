---
title: Narzędzie manifestu COM izolowany właściwości
ms.date: 12/10/2018
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
ms.openlocfilehash: 2fda169ecf304373d27d699bf313bde124dc399f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269716"
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>COM izolowany, narzędzie manifestu, właściwości konfiguracji, &lt;Projectname&gt; okno dialogowe strony właściwości

To okno dialogowe służy do określania **COM izolowany** opcje dla [Mt.exe](https://msdn.microsoft.com/library/aa375649).

Aby uzyskać dostęp do tego okna dialogowego strony właściwości, otwórz strony właściwości dla projektu lub arkuszu właściwości. Rozwiń **narzędziu manifestu** węźle **wspólne właściwości**, a następnie wybierz pozycję **COM izolowany**.

## <a name="task-list"></a>Lista zadań

- [Instrukcje: kompilowanie izolowanych aplikacji korzystających ze składników COM](../how-to-build-isolated-applications-to-consume-com-components.md)

## <a name="uielement-list"></a>Lista elementów UI

- **Plik biblioteki typów**

   Używa opcji/tlb, aby określić nazwę pliku biblioteki typów (pliku .tlb), narzędzie manifestu, zostanie użyta do wygenerowania pliku manifestu.

- **Plik skryptu rejestratora**

   Opcja /rgs jest używana do określenia nazwy plik skryptu rejestratora (pliku .rgs), narzędzie manifestu, zostanie użyta do wygenerowania pliku manifestu.

- **Nazwa pliku składnika**

   Opcja/dll jest używana do określenia nazwy zasobu, który zostanie wygenerowany przez narzędzie manifestu. Wprowadź wartość tej właściwości podczas wartości dla dowolnego **pliku biblioteki typów** lub **plik skryptu rejestratora** zostały określone.

- **Plik zastępstw**

   Używa opcji /replacements, aby określić pełną ścieżkę do pliku, który zawiera wartości dla wymienialnych ciągów w pliku .rgs.

## <a name="see-also"></a>Zobacz także

[Aplikacje izolowane](/windows/desktop/SbsCs/isolated-applications)<br>
[Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)<br>
[Strony właściwości narzędzia manifestu](manifest-tool-property-pages.md)<br>
[Ustawianie właściwości kompilacji i kompilatora języka C++ w programie Visual Studio](../working-with-project-properties.md)
