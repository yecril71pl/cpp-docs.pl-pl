---
title: 'Porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: get-started-article
f1_keywords:
- msbuild.cpp.howto.modifytargetframeworkandplatformtoolset
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: modify target framework and platform toolset'
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
caps.latest.revision: 32
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ed85e0f1e1ce94401c505281c0e693a4904f92d
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-modify-the-target-framework-and-platform-toolset"></a>Porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy
Możesz zmienić ustawienia projektu Visual C++ pod kątem różnych wersji programu .NET Framework i używać innej platformie procesami. Domyślnie system projektu używa wersji programu .NET Framework i wersję zestawu narzędzi odnoszą się do wersji programu Visual Studio, która służy do tworzenia projektu. Zestaw narzędzi platformy docelowej można zmienić, modyfikując właściwości projektu. Element docelowy Framework można zmienić, modyfikując plik projektu (.vcxproj). Nie masz Obsługa oddzielny kod podstawowy dla każdego obiektu docelowego kompilacji.  
  
> [!IMPORTANT]
>  Niektóre wersje mogą nie obsługiwać zmodyfikowane docelowych platform lub procesami platformy. Aby uzyskać informacje dotyczące zgodności, zobacz [portu, migracji i uaktualniania projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects).  
  
 Jeśli zmienisz docelowej Framework również zmienić zestaw narzędzi platformy do wersji obsługującej tego Framework. Na przykład docelową programu .NET Framework 4.5, należy użyć narzędzi zgodną platformę, takiego jak Visual Studio 2015 (w wersji 140), programu Visual Studio 2013 (v120) lub programu Visual Studio 2012 (v110). Można użyć **Windows7.1SDK** zestaw narzędzi platformy .NET Framework 2.0, 3.0, 3.5, a 4 i x86, Itanium, docelowy i x64 platform.  
  
> [!NOTE]
>  Aby zmienić zestaw narzędzi platformy docelowej, musi mieć odpowiednie wersje programu Visual Studio lub zestawu SDK platformy Windows, które zostały zainstalowane. Na przykład, aby Docelowa platforma Itanium z **Windows7.1SDK** zestaw narzędzi platformy, musi mieć [Microsoft Windows SDK dla systemu Windows 7 i .NET Framework 4 z dodatkiem SP1](http://www.microsoft.com/download/details.aspx?id=8279) zainstalowany; można jednak użyć inny zgodnej wersji programu Visual Studio do pracy programowania, pod warunkiem, że docelowa poprawne Framework w wersji i zestawu narzędzi platformy.  
  
 Platforma docelowa dalsze można rozszerzyć przez utworzenie zestawu narzędzi platformy niestandardowej. Aby uzyskać więcej informacji, zobacz [C++ natywnego Wielowersyjności](http://go.microsoft.com/fwlink/p/?linkid=196619) na blogu Visual C++.  
  
### <a name="to-change-the-target-framework"></a>Aby zmienić docelowy Framework  
  
1.  W programie Visual Studio w **Eksploratora rozwiązań**, wybierz projekt. Na pasku menu, otwórz **projektu** menu i wybierz polecenie **Zwolnij projekt**. Zwalnia to pliku projektu (.vcxproj) dla projektu.  
  
    > [!NOTE]
    >  Nie można załadować projektu C++, gdy plik projektu jest modyfikowana w programie Visual Studio. Jednak można użyć innego edytora, takiego jak Notatnik, do zmodyfikowania pliku projektu, gdy projekt jest ładowany w programie Visual Studio. Visual Studio wykryje, że plik projektu została zmieniona i wyświetlony monit o ponowne załadowanie projektu.  
  
2.  Na pasku menu wybierz **pliku**, **Otwórz**, **pliku**. W **Otwieranie pliku** okno dialogowe, przejdź do folderu projektu, a następnie otwórz plik projektu (.vcxproj).  
  
3.  W pliku projektu zlokalizować wpis dla docelowej wersji struktury. Na przykład, jeśli projekt jest przeznaczony do użycia programu .NET Framework 4.5, zlokalizuj `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` w `<PropertyGroup Label="Globals">` elementu `<Project>` elementu. Jeśli `<TargetFrameworkVersion>` element nie jest obecny, projektu nie korzysta z programu .NET Framework i zmiana nie jest wymagane.  
  
4.  Zmień wartość na wersji platformy, które mają, np. w wersji 3.5 lub 4.6.  
  
5.  Zapisz zmiany i zamknij Edytor.  
  
6.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz pozycję **Załaduj ponownie projekt**.  
  
7.  Aby sprawdzić zmiany, w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów projektu (a nie dla rozwiązania), a następnie wybierz pozycję **właściwości** można otworzyć projektu **właściwości Strony** okno dialogowe. W lewym okienku okna dialogowego rozwiń **właściwości konfiguracji** , a następnie wybierz **ogólne**. Sprawdź, czy **.NET Framework w wersji docelowej** zawiera nową wersję Framework.  
  
### <a name="to-change-the-project-toolset"></a>Aby zmienić zestaw narzędzi projektu  
  
1.  W programie Visual Studio w **Eksploratora rozwiązań**, otwórz menu skrótów projektu (a nie dla rozwiązania), a następnie wybierz pozycję **właściwości** można otworzyć projektu **strony właściwości**okno dialogowe.  
  
2.  W **strony właściwości** po otwarciu okna dialogowego **konfiguracji** listy rozwijanej, a następnie wybierz **wszystkie konfiguracje**.  
  
3.  W lewym okienku okna dialogowego rozwiń **właściwości konfiguracji** , a następnie wybierz **ogólne**.  
  
4.  W okienku po prawej stronie zaznacz **zestaw narzędzi platformy** a następnie wybierz ma zestaw narzędzi z listy rozwijanej. Na przykład, jeśli zainstalowano [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)] zestawu narzędzi, wybierz opcję **programu Visual Studio 2010 (v100)** go użyć w projekcie.  
  
5.  Wybierz **OK** przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)