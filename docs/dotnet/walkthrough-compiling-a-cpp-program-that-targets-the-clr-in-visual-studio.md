---
title: Kompiluj w języku C + +/ interfejsu wiersza polecenia Program, który jest przeznaczony dla środowiska CLR
ms.date: 09/17/2018
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: fcac0079185b6ceef981b9acfeb555ef29d464e0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034673"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>Przewodnik: Kompiluj w języku C + +/ interfejsu wiersza polecenia programu, przeznaczonego dla CLR w programie Visual Studio

Za pomocą C + +/ interfejsu wiersza polecenia rozszerzenia językowe, można tworzyć programy w języku C++, które używają klas .NET i skompilować je przy użyciu środowiska programistycznego Visual Studio.

Do wykonania tej procedury możesz wpisać swój własny program C++ lub użyć jednego z przykładowych programów. Przykładowy program używanego w tej procedurze tworzy plik tekstowy o nazwie textfile.txt i zapisuje go do katalogu projektu.

## <a name="prerequisites"></a>Wymagania wstępne

Te tematy założono, że rozumiesz podstawy języka C++.

### <a name="to-create-a-new-project-in-visual-studio-and-add-a-new-source-file"></a>Aby utworzyć nowy projekt w programie Visual Studio i Dodaj nowy plik źródłowy

1. Utwórz nowy projekt. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.

1. Typy projektów Visual C++, kliknij **CLR**, a następnie kliknij przycisk **pusty projekt CLR**.

   > [!NOTE]
   > Jeśli **pusty projekt CLR** typu brakuje (Visual Studio 2017 tylko), wybierz **Otwórz Instalator programu Visual Studio** w lewym okienku **nowy projekt** okno dialogowe. Opcję znajdujący się w folderze instalacji **programowanie aplikacji klasycznych w języku C++** w **opcjonalnie** składniki sekcji o nazwie **C + +/ interfejsu wiersza polecenia**.<br/>

1. Wpisz nazwę projektu.

   Domyślnie rozwiązanie, zawierający projekt ma taką samą nazwę jak nowy projekt, ale można wprowadzić inną nazwę. Jeśli chcesz, możesz wprowadzić inną lokalizację dla projektu.

   Kliknij przycisk **OK** Aby utworzyć nowy projekt.

1. Jeśli **Eksploratora rozwiązań** nie jest widoczny, kliknij przycisk **Eksploratora rozwiązań** na **widoku** menu.

1. Dodaj nowy plik źródłowy do projektu:

   - Kliknij prawym przyciskiem myszy **pliki źródłowe** folderu w **Eksploratora rozwiązań**, wskaż polecenie **Dodaj**i kliknij przycisk **nowy element**.

   - Kliknij przycisk **plik C++ (.cpp)** i wpisz nazwę pliku, a następnie kliknij przycisk **Dodaj**.

   **.Cpp** plik pojawia się w **pliki źródłowe** folderu w **Eksploratora rozwiązań** i zostanie wyświetlone okno z kartami, za pomocą miejscem, gdzie wpisujesz kod ma w tym pliku.

1. Kliknij nowo utworzoną karcie w programie Visual Studio i wpisz prawidłowy program Visual C++ lub skopiuj i Wklej jeden z przykładowych programów.

   Na przykład, można użyć [jak: Wpisywanie tekstu do pliku (C + +/ CLI)](how-to-write-a-text-file-cpp-cli.md) przykładowego programu (w **Obsługa plików i we/wy** węzła Programming Guide).

   Jeśli korzystasz z przykładowego program, zwróć uwagę, że używasz `gcnew` słowa kluczowego zamiast `new` podczas tworzenia obiektu platformy .NET, a `gcnew` zwraca uchwyt (`^`) zamiast wskaźnik (`*`):

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Aby uzyskać więcej informacji na temat nowej składni języka Visual C++, zobacz [Component Extensions dla platform środowiska uruchomieniowego](../extensions/component-extensions-for-runtime-platforms.md).

1. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

   **Dane wyjściowe** okna wyświetla informacje o postępie kompilacji, takie jak lokalizacja dziennika kompilacji i komunikat o statusie kompilacji.

   Jeśli wprowadzono zmiany i uruchom program bez wykonania tej operacji kompilacji, okno dialogowe może oznaczać, że projekt jest nieaktualny. Zaznacz pole wyboru, w tym oknie dialogowym, zanim klikniesz pozycję **OK** Jeśli chcesz, aby Visual Studio, aby zawsze używać bieżącej wersji plików, zamiast monitowania użytkownika za każdym razem, tworzy on aplikacji.

1. Na **debugowania** menu, kliknij przycisk **Uruchom bez debugowania**.

1. Jeśli użyto przykładowego programu, po uruchomieniu program zostanie wyświetlone okno polecenia, który wskazuje, że utworzono plik tekstowy.

   **Textfile.txt** plik tekstowy znajduje się teraz w katalogu projektu. Możesz otworzyć ten plik za pomocą Notatnika.

   > [!NOTE]
   > Wybieranie CLR pusty szablon projektu automatycznie ustawiony `/clr` — opcja kompilatora. Aby to sprawdzić, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i klikając **właściwości**, a następnie sprawdź, **Obsługa środowiska uruchomieniowego języka wspólnego** opcji  **Ogólne** węźle **właściwości konfiguracji**.

## <a name="see-also"></a>Zobacz także

[Materiał referencyjny na temat języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemów kompilacji](../build/projects-and-build-systems-cpp.md)<br/>
