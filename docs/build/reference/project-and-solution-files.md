---
title: Pliki projektu i rozwiązania
ms.date: 05/06/2019
helpviewer_keywords:
- project files [C++]
- file types [C++], makefiles
- .sdf, browsing database file
- Makefile projects
- browsing database file, .sdf
- file types [C++], project files
ms.assetid: 5823b954-36cf-42d3-8fd5-25bab3ef63d9
ms.openlocfilehash: 37bfd1a6db2087e97ab76d3d06ed6f56e59b96e3
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707414"
---
# <a name="project-and-solution-files"></a>Pliki projektu i rozwiązania

Następujące pliki są tworzone podczas tworzenia projektu w programie Visual Studio. Są one używane do zarządzania plików projektu w rozwiązaniu.

|Nazwa pliku|Lokalizacja katalogu|Lokalizacja Eksploratora rozwiązań|Opis|
|--------------|------------------------|--------------------------------|-----------------|
|*Solname*SLN|*Projname*|Nie są wyświetlane w Eksploratorze rozwiązań|*Rozwiązania* pliku. Organizuje ona wszystkie elementy projektu lub wielu projektów w jednym rozwiązaniu.|
|*Projname*.suo|*Projname*|Nie są wyświetlane w Eksploratorze rozwiązań|*Opcje rozwiązania* pliku. Tak, aby zawsze po otwarciu projektu lub pliku w rozwiązaniu, ma wygląd i zachowanie, które mają przechowuje dostosowania rozwiązania.|
|*Projname*.vcxproj|*Projname*|Nie są wyświetlane w Eksploratorze rozwiązań|*Projektu* pliku. Przechowuje informacje specyficzne dla każdego projektu. (We wcześniejszych wersjach nosiła nazwę tego pliku *Projname*.vcproj lub *Projname*.dsp.) Na przykład C++ (.vcxproj) pliku projektu, zobacz [pliki projektu](project-files.md).|
|*Projname*.vcxitems|*Projname*|Nie są wyświetlane w Eksploratorze rozwiązań|*Projekt elementy udostępnione* pliku. Ten projekt nie jest wbudowane.  Zamiast tego projektu mogą być przywoływane przez inny projekt C++, a jego pliki będą należały do procesu kompilacji projektu odwołującego się. Może to służyć do udostępnić wspólny kod z projektów w języku C++ dla wielu platform.|
|*Projname*.sdf|*Projname*|Nie są wyświetlane w Eksploratorze rozwiązań|*Baza danych przeglądania* pliku. Obsługuje przeglądanie i nawigacji funkcje takie jak **przejdź do definicji**, **Znajdź wszystkie odwołania**, i **Widok klas**. Są one generowane przez analizowanie plików nagłówkowych.|
|*Projname*. vcxproj.filters|*Projname*|Nie są wyświetlane w Eksploratorze rozwiązań|*Filtry* pliku. Określa, gdzie umieścić plik, który jest dodawany do rozwiązania. Na przykład plik .h jest umieszczany w **pliki nagłówkowe** węzła.|
|*Projname*. vcxproj.user|*Projname*|Nie są wyświetlane w Eksploratorze rozwiązań|*Użytkownika migracji* pliku. Po przeprowadzeniu migracji projektu z programu Visual Studio 2008, ten plik zawiera informacje, które została przekonwertowana z dowolnego pliku .vsprops.|
|*Projname*.idl|*Projname*|Source|(Specyficzne dla projektu) Zawiera kod źródłowy języka opisu interfejsu (IDL) dla biblioteki typu formantu. Ten plik jest używany przez Visual C++ można wygenerować bibliotekę typów. Wygenerowany biblioteki udostępnia interfejs kontroli innym klientom automatyzacji. Aby uzyskać więcej informacji, zobacz [plik definicji interfejsu (IDL)](/windows/desktop/Rpc/the-interface-definition-language-idl-file) w zestawie Windows SDK.|
|Plik Readme.txt|*Projname*|Projekt|*Readme* pliku. On są generowane przez Kreatora aplikacji oraz opis pliki w projekcie.|

## <a name="see-also"></a>Zobacz także

[Plik typy utworzone dla programu Visual Studio C++ projektów](file-types-created-for-visual-cpp-projects.md)
