---
title: 'Porady: integrowanie narzędzi niestandardowych we właściwościach projektu'
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
ms.openlocfilehash: 5a96ffd15bb28022b3000252307c75b3383ac59c
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373752"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Porady: integrowanie narzędzi niestandardowych we właściwościach projektu

Możesz dodać niestandardowe opcje narzędzia do okna **stron właściwości** programu Visual Studio, tworząc źródłowy plik schematu XML.

W sekcji **Właściwości konfiguracji** okna **strony właściwości** są wyświetlane grupy ustawień, które są znane jako *reguły*. Każda reguła zawiera ustawienia dla narzędzia lub grupy funkcji. Na przykład reguła **konsolidatora** zawiera ustawienia dla narzędzia konsolidatora. Ustawienia w regule mogą być podzielone na *Kategorie*.

W tym dokumencie wyjaśniono, jak utworzyć plik w katalogu zestawu, który zawiera właściwości niestandardowego narzędzia, dzięki czemu właściwości są ładowane podczas uruchamiania programu Visual Studio. Aby uzyskać informacje na temat sposobu modyfikowania pliku, zobacz [platform Extensibilty część 2](https://docs.microsoft.com/archive/blogs/vsproject/platform-extensibility-part-2) w blogu zespołu projektu programu Visual Studio.

### <a name="to-add-or-change-project-properties"></a>Aby dodać lub zmienić właściwości projektu

1. W edytorze XML Utwórz plik XML.

1. Zapisz plik w folderze programu Visual Studio `VCTargets\1033` . Istnieje inna ścieżka dla każdej wersji programu Visual Studio, która jest zainstalowana i każdego języka. Na przykład domyślna ścieżka folderu dla programu Visual Studio 2019 Community Edition jest w języku angielskim `C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\VC\VCTargets` . Dostosuj ścieżkę do języka i wersji programu Visual Studio. Każda reguła w oknie **strony właściwości** jest reprezentowana przez plik XML w tym folderze. Upewnij się, że plik ma unikatową nazwę w folderze.

1. Skopiuj zawartość `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml` (lub niezależnie od ścieżki), zamknij ją bez zapisywania zmian, a następnie wklej zawartość w nowym pliku XML. Można użyć dowolnego pliku schematu XML — jest to tylko jeden, którego można użyć, aby rozpocząć pracę z szablonem.

1. W nowym pliku XML zmodyfikuj zawartość zgodnie z wymaganiami. Upewnij się, że w górnej części pliku zmieniono **nazwę reguły** i **regułę. DisplayName** .

1. Zapisz zmiany i zamknij plik.

1. Pliki XML w `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` (lub wszędzie tam zapisane) są ładowane podczas uruchamiania programu Visual Studio. W związku z tym, aby przetestować nowy plik, uruchom ponownie program Visual Studio.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Właściwości**. W oknie **strony właściwości** w okienku po lewej stronie Sprawdź, czy istnieje nowy węzeł o nazwie reguły.

## <a name="see-also"></a>Zobacz też

[MSBuild w wierszu polecenia — C++](msbuild-visual-cpp.md)
