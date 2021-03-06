---
title: Kompiluj program C++/CLI, który jest przeznaczony dla środowiska CLR
description: Użyj języka Microsoft C++ do tworzenia programów i bibliotek, które mogą łączyć natywny kod C++ i programy .NET.
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 2fceb57e062b9179245ba235fb497ff526a6660e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501683"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>Przewodnik: kompilowanie programu C++/CLI, który jest przeznaczony dla środowiska CLR w programie Visual Studio

Za pomocą języka C++/CLI można tworzyć programy języka C++, które używają klas .NET, a także natywnych typów języka C++. Język c++/CLI jest przeznaczony do użycia w aplikacjach konsolowych i w bibliotekach DLL, które zawijają natywny kod C++ i umożliwiają dostęp z programów .NET. Aby utworzyć interfejs użytkownika systemu Windows oparty na platformie .NET, Użyj języka C# lub Visual Basic.

Ta procedura umożliwia wpisanie własnego programu C++ lub użycie jednego z przykładowych programów. Przykładowy program używany w tej procedurze tworzy plik tekstowy o nazwie textfile.txt i zapisuje go w katalogu projektu.

## <a name="prerequisites"></a>Wymagania wstępne

- Zrozumienie podstaw języka C++.
- W programie Visual Studio 2017 i nowszych, obsługa języka C++/CLI jest opcjonalnym składnikiem. Aby go zainstalować, Otwórz **Instalator programu Visual Studio** z menu Start systemu Windows. Upewnij się, że jest zaznaczone pole **Programowanie aplikacji klasycznych w języku C++** i w sekcji składniki **opcjonalne** Sprawdź również **obsługę języka c++/CLI**.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Poniższe kroki różnią się w zależności od używanej wersji programu Visual Studio. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj kontrolki selektora **wersji** . Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>Aby utworzyć projekt C++/CLI w programie Visual Studio 2019

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy u góry, aby otworzyć okno dialogowe **Tworzenie nowego projektu** .

1. W górnej części okna dialogowego wpisz **CLR** w polu wyszukiwania, a następnie wybierz pozycję **CLR pusty projekt** z listy wyników.

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>Aby utworzyć projekt C++/CLI w programie Visual Studio 2017

1. Tworzenie nowego projektu. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

1. W obszarze typy projektów Visual C++ kliknij pozycję **CLR**, a następnie kliknij pozycję **pusty projekt środowiska CLR**.

1. Wpisz nazwę projektu. Domyślnie rozwiązanie, które zawiera projekt, ma taką samą nazwę jak nowy projekt, ale można wprowadzić inną nazwę. Jeśli chcesz, możesz wprowadzić inną lokalizację dla projektu.

1. Kliknij przycisk **OK** , aby utworzyć nowy projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>Aby utworzyć projekt C++/CLI w programie Visual Studio 2015

1. Tworzenie nowego projektu. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

1. W obszarze typy projektów Visual C++ kliknij pozycję **CLR**, a następnie kliknij pozycję **pusty projekt środowiska CLR**.

1. Wpisz nazwę projektu. Domyślnie rozwiązanie, które zawiera projekt, ma taką samą nazwę jak nowy projekt, ale można wprowadzić inną nazwę. Jeśli chcesz, możesz wprowadzić inną lokalizację dla projektu.

1. Kliknij przycisk **OK** , aby utworzyć nowy projekt.

::: moniker-end

## <a name="add-a-source-file"></a>Dodawanie pliku źródłowego

1. Jeśli **Eksplorator rozwiązań** nie jest widoczny, kliknij przycisk **Eksplorator rozwiązań** w menu **Widok** .

1. Dodaj nowy plik źródłowy do projektu:

   - Kliknij prawym przyciskiem myszy folder **pliki źródłowe** w **Eksplorator rozwiązań**, wskaż polecenie **Dodaj**i kliknij pozycję **nowy element**.

   - Kliknij **plik C++ (. cpp)** i wpisz nazwę pliku, a następnie kliknij przycisk **Dodaj**.

   Plik **. cpp** zostanie wyświetlony w folderze **pliki źródłowe** w **Eksplorator rozwiązań** i zostanie wyświetlone okno z kartami, w którym można wpisać kod, który ma być w tym pliku.

1. Kliknij nowo utworzoną kartę w programie Visual Studio i wpisz prawidłowy program Visual C++ lub skopiuj i wklej jeden z przykładowych programów.

   Na przykład możesz użyć programu przykładowego [: Napisz plik tekstowy (C++/CLI)](./file-handling-and-i-o-cpp-cli.md#write_text) (w węźle **Obsługa plików i we/wy** przewodnika programowania).

   W przypadku korzystania z przykładowego programu należy zauważyć, że użycie **`gcnew`** słowa kluczowego zamiast **`new`** podczas tworzenia obiektu .NET i **`gcnew`** zwraca dojście (), `^` a nie wskaźnik ( `*` ):

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Aby uzyskać więcej informacji na temat składni języka C++/CLI, zobacz [rozszerzenia składników dla platform środowiska uruchomieniowego](../extensions/component-extensions-for-runtime-platforms.md).

1. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

   W oknie **dane wyjściowe** są wyświetlane informacje o postępie kompilacji, takie jak lokalizacja dziennika kompilacji i komunikat informujący o stanie kompilacji.

   Jeśli wprowadzisz zmiany i uruchomisz program bez wykonywania kompilacji, okno dialogowe może wskazywać, że projekt jest nieaktualny. Zaznacz pole wyboru w tym oknie dialogowym przed kliknięciem przycisku **OK** , jeśli chcesz, aby program Visual Studio zawsze używał bieżących wersji plików zamiast monitowania użytkownika za każdym razem, gdy kompiluje aplikację.

1. W menu **debugowanie** kliknij polecenie **Uruchom bez debugowania**.

1. Jeśli użyto przykładowego programu, podczas uruchamiania programu wyświetlane jest okno polecenia, które wskazuje, że plik tekstowy został utworzony.

   Plik tekstowy **textfile.txt** znajduje się teraz w katalogu projektu. Możesz otworzyć ten plik za pomocą Notatnika.

   > [!NOTE]
   > Wybór pustego szablonu projektu CLR powoduje automatyczne ustawienie `/clr` opcji kompilatora. Aby to sprawdzić, kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i kliknij polecenie **Właściwości**, a następnie sprawdź opcję **Obsługa środowiska uruchomieniowego** CLR **General** w węźle ogólne **Właściwości konfiguracji**.

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)<br/>
