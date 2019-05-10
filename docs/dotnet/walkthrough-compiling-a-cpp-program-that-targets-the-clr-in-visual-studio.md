---
title: Skompilować C++sposób niezamierzony Program, który jest przeznaczony dla środowiska CLR
description: Użyj usługi Microsoft C++ do tworzenia programów i bibliotek, które można połączyć z natywnych C++ kodu i programy platformy .NET.
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 8462b2b031bdcdebf65d58974c521d80e57d856d
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221807"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>Przewodnik: Skompilować C++Program w sposób niezamierzony, przeznaczonego dla CLR w programie Visual Studio

Za pomocą C++/interfejsu wiersza polecenia można utworzyć C++ programów, które używają klas platformy .NET, a także native C++ typów. C++/ Interfejs wiersza polecenia jest przeznaczony do użycia w aplikacji konsoli w bibliotekach DLL, które umieszczają w otoce natywnych C++ kod i go udostępnić z programy platformy .NET. Aby utworzyć interfejs użytkownika Windows oparte na platformie .NET, należy użyć C# lub Visual Basic. 

Do wykonania tej procedury możesz wpisać swój własny program C++ lub użyć jednego z przykładowych programów. Przykładowy program używanego w tej procedurze tworzy plik tekstowy o nazwie textfile.txt i zapisuje go do katalogu projektu.

## <a name="prerequisites"></a>Wymagania wstępne

- Po zrozumieniu podstaw języka C++.
- W programie Visual Studio 2017 i nowszych C++/obsługę interfejsu wiersza polecenia jest opcjonalnym składnikiem. Aby go zainstalować, otwórz **Instalatora programu Visual Studio** z menu Windows Start. Upewnij się, że **programowanie aplikacji klasycznych przy użyciu C++**  kafelka jest zaznaczone, a następnie w **opcjonalne** sekcji składników, również sprawdzanie poprawności  **C++obsługę interfejsu wiersza polecenia**.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Poniższe kroki różnią się w zależności od tego, która wersja programu Visual Studio, którego używasz. Upewnij się, że selektor wersji, w lewym górnym rogu tej strony została prawidłowo ustawiona.

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>Aby utworzyć C++sposób niezamierzony projekt w programie Visual Studio 2019 r.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy, u góry, aby otworzyć **Utwórz nowy projekt** okno dialogowe.

1. W górnej części okna dialogowego wpisz **CLR** w wyszukiwaniu pole, a następnie wybierz **pusty projekt CLR** z listy wyników. 

1. Wybierz **Utwórz** przycisk, aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>Aby utworzyć C++sposób niezamierzony projektu w programie Visual Studio 2017

1. Utwórz nowy projekt. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.

1. Typy projektów Visual C++, kliknij **CLR**, a następnie kliknij przycisk **pusty projekt CLR**.

1. Wpisz nazwę projektu. Domyślnie rozwiązanie, zawierający projekt ma taką samą nazwę jak nowy projekt, ale można wprowadzić inną nazwę. Jeśli chcesz, możesz wprowadzić inną lokalizację dla projektu.

1. Kliknij przycisk **OK** Aby utworzyć nowy projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>Aby utworzyć C++sposób niezamierzony projektu w programie Visual Studio 2015

1. Utwórz nowy projekt. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.

1. Typy projektów Visual C++, kliknij **CLR**, a następnie kliknij przycisk **pusty projekt CLR**.

1. Wpisz nazwę projektu. Domyślnie rozwiązanie, zawierający projekt ma taką samą nazwę jak nowy projekt, ale można wprowadzić inną nazwę. Jeśli chcesz, możesz wprowadzić inną lokalizację dla projektu.

1. Kliknij przycisk **OK** Aby utworzyć nowy projekt.

::: moniker-end

## <a name="add-a-source-file"></a>Dodawanie pliku źródłowego

1. Jeśli **Eksploratora rozwiązań** nie jest widoczny, kliknij przycisk **Eksploratora rozwiązań** na **widoku** menu.

1. Dodaj nowy plik źródłowy do projektu:

   - Kliknij prawym przyciskiem myszy **pliki źródłowe** folderu w **Eksploratora rozwiązań**, wskaż polecenie **Dodaj**i kliknij przycisk **nowy element**.

   - Kliknij przycisk **plik C++ (.cpp)** i wpisz nazwę pliku, a następnie kliknij przycisk **Dodaj**.

   **.Cpp** plik pojawia się w **pliki źródłowe** folderu w **Eksploratora rozwiązań** i zostanie wyświetlone okno z kartami, za pomocą miejscem, gdzie wpisujesz kod ma w tym pliku.

1. Kliknij nowo utworzoną karcie w programie Visual Studio i wpisz prawidłowy program Visual C++ lub skopiuj i Wklej jeden z przykładowych programów.

   Na przykład, można użyć [jak: Wpisywanie tekstu do pliku (C++sposób niezamierzony)](how-to-write-a-text-file-cpp-cli.md) przykładowego programu (w **Obsługa plików i we/wy** węzła Programming Guide).

   Jeśli korzystasz z przykładowego program, zwróć uwagę, że używasz `gcnew` słowa kluczowego zamiast `new` podczas tworzenia obiektu platformy .NET, a `gcnew` zwraca uchwyt (`^`) zamiast wskaźnik (`*`):

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Aby uzyskać więcej informacji na temat C++sposób niezamierzony składni, zobacz [Component Extensions dla platform środowiska uruchomieniowego](../extensions/component-extensions-for-runtime-platforms.md).

1. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

   **Dane wyjściowe** okna wyświetla informacje o postępie kompilacji, takie jak lokalizacja dziennika kompilacji i komunikat o statusie kompilacji.

   Jeśli wprowadzono zmiany i uruchom program bez wykonania tej operacji kompilacji, okno dialogowe może oznaczać, że projekt jest nieaktualny. Zaznacz pole wyboru, w tym oknie dialogowym, zanim klikniesz pozycję **OK** Jeśli chcesz, aby Visual Studio, aby zawsze używać bieżącej wersji plików, zamiast monitowania użytkownika za każdym razem, tworzy on aplikacji.

1. Na **debugowania** menu, kliknij przycisk **Uruchom bez debugowania**.

1. Jeśli użyto przykładowego programu, po uruchomieniu program zostanie wyświetlone okno polecenia, który wskazuje, że utworzono plik tekstowy.

   **Textfile.txt** plik tekstowy znajduje się teraz w katalogu projektu. Możesz otworzyć ten plik za pomocą Notatnika.

   > [!NOTE]
   > Wybieranie CLR pusty szablon projektu automatycznie ustawiony `/clr` — opcja kompilatora. Aby to sprawdzić, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i klikając **właściwości**, a następnie sprawdź, **Obsługa środowiska uruchomieniowego języka wspólnego** opcji  **Ogólne** węźle **właściwości konfiguracji**.

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)<br/>
