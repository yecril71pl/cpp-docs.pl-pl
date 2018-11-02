---
title: 'Porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy'
ms.custom: conceptual
ms.date: 11/04/2016
f1_keywords:
- msbuild.cpp.howto.modifytargetframeworkandplatformtoolset
helpviewer_keywords:
- 'msbuild (c++), howto: modify target framework and platform toolset'
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
ms.openlocfilehash: 7759cf13e95fab97ee5a7b77e22c690a69fde41a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523122"
---
# <a name="how-to-modify-the-target-framework-and-platform-toolset"></a>Porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy

Możesz zmienić ustawienia projektu Visual C++ pod kątem różnych wersji programu .NET Framework i używać różnych zestawów narzędzi platformy. Domyślnie system projektu używa wersji .NET Framework i wersji zestawu narzędzi, które odnoszą się do wersji programu Visual Studio, którego używasz do tworzenia projektu. Możesz zmienić zestaw narzędzi platformy docelowej modyfikując właściwości projektu. Możesz zmienić szablon docelowy modyfikując plik projektu (.vcxproj). Nie trzeba utrzymywać osobnego kodu podstawowego dla każdego celu kompilacji.

> [!IMPORTANT]
>  Niektóre wersje mogą nie obsługiwać modyfikowanych docelowych platform ani zestawów narzędzi platformy. Aby uzyskać informacje o zgodności – zobacz [Port, migrowanie i uaktualnianie projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects).

Kiedy zmieniasz szablon docelowy, należy również zmienić zestaw narzędzi platformy na wersję obsługującą ten szablon. Na przykład pod kątem programu .NET Framework 4.5, należy użyć kompatybilnego zestawu narzędzi platformy takie jak Visual Studio 2015 (wersja 140), Visual Studio 2013 (v120) lub programu Visual Studio 2012 (v110). Możesz użyć **Windows7.1SDK** zestawu narzędzi platformy docelowej .NET Framework 2.0, 3.0, 3.5 i 4 i x86, Itanium i x64 platform.

> [!NOTE]
>  Aby zmienić zestaw narzędzi platformy docelowej, musi mieć odpowiednie wersje programu Visual Studio lub zestawu SDK platformy Windows, które zostały zainstalowane. Na przykład, aby Docelowa platforma Itanium z **Windows7.1SDK** zestawu narzędzi platformy, konieczne jest posiadanie [Microsoft Windows SDK for Windows 7 i platformy .NET Framework 4 z dodatkiem SP1](http://www.microsoft.com/download/details.aspx?id=8279) zainstalowany; Jednakże, można użyć innej zgodnej wersji programu Visual Studio do pracy programowania, pod warunkiem, że platformą docelową jest program poprawne Framework w wersji i zestawu narzędzi platformy.

Możesz rozszerzyć platformę docelową dalej tworząc niestandardowy zestaw narzędzi platformy. Aby uzyskać więcej informacji, zobacz [C++ natywna Wielowersyjność](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) na blogu Visual C++.

### <a name="to-change-the-target-framework"></a>Aby zmienić platformę docelową

1. W programie Visual Studio w **Eksploratora rozwiązań**, wybierz swój projekt. Na pasku menu Otwórz **projektu** menu i wybrać **Zwolnij projekt**. To wyładowuje plik projektu (.vcxproj) dla projektu.

    > [!NOTE]
    >  Nie można załadować projektu C++, gdy plik projektu jest modyfikowany w programie Visual Studio. Jednak służy innego edytora, takiego jak Notatnik do zmodyfikowania pliku projektu, gdy projekt jest ładowany w programie Visual Studio. Visual Studio wykryje, że plik projektu został zmieniony i wyświetlenie monitu o ponowne załadowanie projektu.

1. Na pasku menu wybierz **pliku**, **Otwórz**, **pliku**. W **Otwórz plik** okno dialogowe, przejdź do folderu projektu, a następnie otwórz plik projektu (.vcxproj).

1. W pliku projektu zlokalizuj wpis dla wersji platformy docelowej. Na przykład, jeśli projekt jest przeznaczony do użycia programu .NET Framework 4.5, zlokalizuj `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` w `<PropertyGroup Label="Globals">` elementu `<Project>` elementu. Jeśli `<TargetFrameworkVersion>` element nie jest obecny, projektu nie korzysta z programu .NET Framework i zmiana nie jest potrzebna.

1. Zmień wartość na wersję, której potrzebujesz, takie jak 3.5 lub wersje 4.6.

1. Zapisz zmiany i zamknąć Edytor.

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **Załaduj ponownie projekt**.

1. Aby sprawdzić zmiany, w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla projektu (a nie dla rozwiązania), a następnie wybierz **właściwości** można otworzyć projektu **właściwości Strony** okno dialogowe. W lewym okienku okna dialogowego, rozwiń **właściwości konfiguracji** , a następnie wybierz **ogólne**. Upewnij się, że **wersji platformy docelowej .NET** przedstawia wersję szablonu.

### <a name="to-change-the-project-toolset"></a>Aby zmienić zestaw narzędzi projektu

1. W programie Visual Studio w **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu (a nie dla rozwiązania), a następnie wybierz **właściwości** można otworzyć projektu **stron właściwości**okno dialogowe.

1. W **stron właściwości** po otwarciu okna dialogowego **konfiguracji** listy rozwijanej, a następnie wybierz **wszystkie konfiguracje**.

1. W lewym okienku okna dialogowego, rozwiń **właściwości konfiguracji** , a następnie wybierz **ogólne**.

1. W okienku po prawej stronie wybierz **zestawu narzędzi platformy** a następnie wybierz zestaw narzędzi ma z listy rozwijanej. Na przykład jeśli zainstalowano zestaw narzędzi Visual Studio 2010, wybierz pozycję **programu Visual Studio 2010 (v100)** z niej korzystać w projekcie.

1. Wybierz **OK** przycisku.

## <a name="see-also"></a>Zobacz też

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)