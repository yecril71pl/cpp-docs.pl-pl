---
title: Dziedziczenie właściwości w projektach programu Visual Studio — C++
description: Jak działa dziedziczenie właściwości w projektach natywnych (MSBuild) Visual Studio C++.
ms.date: 02/21/2020
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 4740c479c6cc7c877fd72b7828a8e4811826de6c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328475"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Dziedziczenie właściwości w projektach programu Visual Studio

Natywny system projektu programu Visual Studio jest oparty na systemie MSBuild. MSBuild definiuje formaty plików i reguły dla projektów budowlanych dowolnego rodzaju. Zarządza większość złożoności tworzenia dla wielu konfiguracji i platform. Przekonasz się, jak to działa. Jest to szczególnie ważne, jeśli chcesz zdefiniować konfiguracje niestandardowe. Lub, aby utworzyć wielokrotnego stosowania zestawów właściwości, które można udostępniać i importować do wielu projektów.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>Plik .vcxproj, .props plików i .targets plików

Właściwości projektu są przechowywane bezpośrednio w pliku*`.vcxproj`* projektu ( *`.targets`* ) *`.props`* lub w innych plikach lub plikach, które importuje plik projektu i które dostarczają wartości domyślne. W programie Visual Studio 2015 *`\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140`* pliki te znajdują się w programie . W programie Visual Studio 2017 *`\Program Files (x86)\Microsoft Visual Studio\2017\<edition>\Common7\IDE\VC\VCTargets`* te *`<edition>`* pliki znajdują się w programie , gdzie jest zainstalowana wersja programu Visual Studio. W programie Visual Studio 2019 *`\Program Files (x86)\Microsoft Visual Studio\2019\<edition>\MSBuild\Microsoft\VC\v160`* pliki te znajdują się w programie . Właściwości są również przechowywane *`.props`* w plikach niestandardowych, które można dodać do własnego projektu. Zdecydowanie zaleca się, aby NIE edytować tych plików ręcznie. Zamiast tego należy użyć stron właściwości w IDE, aby zmodyfikować wszystkie właściwości, zwłaszcza te, które uczestniczą w dziedziczeniu, chyba że masz głębokie zrozumienie MSBuild.

Jak pokazano wcześniej, tej samej właściwości dla tej samej konfiguracji mogą być przypisane inną wartość w tych różnych plików. Podczas tworzenia projektu aparat MSBuild ocenia plik projektu i wszystkie importowane pliki w dobrze zdefiniowanej kolejności (opisane poniżej). Podczas obliczynia każdego pliku wszystkie wartości właściwości zdefiniowane w tym pliku zastąpią istniejące wartości. Wszystkie wartości, które nie są określone są dziedziczone z plików, które zostały ocenione wcześniej. Po ustawieniu właściwości ze stronami właściwości, ważne jest również, aby zwrócić uwagę na to, gdzie ją ustawić. Jeśli ustawisz właściwość na *`.props`* "X" w pliku, ale właściwość jest ustawiona na "Y" w pliku projektu, projekt zostanie utworzony z właściwością ustawioną na "Y". Jeśli ta sama właściwość jest ustawiona na "Z" w elemencie projektu, takim jak *`.cpp`* plik, aparat MSBuild użyje wartości "Z".

Oto podstawowe drzewo dziedziczenia:

1. Ustawienia domyślne z zestawu narzędzi CPP MSBuild (.. \Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props, który jest *`.vcxproj`* importowany przez plik.)

1. Arkusze właściwości

1. *`.vcxproj`* Plik. (Można zastąpić ustawienia domyślne i ustawienia arkusza właściwości.)

1. Metadane elementów

> [!TIP]
> Na stronie właściwości właściwość **pogrubioną** jest zdefiniowana w bieżącym kontekście. Właściwość czcionką normalną jest dziedziczona.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>Wyświetlanie rozwiniętego pliku projektu ze wszystkimi zaimportowanymi wartościami

