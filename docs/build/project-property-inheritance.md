---
title: Dziedziczenie właściwości w projektach programu Visual Studio —C++
description: Jak dziedziczenie właściwości działa w projektach natywnych (MSBuild C++ ) Visual Studio.
ms.date: 02/21/2020
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 2032ab63c7d278a080742dba8d8d0c6c3ed7a094
ms.sourcegitcommit: 9a63e9b36d5e7fb13eab15c2c35bedad4fb03ade
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77600020"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Dziedziczenie właściwości w projektach programu Visual Studio

Natywny system projektu programu Visual Studio jest oparty na programie MSBuild. Program MSBuild definiuje formaty plików i reguły do tworzenia projektów dowolnego rodzaju. Zarządza większością złożoności kompilowania dla wielu konfiguracji i platform. Warto zrozumieć, jak to działa. Jest to szczególnie ważne, jeśli chcesz zdefiniować konfiguracje niestandardowe. Lub, aby utworzyć zestawy właściwości do wielokrotnego użytku, które można udostępniać i importować do wielu projektów.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>Plik. vcxproj,. props — pliki i. targets

Właściwości projektu są przechowywane bezpośrednio w pliku projektu ( *`.vcxproj`* ) lub w innych *`.targets`* lub *`.props`* plikach importowanych przez plik projektu i dostarczających wartości domyślne. W przypadku programu Visual Studio 2015 te pliki znajdują się w *`\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140`* . W przypadku programu Visual Studio 2017 te pliki znajdują się w *`\Program Files (x86)\Microsoft Visual Studio\2017\<edition>\Common7\IDE\VC\VCTargets`* , gdzie *`<edition>`* jest zainstalowana wersja programu Visual Studio. W programie Visual Studio 2019 te pliki znajdują się w *`\Program Files (x86)\Microsoft Visual Studio\2019\<edition>\MSBuild\Microsoft\VC\v160`* . Właściwości są również przechowywane w dowolnych niestandardowych plikach *`.props`* , które można dodać do własnego projektu. Zdecydowanie zalecamy, aby nie edytować tych plików ręcznie. Zamiast tego należy użyć stron właściwości w IDE, aby zmodyfikować wszystkie właściwości, szczególnie te, które uczestniczą w dziedziczeniu, chyba że masz głębokie zrozumienie programu MSBuild.

Jak pokazano wcześniej, taka sama właściwość dla tej samej konfiguracji może mieć przypisaną inną wartość w tych różnych plikach. Podczas kompilowania projektu aparat MSBuild ocenia plik projektu i wszystkie zaimportowane pliki w dobrze zdefiniowanej kolejności (opisane poniżej). W miarę oceniania każdego pliku wszystkie wartości właściwości zdefiniowane w tym pliku zastąpią istniejące wartości. Wszystkie wartości, które nie są określone, są dziedziczone z plików, które zostały ocenione wcześniej. Podczas ustawiania właściwości przy użyciu stron właściwości należy również zwrócić uwagę na to, gdzie ją ustawisz. Jeśli ustawisz właściwość na "X" w pliku *`.props`* , ale właściwość ma wartość "y" w pliku projektu, projekt zostanie skompilowany z właściwością ustawioną na wartość "y". Jeśli ta sama właściwość jest ustawiona na wartość "Z" w elemencie projektu, takim jak plik *`.cpp`* , aparat MSBuild będzie używał wartości "Z".

Oto podstawowe drzewo dziedziczenia:

1. Ustawienia domyślne z zestawu narzędzi programu MSBuild CPP (.. \Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props, który jest importowany przez plik *`.vcxproj`* .)

1. Arkusze właściwości

1. plik *`.vcxproj`* . (Można zastąpić ustawienia domyślne i ustawienia arkusza właściwości.)

1. Metadane elementów

> [!TIP]
> Na stronie właściwości Właściwość **pogrubiona** jest definiowana w bieżącym kontekście. Właściwość czcionką normalną jest dziedziczona.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>Wyświetlanie rozwiniętego pliku projektu ze wszystkimi zaimportowanymi wartościami

