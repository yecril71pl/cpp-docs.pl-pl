---
title: Dziedziczenie właściwości w projektach programu Visual Studio — C++
ms.date: 12/10/2018
helpviewer_keywords:
- Visual C++ projects, property inheritance
ms.openlocfilehash: edd6d3bf82f7a13cf6687abeba3758dcceca5e84
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823790"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Dziedziczenie właściwości w projektach programu Visual Studio

System projektu programu Visual Studio zależy od platformy MSBuild definiuje formaty plików i reguł do tworzenia projektów wszelkiego rodzaju. Program MSBuild zarządza wiele trudności, ponieważ tworzenie dla wielu platform i konfiguracje, ale trzeba nieco wiedzieć o tym, jak działa. Jest to szczególnie ważne, jeśli chcesz zdefiniować konfiguracje niestandardowe lub Utwórz wielokrotnego użytku zestawy właściwości, które można udostępniać i zaimportować do wielu projektów.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>Plik .vcxproj, .props pliki i pliki .targets

Właściwości projektu są przechowywane bezpośrednio w pliku projektu (*.vcxproj) lub w innych plikach .targets lub .props, że import pliku projektu, które dostarczają wartości domyślne. Dla programu Visual Studio 2015, te pliki znajdują się w **\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140**. Dla programu Visual Studio 2017, te pliki znajdują się w  **\\Program Files (x86)\\programu Microsoft Visual Studio\\2017\\_wersji_\\Common7\\ IDE\\VC\\VCTargets**, gdzie _wersji_ jest zainstalowanej wersji programu Visual Studio. Właściwości są także przechowywane w plikach .props niestandardowych, które można dodać do własnego projektu. Zdecydowanie zalecamy czy nie ręcznie edytować tych plików, a zamiast tego użyć strony właściwości w środowisku IDE, aby zmodyfikować wszystkie właściwości, zwłaszcza tych, które uczestniczą w dziedziczeniu, chyba że masz bardzo dobre Omówienie programu MSBuild.

Jak pokazano wcześniej, tę samą właściwość dla taką samą konfigurację można przypisać inną wartość w tych różnych plikach. Podczas tworzenia projektu, aparat MSBuild oblicza plik projektu i wszystkie zaimportowane pliki w dobrze zdefiniowanej kolejności (opisanych poniżej). Zgodnie z każdego pliku jest oceniany, wszystkie wartości właściwości zdefiniowane w tym pliku spowoduje zastąpienie istniejących wartości. Wszelkie wartości, które nie zostały określone są dziedziczone z plików, które zostały ocenione wcześniej. W związku z tym podczas ustawiania właściwości na stronach właściwości warto również zwrócić uwagę na gdzie ustawić. Jeśli właściwość jest ustawiona na "X" w pliku .props, ale właściwości jest równa "Y" w pliku projektu, projekt zostanie skompilowany z właściwością "Y". Jeśli w tej samej właściwości jest równa "Z" dla elementu projektu, np. plik .cpp, aparat MSBuild będzie używać wartości "Z". 

Oto podstawowe drzewo dziedziczenia:

1. Domyślne ustawienia z zestawu narzędzi CPP MSBuild (..\Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.cpp.default.props, który jest importowany przez plik .vcxproj.)

2. Arkusze właściwości

3. Plik .vcxproj. (Można zastąpić ustawienia domyślne i ustawienia arkusza właściwości.)

4. Metadane elementów

> [!TIP]
> Na stronie właściwości, właściwość w `bold` jest zdefiniowany w bieżącym kontekście. Właściwość czcionką normalną jest dziedziczona.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>Wyświetl plik projektu z wszystkich importowanych wartości

Czasami warto wyświetlić plik rozszerzony w celu stwierdzenia, jak jest dziedziczona dana wartość właściwości. Aby wyświetlić rozszerzoną wersję, wprowadź następujące polecenie w wierszu polecenia Visual Studio. (Zastąp nazwy plików zastępczych nazwami, których chcesz używać.)

**Program MSBuild /pp:** *temp* **.txt** *myapp* **.vcxproj**

Rozwinięte pliki projektu mogą być duże i trudne do zrozumienia, chyba że znasz MSBuild. Oto podstawowa struktura pliku projektu:

1. Podstawowe właściwości projektu, które nie są udostępniane w środowisku IDE.

2. Import pliku Microsoft.cpp.default.props, który określa pewne właściwości podstawowe, niezależne od zestawu narzędzi.

3. Globalne właściwości konfiguracji (udostępniane jako **PlatformToolset** i **projektu** właściwości domyślnych na **ogólne ustawienia konfiguracji** strony. Te właściwości określają, który zestaw narzędzi i które wewnętrzne arkusze właściwości są importowane w pliku Microsoft.cpp.props w następnym kroku.

4. Import pliku Microsoft.cpp.props, który określa większość ustawień domyślnych projektu.

5. Import wszystkich arkuszy właściwości, w tym plików .user. Arkusze właściwości można zastąpić wszystkim, z wyjątkiem **PlatformToolset** i **projektu** właściwości domyślnych.

6. Pozostałe właściwości konfiguracji projektu. Te wartości mogą zastąpić to, co ustawiono w arkuszach właściwości.

7. Elementy (pliki) wraz z ich metadanymi. To jest zawsze ostateczny wynik, jeśli chodzi o reguły oceny MSBuild, nawet jeśli występują one przed innymi właściwościami i importami.

Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](/visualstudio/msbuild/msbuild-properties).

## <a name="build-configurations"></a>Konfiguracje kompilacji

Konfiguracja jest po prostu dowolne grupy właściwości, które są określone nazwy. Program Visual Studio oferuje konfiguracje Debug i Release, i każdy ustawia różne właściwości odpowiednio do kompilacji debugowania lub kompilacji wydania. Możesz użyć **programu Configuration Manager** konfiguracje niestandardowe jest definiowana jako wygodny sposób właściwości grupy dla określonej wersji kompilacji. 

Aby lepiej zrozumieć, konfiguracje kompilacji, otwórz **Menedżer właściwości** , wybierając **widoku &#124; Menedżer właściwości** lub **widoku &#124; Windows inne &#124; Menedżer właściwości**  w zależności od ustawień. **Menedżer właściwości** ma węzły dla każdej pary konfiguracji i platformy w projekcie. W każdym z tych węzłów są węzły arkusze właściwości (pliki .props), które ustawić niektóre określonych właściwości dla tej konfiguracji.

![Menedżer właściwości](media/property-manager.png "Menedżer właściwości")

Jeśli przejdź do okienka ogólne na stronach właściwości i ustaw właściwość zestawu znaków na "Nieustawione" zamiast "Użyj Unicode" i kliknij **OK**, wyświetli się Menedżer właściwości nie **obsługi standardu Unicode** arkusz właściwości bieżącej konfiguracji, ale nadal będą dostępne dla innych konfiguracji.

Aby uzyskać więcej informacji o Menedżerze właściwości i arkuszach właściwości, zobacz [udziału lub resuse ustawienia projektu Visual Studio C++](create-reusable-property-configurations.md).

> [!TIP]
> Plik .user, odnoszący jest funkcją starszej wersji, a firma Microsoft zaleca, Usuń Aby zachować właściwości poprawnie pogrupowane według konfiguracji i platformy.