Czasami warto wyświetlić plik rozszerzony w celu stwierdzenia, jak jest dziedziczona dana wartość właściwości. Aby wyświetlić rozszerzoną wersję, wprowadź następujące polecenie w wierszu polecenia Visual Studio. (Zastąp nazwy plików zastępczych nazwami, których chcesz używać.)

> **msbuild /pp:**_temp_**.txt** _myapp_**.vcxproj**

Rozszerzone pliki projektu mogą być duże i trudne do zrozumienia, chyba że znasz MSBuild. Oto podstawowa struktura pliku projektu:

1. Podstawowe właściwości projektu, które nie są widoczne w IDE.

1. Import *`Microsoft.cpp.default.props`*, który definiuje niektóre podstawowe, właściwości niezależne od zestawu narzędzi.

1. Właściwości konfiguracji globalnej (udostępniane jako właściwości domyślne **narzędzia platformy i** **projektu** na stronie **Ogólne konfiguracja.** Właściwości te określają, który zestaw narzędzi i wewnętrzne arkusze właściwości są importowane w *`Microsoft.cpp.props`* następnym kroku.

1. Import *`Microsoft.cpp.props`*, który ustawia większość domyślnych ustawień projektu.

1. Importowanie wszystkich arkuszy *`.user`* właściwości, w tym plików. Te arkusze właściwości można zastąpić wszystko z wyjątkiem **PlatformToolset** i **Project** domyślne właściwości.

1. Pozostałe właściwości konfiguracji projektu. Te wartości mogą zastąpić to, co ustawiono w arkuszach właściwości.

1. Elementy (pliki) wraz z ich metadanymi. Te elementy są zawsze ostatnim słowem w regułach oceny MSBuild, nawet jeśli występują przed innymi właściwościami i importami.

Aby uzyskać więcej informacji, zobacz [WŁAŚCIWOŚCI MSBuild](/visualstudio/msbuild/msbuild-properties).

## <a name="build-configurations"></a>Konfiguracje kompilacji

Konfiguracja jest tylko dowolną grupą właściwości, które mają nazwę. Visual Studio udostępnia debugowanie i wersji konfiguracji. Każdy zestawi różne właściwości odpowiednio dla kompilacji debugowania lub wydania kompilacji. Za pomocą **programu Menedżer konfiguracji** można zdefiniować konfiguracje niestandardowe. Są one wygodnym sposobem grupowanie właściwości dla określonego smaku kompilacji.

Aby lepiej zorientować się w konfiguracji kompilacji, otwórz **Menedżera właściwości**. Można go otworzyć, wybierając **opcję Wyświetl > Menedżera właściwości** lub Wyświetl > Inne > Menedżera właściwości systemu **Windows**, w zależności od ustawień. **Menedżer właściwości** ma węzły dla każdej konfiguracji i pary platformy w projekcie. W każdym z tych węzłów znajdują*`.props`* się węzły dla arkuszy właściwości (plików), które ustawiają pewne określone właściwości dla tej konfiguracji.

![Menedżer właściwości](media/property-manager.png "Menedżer właściwości")

Na przykład można przejść do okienka Ogólne na stronach właściwości. Zmień właściwość Zestaw znaków na "Not Set" zamiast "Use Unicode", a następnie kliknij przycisk **OK**. Menedżer właściwości nie pokazuje teraz arkusza właściwości **Pomocy technicznej Unicode.** Jest usuwany dla bieżącej konfiguracji, ale nadal istnieje dla innych konfiguracji.

Aby uzyskać więcej informacji na temat Menedżera właściwości i arkuszy właściwości, zobacz [Udostępnianie lub ponowne używanie ustawień projektu programu Visual Studio C++](create-reusable-property-configurations.md).

> [!TIP]
> Plik *`.user`* jest starszą funkcją. Zaleca się, aby go usunąć, aby zachować właściwości poprawnie zgrupowane zgodnie z konfiguracją i platformą.