Czasami warto wyświetlić plik rozszerzony w celu stwierdzenia, jak jest dziedziczona dana wartość właściwości. Aby wyświetlić rozszerzoną wersję, wprowadź następujące polecenie w wierszu polecenia Visual Studio. (Zastąp nazwy plików zastępczych nazwami, których chcesz używać.)

> **MSBuild/PP:** _temp_ **. txt** _MojaApl_ **. vcxproj**

Rozwinięte pliki projektu mogą być duże i trudne do zrozumienia, chyba że znasz program MSBuild. Oto podstawowa struktura pliku projektu:

1. Podstawowe właściwości projektu, które nie są ujawniane w środowisku IDE.

1. Importowanie *`Microsoft.cpp.default.props`* , które definiuje podstawowe właściwości niezależne od zestawu narzędzi.

1. Globalne właściwości konfiguracji (uwidocznione jako **PlatformToolset** i domyślne właściwości **projektu** na stronie **Ogólne konfiguracji** ). Te właściwości określają, który zestaw narzędzi i wewnętrzne arkusze właściwości są importowane w *`Microsoft.cpp.props`* w następnym kroku.

1. Importowanie *`Microsoft.cpp.props`* , które ustawia większość wartości domyślnych projektu.

1. Importowanie wszystkich arkuszy właściwości, w tym plików *`.user`* . Te arkusze właściwości mogą zastąpić wszystko, z wyjątkiem właściwości domyślnych **PlatformToolset** i **Project** .

1. Pozostałe właściwości konfiguracji projektu. Te wartości mogą zastąpić to, co ustawiono w arkuszach właściwości.

1. Elementy (pliki) wraz z ich metadanymi. Te elementy są zawsze ostatnim słowem w regułach oceny MSBuild, nawet jeśli występują przed innymi właściwościami i importami.

Aby uzyskać więcej informacji, zobacz [Właściwości programu MSBuild](/visualstudio/msbuild/msbuild-properties).

## <a name="build-configurations"></a>Konfiguracje kompilacji

Konfiguracja jest tylko dowolną grupą właściwości, które mają nazwę. Program Visual Studio oferuje konfiguracje debugowania i wydawania. Każda z nich ustawia różne właściwości odpowiednio dla kompilacji debugowania lub kompilacji wydania. Za pomocą **Configuration Manager** można definiować konfiguracje niestandardowe. Są one wygodnym sposobem grupowania właściwości dla określonej wersji kompilacji.

Aby lepiej poznać konfiguracje kompilacji, Otwórz **Menedżer właściwości**. Można go otworzyć, wybierając pozycję **wyświetl > Menedżer właściwości** lub **widok > innych Menedżer właściwości > systemu Windows**, w zależności od ustawień. **Menedżer właściwości** ma węzły dla każdej pary konfiguracji i platformy w projekcie. W każdym z tych węzłów są węzły dla arkuszy właściwości (pliki *`.props`* ), które ustawiają określone właściwości dla danej konfiguracji.

![Menedżer właściwości](media/property-manager.png "Menedżer właściwości")

Na przykład możesz przejść do okienka ogólne na stronach właściwości. Zmień wartość właściwości zestaw znaków na "nie ustawiono" zamiast "Użyj Unicode", a następnie kliknij przycisk **OK**. Menedżer właściwości teraz nie zawiera arkusza właściwości **obsługi Unicode** . Jest ona usuwana dla bieżącej konfiguracji, ale nadal istnieje inna konfiguracja.

Aby uzyskać więcej informacji na temat Menedżer właściwości i arkuszy właściwości, zobacz [udostępnianie lub ponowne C++ Używanie ustawień projektu programu Visual Studio](create-reusable-property-configurations.md).

> [!TIP]
> Plik *`.user`* jest starszą funkcją. Firma Microsoft zaleca, aby je usunąć, aby zachować właściwości prawidłowo pogrupowane zgodnie z konfiguracją i platformą.
