---
title: Projekty programu Visual Studio — C++
ms.date: 10/25/2019
helpviewer_keywords:
- ATL projects, creating
- Visual Studio C++ projects, creating
- projects [C++], creating
- Visual Studio C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: 3694478e22bfd2a3c58a72ba0c3ad2d15351bc9f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078696"
---
# <a name="visual-studio-projects---c"></a>Projekty programu Visual Studio — C++

*Projekt programu Visual Studio* jest projektem opartym na systemie kompilacji MSBuild. MSBuild jest natywnym systemem kompilacji dla programu Visual Studio i jest generalnie najlepszym systemem kompilacji do użycia dla programów specyficznych dla systemu Windows. Program MSBuild jest ściśle zintegrowany z programem Visual Studio, ale można go również użyć z poziomu wiersza polecenia. W przypadku projektów dla wielu platform lub projektów korzystających z bibliotek Open Source zalecamy używanie [projektów CMAKE w programie Visual](cmake-projects-in-visual-studio.md) Studio w programie visual Studio 2017 i nowszych. Informacje o uaktualnianiu projektów programu MSBuild ze starszych wersji programu Visual Studio można znaleźć w [przewodniku dotyczącym przenoszenia i uaktualniania języka Microsoft C++](../porting/visual-cpp-porting-and-upgrading-guide.md).

## <a name="create-a-project"></a>Tworzenie projektu

::: moniker range="vs-2019"

Projekty języka c++ można tworzyć, wybierając kolejno pozycje **plik** > **Nowy** > **projekt**, a następnie ustawiając **Język** na C++. Na liście wyników zostanie wyświetlona lista szablonów projektu, które można filtrować, ustawiając typ **platformy** lub **projektu** oraz wpisując słowa kluczowe w polu wyszukiwania.

   ![Szablony projektów programu Visual Studio 2019](../build/media/vs2019-choose-console-app.png "Okno dialogowe nowego projektu programu Visual Studio 2019")

::: moniker-end

::: moniker range="vs-2017"

Projekty języka C++ można tworzyć, wybierając kolejno pozycje **plik** > **Nowy** > **projekt**, a następnie wybierając Visual C++ w okienku po lewej stronie. W środkowym okienku zostanie wyświetlona lista szablonów projektu:

   ![Szablony projektów](../overview/media/vs2017-new-project.png "Okno dialogowe nowego projektu programu Visual Studio 2017")

::: moniker-end

Aby uzyskać więcej informacji na temat wszystkich domyślnych szablonów projektu, które są zawarte w Visual Studio, zobacz [Szablony projektów C++ w programie Visual Studio](reference/visual-cpp-project-types.md). Możesz tworzyć własne szablony projektów. Aby uzyskać więcej informacji, zobacz [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).

Po utworzeniu projektu jest on wyświetlany w oknie [Eksplorator rozwiązań](/visualstudio/ide/solutions-and-projects-in-visual-studio) :

   ![Eksplorator rozwiązań](media/mathlibrary-solution-explorer-153.png)

Podczas tworzenia nowego projektu tworzony jest również plik rozwiązania (. sln). Możesz dodać kolejne projekty do rozwiązania, klikając je prawym przyciskiem myszy w **Eksplorator rozwiązań**. Plik rozwiązania służy do koordynowania zależności kompilacji, gdy istnieje wiele powiązanych projektów, ale nie jest to znacznie więcej niż. Wszystkie opcje kompilatora są ustawiane na poziomie projektu.

## <a name="add-items"></a>Dodawanie elementów

Dodaj pliki kodu źródłowego, ikony lub inne elementy do projektu, klikając prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierając polecenie **Dodaj > nowe** lub **Dodaj > istniejące**.

## <a name="add-third-party-libraries"></a>Dodaj biblioteki innych firm

Aby dodać biblioteki innych firm, użyj Menedżera pakietów [vcpkg](vcpkg.md) . Uruchom krok integracja z programem Visual Studio, aby skonfigurować ścieżki do tej biblioteki podczas odwoływania się do niej z dowolnego projektu programu Visual Studio.

## <a name="set-compiler-options-and-other-build-properties"></a>Ustawianie opcji kompilatora i innych właściwości kompilacji

Aby skonfigurować ustawienia kompilacji dla projektu, kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. Aby uzyskać więcej informacji, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](working-with-project-properties.md).

## <a name="compile-and-run"></a>Kompiluj i uruchom

Aby skompilować i uruchomić nowy projekt, naciśnij klawisz **F5** lub kliknij *listę rozwijaną Debug* z zieloną strzałką na głównym pasku narzędzi. *Lista rozwijana konfiguracji* umożliwia wybranie, czy należy przeprowadzić kompilację *debugowania* czy *wydania* (lub inną konfigurację niestandardową).

Nowy projekt kompiluje się bez błędów. Podczas dodawania własnego kodu możesz czasami wprowadzić błąd lub wyzwolić ostrzeżenie. Błąd uniemożliwia ukończenie kompilacji; Ostrzeżenie nie jest. Wszystkie błędy i ostrzeżenia pojawią się zarówno w Okno Dane wyjściowe, jak i w Lista błędów podczas kompilowania projektu.

   ![Okno danych wyjściowych i Lista błędów](../overview/media/vs2017-output-error-list.png)

W Lista błędów można nacisnąć klawisz **F1** w wyróżnionym błędzie, aby przejść do tematu dokumentacji.

## <a name="in-this-section"></a>W tej sekcji

[Ustawianie właściwości kompilacji i kompilatora języka C++ w programie Visual Studio](working-with-project-properties.md)<br/>
Jak używać stron właściwości i arkuszy właściwości do określania ustawień projektu.

[Odwoływanie się do bibliotek i składników podczas kompilacji](adding-references-in-visual-cpp-projects.md)<br/>
Jak dołączyć składniki libs, DLL, COM i .NET do projektu.

[Porządkowanie plików wyjściowych projektu](how-to-organize-project-output-files-for-builds.md)<br/>
Jak dostosować lokalizację plików wykonywalnych utworzonych w procesie kompilacji.

[Niestandardowe kroki kompilacji i zdarzenia kompilacji](understanding-custom-build-steps-and-build-events.md)<br/>
Jak dodać dowolne dowolne polecenie do procesu kompilacji w określonych punktach.

[Tworzenie projektu z istniejącego kodu](how-to-create-a-cpp-project-from-existing-code.md)<br/>
Jak utworzyć nowy projekt programu Visual Studio na podstawie luźnej kolekcji plików źródłowych.

## <a name="see-also"></a>Zobacz też

[Projekty i systemy kompilacji](projects-and-build-systems-cpp.md)<br>
[Przewodnik dotyczący przenoszenia i uaktualniania języka Microsoft C++](../porting/visual-cpp-porting-and-upgrading-guide.md)
