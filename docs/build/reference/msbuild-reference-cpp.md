---
title: Dokumentacja programu MSBuild C++ dla projektów w programie Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: ec1285a760d438a94863181a1b099e6db153c268
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168905"
---
# <a name="msbuild-reference-for-c-projects"></a>Dokumentacja aparatu MSBuild dla projektów w języku C++

MSBuild to natywny system kompilacji dla wszystkich projektów w programie Visual Studio, C++ łącznie z projektami. Podczas kompilowania projektu w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio wywołuje narzędzie MSBuild. exe, które z kolei wykorzystuje plik projektu. vcxproj i różne pliki targets i. props. Ogólnie rzecz biorąc zdecydowanie zalecamy użycie środowiska IDE programu Visual Studio do ustawiania właściwości projektu i wywoływać MSBuild. Ręczne edytowanie plików projektu może prowadzić do poważnych problemów, jeśli nie zostały prawidłowo wykonane.

Jeśli z jakiegoś powodu chcesz użyć programu MSBuild bezpośrednio z wiersza polecenia, zobacz [Korzystanie z programu MSBuild z poziomu wiersza polecenia](../msbuild-visual-cpp.md). Aby uzyskać więcej informacji na temat programu MSBuild, zobacz [MSBuild](/visualstudio/msbuild/msbuild) w dokumentacji programu Visual Studio.

## <a name="in-this-section"></a>W tej sekcji

[Funkcje wewnętrzne aparatu MSBuild dla projektów w języku C++](msbuild-visual-cpp-overview.md)<br/>
Informacje na temat sposobu przechowywania i używania właściwości i obiektów docelowych.

[Typowe makra dla właściwości i poleceń kompilacji](common-macros-for-build-commands-and-properties.md)<br/>
Opisuje makra (stałe czasu kompilacji), których można użyć do zdefiniowania właściwości, takich jak ścieżki i wersje produktów.

[Typy plików utworzone dla C++ projektów](file-types-created-for-visual-cpp-projects.md)<br/>
Opisuje różne rodzaje plików, które program Visual Studio tworzy dla różnych typów projektów.

[Szablony projektów C++ programu Visual Studio](visual-cpp-project-types.md)<br>
Zawiera opis typów projektów opartych na programie MSBuild, które C++są dostępne dla programu.

[Szablony nowych elementów w języku C++](using-visual-cpp-add-new-item-templates.md)<br>
Opisuje pliki źródłowe i inne elementy, które można dodać do projektu programu Visual Studio.

[Wstępnie skompilowane pliki nagłówkowe](../creating-precompiled-header-files.md) Jak używać prekompilowanych plików nagłówkowych i jak utworzyć własny niestandardowy kod wstępnie skompilowany w celu przyspieszenia czasu kompilacji.

[Odwołanie do właściwości projektu programu Visual Studio](property-pages-visual-cpp.md)<br/>
Dokumentacja referencyjna dla właściwości projektu ustawionych w środowisku IDE programu Visual Studio.

## <a name="see-also"></a>Zobacz też

[Dokumentacja kompilacji w języku C/C++](c-cpp-building-reference.md)
