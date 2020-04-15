---
title: Odwołanie msbuild dla projektów języka C++ w programie Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: 96987a252d12f718025dd55deecad5c6bac26872
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336210"
---
# <a name="msbuild-reference-for-c-projects"></a>Dokumentacja aparatu MSBuild dla projektów w języku C++

MSBuild jest macierzystym systemem kompilacji dla wszystkich projektów w programie Visual Studio, w tym projektów Języka C++. Podczas tworzenia projektu w środowisku programowym program Visual Studio zintegrowane programistyczne (IDE), wywołuje narzędzie msbuild.exe, który z kolei zużywa .vcxproj pliku projektu i różnych .targets i .props plików. Ogólnie rzecz biorąc zdecydowanie zaleca się przy użyciu środowiska IDE programu Visual Studio, aby ustawić właściwości projektu i wywołać MSBuild. Ręczna edycja plików projektu może prowadzić do poważnych problemów, jeśli nie zostaną wykonane poprawnie.

Jeśli z jakiegoś powodu chcesz używać MSBuild bezpośrednio z wiersza polecenia, zobacz [Używanie MSBuild z wiersza polecenia](../msbuild-visual-cpp.md). Aby uzyskać więcej informacji na temat MSBuild w ogóle, zobacz [MSBuild](/visualstudio/msbuild/msbuild) w dokumentacji programu Visual Studio.

## <a name="in-this-section"></a>W tej sekcji

[Funkcje wewnętrzne aparatu MSBuild dla projektów w języku C++](msbuild-visual-cpp-overview.md)<br/>
Informacje o sposobie przechowywania i korzystania z obiektów docelowych właściwości i obiektów docelowych.

[Typowe makra dla poleceń i właściwości kompilacji](common-macros-for-build-commands-and-properties.md)<br/>
Opisuje makra (stałe w czasie kompilacji), które mogą być używane do definiowania właściwości, takich jak ścieżki i wersje produktów.

[Typy plików utworzone dla projektów języka C++](file-types-created-for-visual-cpp-projects.md)<br/>
Opisuje różne rodzaje plików, które visual studio tworzy dla różnych typów projektów.

[Szablony projektów programu Visual Studio C++](visual-cpp-project-types.md)<br>
W tym artykule opisano typy projektów oparte na msbuild, które są dostępne dla języka C++.

[Szablony nowych elementów w języku C++](using-visual-cpp-add-new-item-templates.md)<br>
Zawiera opis plików źródłowych i innych elementów, które można dodać do projektu programu Visual Studio.

[Wstępnie skompilowane pliki nagłówkowe](../creating-precompiled-header-files.md) Jak używać wstępnie skompilowanych plików nagłówkowych i jak utworzyć własny niestandardowy wstępnie skompilowany kod, aby przyspieszyć czas kompilacji.

[Odwołanie do właściwości projektu programu Visual Studio](property-pages-visual-cpp.md)<br/>
Dokumentacja referencyjna dla właściwości projektu, które są ustawione w programie Visual Studio IDE.

## <a name="see-also"></a>Zobacz też

[Odwołanie kompilacji C/C++](c-cpp-building-reference.md)
