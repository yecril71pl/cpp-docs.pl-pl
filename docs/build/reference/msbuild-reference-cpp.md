---
title: Odwołanie do MSBuild dla projektów języka C++ w programie Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: b6ec6b5d276cb7104cf61c229476596d2a2a7684
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024702"
---
# <a name="msbuild-reference-for-c-projects"></a>Odwołanie do MSBuild dla projektów języka C++

Program MSBuild jest system kompilacji natywnej dla wszystkich projektów w programie Visual Studio, w tym projektów w języku C++. Podczas tworzenia projektu w programie Visual Studio zintegrowane środowisko programistyczne (IDE), wywołuje narzędzie msbuild.exe, które z kolei używa pliku projektu .vcxproj i różnych plików .targets i props. Ogólnie rzecz biorąc zdecydowanie zaleca się ustawiania właściwości projektu i wywoływania MSBuild, przy użyciu programu Visual Studio IDE. Ręczna Edycja plików projektu może prowadzić do poważnych problemów, jeśli nie jest prawidłowo wykonane.

Jeśli z jakiegoś powodu chcesz użyć programu MSBuild bezpośrednio z poziomu wiersza polecenia, zobacz [Użyj programu MSBuild w wierszu polecenia](../msbuild-visual-cpp.md). Aby uzyskać więcej informacji na temat MSBuild ogólnie rzecz biorąc, zobacz [MSBuild](/visualstudio/msbuild/msbuild) w dokumentacji programu Visual Studio.

## <a name="in-this-section"></a>W tej sekcji

[Funkcje wewnętrzne aparatu MSBuild dla projektów w języku C++](msbuild-visual-cpp-overview.md)<br/>
Informacje dotyczące sposobu cele i właściwości są przechowywane i używane.

[Typowe makra dla właściwości i poleceń kompilacji](common-macros-for-build-commands-and-properties.md)<br/>
W tym artykule opisano makra (stałych kompilacji), które mogą służyć do definiowania właściwości, takich jak ścieżki i wersji produktu.

[Typy plików utworzonych dla projektów w języku C++](file-types-created-for-visual-cpp-projects.md)<br/>
W tym artykule opisano różne rodzaje plików, które program Visual Studio tworzy dla różnych typach projektów.

[Szablony projektu programu Visual Studio C++](visual-cpp-project-types.md)<br>
Zawiera opis typów projektów opartych na platformie MSBuild, które są dostępne dla języka C++.

[Szablony nowych elementów w języku C++](using-visual-cpp-add-new-item-templates.md)<br>
Opisuje pliki źródłowe i inne elementy, które można dodać do projektu programu Visual Studio.

[Prekompilowanych plików nagłówka](../creating-precompiled-header-files.md) w jaki sposób używać prekompilowane pliki nagłówka oraz jak tworzyć własne wstępnie skompilowany kod, aby skrócić czas kompilacji.

[Odwołanie do właściwości projektu Visual Studio](property-pages-visual-cpp.md)<br/>
Dokumentacja dotycząca właściwości projektu, które są ustawiane w środowisku IDE programu Visual Studio.

## <a name="see-also"></a>Zobacz także

[Dokumentacja kompilacji w języku C/C++](c-cpp-building-reference.md)