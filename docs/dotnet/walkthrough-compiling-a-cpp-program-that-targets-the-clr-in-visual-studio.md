---
title: Skompiluj program C++/CLI, który jest przeznaczony dla clr
description: Użyj programu Microsoft C++ do tworzenia programów i bibliotek, które mogą łączyć natywny kod C++ i programy .NET.
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 0d661d9e77211a0e49f8695ad713b607377a236a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371814"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>Instruktaż: Kompilowanie programu C++/CLI, który jest przeznaczony dla programu CLR w programie Visual Studio

Za pomocą języka C++/CLI można tworzyć programy języka C++, które używają klas .NET, a także natywnych typów C++. C++/CLI jest przeznaczony do użytku w aplikacjach konsoli i w bibliotekach DLL, które zawijają natywny kod C++ i udostępniają go z programów .NET. Aby utworzyć interfejs użytkownika systemu Windows oparty na .NET, użyj języka C# lub Języka Visual Basic.

W przypadku tej procedury można wpisać własny program C++ lub użyć jednego z przykładowych programów. Przykładowy program, którego używamy w tej procedurze, tworzy plik tekstowy o nazwie textfile.txt i zapisuje go w katalogu projektu.

## <a name="prerequisites"></a>Wymagania wstępne

- Zrozumienie podstaw języka C++.
- W programie Visual Studio 2017 i nowszych obsługa języka C++/CLI jest składnikiem opcjonalnym. Aby go zainstalować, otwórz **Instalatora programu Visual Studio** z menu Start systemu Windows. Upewnij się, że **programowanie pulpitu z** kafelkiem C++ jest zaznaczone, a w sekcji **Składniki opcjonalne** sprawdź również **obsługę języka C++/CLI**.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Poniższe kroki różnią się w zależności od używanej wersji programu Visual Studio. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj formantu selektor **wersji.** Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>Aby utworzyć projekt C++/CLI w programie Visual Studio 2019

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy u góry okno dialogowe **Tworzenie nowego projektu.**

1. W górnej części okna dialogowego wpisz **clr** w polu wyszukiwania, a następnie wybierz **pozycję CLR Pusty projekt** z listy wyników.

1. Wybierz przycisk **Utwórz,** aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>Aby utworzyć projekt C++/CLI w programie Visual Studio 2017

1. Tworzenie nowego projektu. W menu **Plik** wskaż polecenie **Nowy**, a następnie kliknij polecenie **Projekt**.

1. W typach projektów Visual C++ kliknij przycisk **CLR**, a następnie kliknij pozycję **CLR Empty Project**.

1. Wpisz nazwę projektu. Domyślnie rozwiązanie zawierające projekt ma taką samą nazwę jak nowy projekt, ale można wprowadzić inną nazwę. Jeśli chcesz, możesz wprowadzić inną lokalizację dla projektu.

1. Kliknij **przycisk OK,** aby utworzyć nowy projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>Aby utworzyć projekt C++/CLI w programie Visual Studio 2015

1. Tworzenie nowego projektu. W menu **Plik** wskaż polecenie **Nowy**, a następnie kliknij polecenie **Projekt**.

1. W typach projektów Visual C++ kliknij przycisk **CLR**, a następnie kliknij pozycję **CLR Empty Project**.

1. Wpisz nazwę projektu. Domyślnie rozwiązanie zawierające projekt ma taką samą nazwę jak nowy projekt, ale można wprowadzić inną nazwę. Jeśli chcesz, możesz wprowadzić inną lokalizację dla projektu.

1. Kliknij **przycisk OK,** aby utworzyć nowy projekt.

::: moniker-end

## <a name="add-a-source-file"></a>Dodawanie pliku źródłowego

1. Jeśli **Eksplorator rozwiązań** nie jest widoczny, kliknij polecenie **Eksplorator rozwiązań** w menu **Widok.**

1. Dodaj nowy plik źródłowy do projektu:

   - Kliknij prawym przyciskiem myszy folder **Pliki źródłowe** w **Eksploratorze rozwiązań,** wskaż polecenie **Dodaj**i kliknij polecenie **Nowy element**.

   - Kliknij **pozycję Plik C++ (cpp)** i wpisz nazwę pliku, a następnie kliknij przycisk **Dodaj**.

   Plik **cpp** pojawi się w folderze **Pliki źródłowe** w **Eksploratorze rozwiązań** i zostanie wyświetlane okno z kartami, w którym wpisujesz odpowiedni kod w tym pliku.

1. Kliknij nowo utworzoną kartę w programie Visual Studio i wpisz prawidłowy program Visual C++ lub skopiuj i wklej jeden z przykładowych programów.

   Na przykład można użyć przykładowego programu [Jak: Pisanie pliku tekstowego (C++/CLI)](how-to-write-a-text-file-cpp-cli.md) (w węźle **Obsługa plików i We/Wy** przewodnika programowania).

   Jeśli używasz przykładowego programu, zwróć `gcnew` uwagę, `new` że używasz słowa kluczowego `gcnew` zamiast podczas`^`tworzenia obiektu .NET, a to zwraca uchwyt ( ) zamiast wskaźnika (`*`):

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Aby uzyskać więcej informacji na temat składni C++/CLI, zobacz [Rozszerzenia składników dla platform środowiska wykonawczego](../extensions/component-extensions-for-runtime-platforms.md).

1. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

   Okno **Dane wyjściowe** wyświetla informacje o postępie kompilacji, takie jak lokalizacja dziennika kompilacji i komunikat wskazujący stan kompilacji.

   Jeśli wprowadzasz zmiany i uruchamiasz program bez wykonywania kompilacji, okno dialogowe może wskazywać, że projekt jest nieaktualny. Zaznacz pole wyboru w tym oknie dialogowym przed **kliknięciem przycisku OK,** jeśli program Visual Studio ma zawsze używać bieżących wersji plików zamiast monitować o za każdym razem, gdy tworzy aplikację.

1. W menu **Debugowanie** kliknij przycisk **Start bez debugowania**.

1. Jeśli używany był przykładowy program, po uruchomieniu programu zostanie wyświetlone okno poleceń wskazujące, że plik tekstowy został utworzony.

   Plik tekstowy **textfile.txt** znajduje się teraz w katalogu projektu. Możesz otworzyć ten plik za pomocą Notatnika.

   > [!NOTE]
   > Wybranie pustego szablonu projektu `/clr` CLR automatycznie ustawiło opcję kompilatora. Aby to sprawdzić, kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i kliknij polecenie **Właściwości**, a następnie sprawdź opcję **Obsługa środowiska uruchomieniowego języka wspólnego** w węźle **Ogólne** **właściwości konfiguracji**.

## <a name="see-also"></a>Zobacz też

[Odwołanie do języka języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)<br/>
