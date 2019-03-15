---
title: Projekty programu Visual Studio — C++
ms.date: 12/12/2018
f1_keywords:
- vcprojects
- creatingmanagingVC
helpviewer_keywords:
- ATL projects, creating
- Visual C++ projects, creating
- projects [C++], creating
- Visual C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: b5fb9ac87547578f101676d4cf424c7065155842
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823660"
---
# <a name="visual-studio-projects---c"></a>Projektów programu Visual Studio — C++

A *projektu programu Visual Studio* projekt zależy od systemu kompilacji MSBuild. Program MSBuild jest system kompilacji natywnej dla programu Visual Studio i ogólnie najlepsze kompilacji systemowi operacyjnemu używanie dla aplikacji platformy uniwersalnej systemu Windows, a także aplikacji pulpitu, korzystających z biblioteki ATL i MFC, składników COM i innych programów specyficzne dla Windows. Program MSBuild jest ściśle zintegrowana z programem Visual Studio, ale można go także użyć w wierszu polecenia. 

## <a name="create-a-project"></a>Tworzenie projektu

Utworzenia projektów w języku C++, należy wybrać **pliku &#124; nowy &#124; projektu**, a następnie wybierając Visual C++ w okienku po lewej stronie. W środkowym okienku można wyświetlić listę szablonów projektu: 

   ![Szablony projektów](../media/vs2017-new-project.png "programu Visual Studio 2017 nowego projektu okna dialogowego")

Aby uzyskać więcej informacji na temat wszystkie domyślne szablony projektów, które są zawarte w programie Visual Studio, zobacz [szablonów projektów języka C++ w programie Visual Studio](reference/visual-cpp-project-types.md). Można tworzyć własne szablony projektu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie szablonów projektów](/visualstudio/ide/how-to-create-project-templates).

Po utworzeniu projektu, pojawi się w [Eksploratora rozwiązań](/visualstudio/ide/solutions-and-projects-in-visual-studio) okna:

   ![Eksplorator rozwiązań](media/mathlibrary-solution-explorer-153.png)

Podczas tworzenia nowego projektu tworzony jest także plik rozwiązania (.sln). Można dodać dodatkowe projekty do rozwiązania, klikając prawym przyciskiem myszy na nim w **Eksploratora rozwiązań**. Plik rozwiązania służy do koordynowania zależności kompilacji, jeśli masz wiele powiązanych projektów, ale nie robi znacznie więcej niż. Wszystkie opcje kompilatora są ustawiane na poziomie projektu.

## <a name="add-items"></a>Dodawanie elementów

Dodawanie plików kodu źródłowego, ikony lub innych elementów do projektu, klikając prawym przyciskiem myszy nad projektem w **Eksploratora rozwiązań** i wybierając pozycję **Dodaj > Nowy** lub **Dodaj > istniejące**.

## <a name="add-third-party-libraries"></a>Dodawanie bibliotek innych firm

Aby dodać bibliotek innych firm, należy użyć [vcpkg](../vcpkg.md) Menedżera pakietów. Uruchom krok integracji programu Visual Studio, aby skonfigurować ścieżki do tej biblioteki, gdy odwołujesz z każdego projektu programu Visual Studio. 

## <a name="set-compiler-options-and-other-build-properties"></a>Ustaw opcje kompilatora i inne właściwości kompilacji

Aby skonfigurować ustawienia kompilacji dla projektu, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz polecenie **właściwości**. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](working-with-project-properties.md).

## <a name="compile-and-run"></a>Kompilowanie i uruchamianie

Aby skompilować i uruchomić nowy projekt, naciśnij klawisz **F5** lub kliknij przycisk *listy rozwijanej Debuguj* z zieloną strzałką na głównym pasku narzędzi. *Listy rozwijanej konfiguracji* jest, gdzie możesz zdecydować się przeprowadzić *debugowania* lub *wersji* kompilacji (lub innych niestandardowych konfiguracji).

Nowy projekt kompiluje bez błędów. Dodając własny kod, może co pewien czas wprowadzenia w błąd lub wyzwalania ostrzeżenia. Błąd uniemożliwia ukończenie; kompilacji Ostrzeżenie — nie. Wszystkie błędy i ostrzeżenia pojawi się zarówno w oknie danych wyjściowych, jak i na liście błędów podczas kompilowania projektu. 

   ![Dane wyjściowe okna i na liście błędów](../media/vs2017-output-error-list.png)

Na liście błędów, możesz nacisnąć przycisk **F1** w przypadku wyróżnione błędu, aby przejść do jego temat w dokumentacji.

## <a name="in-this-section"></a>W tej sekcji

[Ustaw kompilator języka C++ i właściwości w programie Visual Studio kompilacji](working-with-project-properties.md)<br/>
Jak używać stron właściwości i arkuszach właściwości, aby określić własne ustawienia projektu.

[Dokumentacja bibliotek i składników w czasie kompilacji](adding-references-in-visual-cpp-projects.md)<br/>
Jak dołączyć biblioteki i biblioteki dll, składniki COM i .NET w projekcie.
 
[Porządkowanie plików wyjściowych projektu](how-to-organize-project-output-files-for-builds.md)<br/>
Jak dostosować lokalizację plików wykonywalnych, utworzone w procesie kompilacji.

[Niestandardowych krokach budowania lub zdarzeniach kompilacji](understanding-custom-build-steps-and-build-events.md)<br/>
Jak dodać dowolnego dowolnego polecenia do procesu kompilacji w wybranych punktach.

[Tworzenie projektu z istniejącego kodu](how-to-create-a-cpp-project-from-existing-code.md)<br/>
Jak utworzyć nowy projekt programu Visual Studio z kolekcją luźno plików źródłowych.

## <a name="see-also"></a>Zobacz też

[Projekty i systemów kompilacji](projects-and-build-systems-cpp.md)<br>
