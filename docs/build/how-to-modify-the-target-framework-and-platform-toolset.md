---
title: 'Porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy'
ms.custom: conceptual
ms.date: 07/24/2019
helpviewer_keywords:
- 'msbuild (c++), howto: modify target framework and platform toolset'
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
ms.openlocfilehash: c5e7172fea06f6b455422fb023a0b6462b5c4103
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964903"
---
# <a name="how-to-modify-the-target-framework-and-platform-toolset"></a>Porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy

Można edytować plik projektu Visual Studio C++, aby wskazać różne wersje zestawu narzędzi platformy C++, Windows SDK i .NET Framework (tylko projekty C++/CLI). Domyślnie system projektu używa wersji .NET Framework i wersji zestawu narzędzi, która odpowiada wersji programu Visual Studio, która jest używana do tworzenia projektu. Można zmodyfikować wszystkie te wartości w pliku. vcxproj, aby można było używać tej samej bazy kodu dla każdego elementu docelowego kompilacji.

## <a name="platform-toolset"></a>Zestaw narzędzi platformy

Zestaw narzędzi platformy składa się z kompilatora C++ (CL. exe) i konsolidatora (link. exe) wraz z bibliotekami standardowymi C/C++. Ponieważ program Visual Studio 2015, główna wersja zestawu narzędzi pozostawała w 14, co oznacza, że projekty skompilowane z programem Visual Studio 2019 lub Visual Studio 2017 są zgodne z projektami skompilowanymi w programie Visual Studio 2015. Wersja pomocnicza została zaktualizowana o 1 dla każdej wersji, ponieważ program Visual Studio 2015:

- Visual Studio 2015: wersji 140
- Visual Studio 2017: Najnowsze 141
- Visual Studio 2019: v142

Te zestawy narzędzi obsługują .NET Framework 4,5 i nowszych.

Program Visual Studio obsługuje także wieloadresowanie dla projektów języka C++. Możesz użyć środowiska IDE programu Visual Studio do edytowania i kompilowania projektów, które zostały utworzone przy użyciu starszych wersji programu Visual Studio, bez uaktualniania ich do korzystania z nowej wersji zestawu narzędzi. Na komputerze muszą być zainstalowane starsze zestawy narzędzi. Aby uzyskać więcej informacji, zobacz [jak używać natywnego wielu elementów docelowych w programie Visual Studio](../porting/use-native-multi-targeting.md). Na przykład w programie Visual Studio 2015 można *kierować* do .NET Framework 2,0, ale musisz użyć wcześniejszego zestawu narzędzi, który go obsługuje.

## <a name="target-framework-ccli-project-only"></a>Platforma docelowa (tylko projekt C++/CLI)

W przypadku zmiany platformy docelowej należy również zmienić zestaw narzędzi platformy do wersji obsługującej tę platformę. Na przykład aby wskazać .NET Framework 4,5, należy użyć zgodnego zestawu narzędzi platformy, takiego jak Visual Studio 2015 (wersji 140), Visual Studio 2013 (v120) lub Visual Studio 2012 (v110). Zestaw narzędzi platformy [zestawu Windows 7,1 SDK](https://www.microsoft.com/download/details.aspx?id=8279) umożliwia używanie .NET Framework 2,0, 3,0, 3,5 i 4 oraz platform x86/x64.

Platformę docelową można zwiększyć, tworząc niestandardowy zestaw narzędzi platformy. Aby uzyskać więcej informacji, zobacz Blog dotyczący [wielu elementów docelowych języka C++](https://devblogs.microsoft.com/cppblog/c-native-multi-targeting/) w blogu Visual C++.

### <a name="to-change-the-target-framework"></a>Aby zmienić platformę docelową

1. W programie Visual Studio w obszarze **Eksplorator rozwiązań**wybierz projekt. Na pasku menu Otwórz menu **projekt** i wybierz polecenie **Zwolnij projekt**. Spowoduje to odładowanie pliku projektu (. vcxproj) dla projektu.

   > [!NOTE]
   >  Nie można załadować projektu C++, gdy plik projektu jest modyfikowany w programie Visual Studio. Można jednak użyć innego edytora, takiego jak Notatnik, aby zmodyfikować plik projektu, podczas gdy projekt jest ładowany w programie Visual Studio. Program Visual Studio wykryje, że plik projektu został zmieniony i wyświetli monit o ponowne załadowanie projektu.

1. Na pasku menu wybierz **plik**, **Otwórz**, **plik**. W oknie dialogowym **Otwórz plik** przejdź do folderu projektu, a następnie otwórz plik projektu (. vcxproj).

1. W pliku projektu Znajdź wpis dla wersji platformy docelowej. Na przykład, jeśli projekt jest przeznaczony do używania .NET Framework 4,5, Znajdź `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` w `<PropertyGroup Label="Globals">` elemencie `<Project>` elementu. Jeśli `<TargetFrameworkVersion>` element nie jest obecny, projekt nie używa .NET Framework i żadna zmiana nie jest wymagana.

1. Zmień wartość na żądaną wersję platformy, na przykład v 3.5 lub v 4.6.

1. Zapisz zmiany i Zamknij Edytor.

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Załaduj ponownie projekt**.

1. Aby sprawdzić zmianę, w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla projektu (nie dla rozwiązania), a następnie wybierz **Właściwości** , aby otworzyć okno dialogowe **strony właściwości** projektu. W lewym okienku okna dialogowego rozwiń węzeł **Właściwości konfiguracji** , a następnie wybierz pozycję **Ogólne**. Sprawdź, czy **wersja programu .NET Target Framework** zawiera nową wersję platformy.

### <a name="to-change-the-platform-toolset"></a>Aby zmienić zestaw narzędzi platformy

1. W programie Visual Studio w **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu (nie dla rozwiązania), a następnie wybierz **Właściwości** , aby otworzyć okno dialogowe **strony właściwości** projektu.

1. W oknie dialogowym **strony właściwości** Otwórz listę rozwijaną **Konfiguracja** , a następnie wybierz pozycję **wszystkie konfiguracje**.

1. W lewym okienku okna dialogowego rozwiń węzeł **Właściwości konfiguracji** , a następnie wybierz pozycję **Ogólne**.

1. W prawym okienku wybierz zestaw **narzędzi platformy** , a następnie wybierz żądany zestaw narzędzi z listy rozwijanej. Na przykład jeśli zainstalowano zestaw narzędzi programu Visual Studio 2010, wybierz pozycję **Visual studio 2010 (V100)** , aby użyć go dla projektu.

1. Wybierz przycisk **OK** .

## <a name="see-also"></a>Zobacz też

[MSBuild w wierszu polecenia — C++](msbuild-visual-cpp.md)
