---
title: Kompiluj program C++/CLI, który jest przeznaczony dla środowiska CLR
description: Użyj firmy C++ Microsoft do tworzenia programów i bibliotek, które mogą C++ łączyć kod natywny i programy platformy .NET.
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 36c41856dfcdb5c5f50ba59205b4c73c5fde5963
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080016"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>Przewodnik: kompilowanie C++programu/CLI, który jest przeznaczony dla środowiska CLR w programie Visual Studio

Za pomocą C++/CLI można tworzyć C++ programy korzystające z klas .NET, a także typy C++ natywne. C++/CLI jest przeznaczona do użycia w aplikacjach konsolowych i w bibliotekach DLL C++ , które zawijają kod natywny i umożliwiają dostęp z programów .NET. Aby utworzyć interfejs użytkownika systemu Windows oparty na platformie .NET, C# użyj lub Visual Basic.

W ramach tej procedury można wpisać własny C++ program lub użyć jednego z przykładowych programów. Przykładowy program używany w tej procedurze tworzy plik tekstowy o nazwie textfile. txt i zapisuje go w katalogu projektu.

## <a name="prerequisites"></a>Wymagania wstępne

- Zrozumienie podstaw C++ języka.
- W programie Visual Studio 2017 i nowszych C++/CLI jest to opcjonalny składnik. Aby go zainstalować, Otwórz **Instalator programu Visual Studio** z menu Start systemu Windows. Upewnij się, że jest zaznaczone pole **Programowanie aplikacji klasycznych z C++**  kafelkiem, a następnie w sekcji składniki **opcjonalne** Sprawdź  **C++również pomoc techniczną/CLI**.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Poniższe kroki różnią się w zależności od używanej wersji programu Visual Studio. Upewnij się, że selektor wersji w lewym górnym rogu tej strony jest poprawnie ustawiony.

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>Aby utworzyć projekt C++/CLI w programie Visual Studio 2019

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy u góry, aby otworzyć okno dialogowe **Tworzenie nowego projektu** .

1. W górnej części okna dialogowego wpisz **CLR** w polu wyszukiwania, a następnie wybierz pozycję **CLR pusty projekt** z listy wyników.

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>Aby utworzyć projekt C++/CLI w programie Visual Studio 2017

1. Tworzenie nowego projektu. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

1. W oknie typy C++ projektu wizualizacji kliknij pozycję **CLR**, a następnie kliknij pozycję **pusty projekt środowiska CLR**.

1. Wpisz nazwę projektu. Domyślnie rozwiązanie, które zawiera projekt, ma taką samą nazwę jak nowy projekt, ale można wprowadzić inną nazwę. Jeśli chcesz, możesz wprowadzić inną lokalizację dla projektu.

1. Kliknij przycisk **OK** , aby utworzyć nowy projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>Aby utworzyć projekt C++/CLI w programie Visual Studio 2015

1. Tworzenie nowego projektu. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

1. W oknie typy C++ projektu wizualizacji kliknij pozycję **CLR**, a następnie kliknij pozycję **pusty projekt środowiska CLR**.

1. Wpisz nazwę projektu. Domyślnie rozwiązanie, które zawiera projekt, ma taką samą nazwę jak nowy projekt, ale można wprowadzić inną nazwę. Jeśli chcesz, możesz wprowadzić inną lokalizację dla projektu.

1. Kliknij przycisk **OK** , aby utworzyć nowy projekt.

::: moniker-end

## <a name="add-a-source-file"></a>Dodawanie pliku źródłowego

1. Jeśli **Eksplorator rozwiązań** nie jest widoczny, kliknij przycisk **Eksplorator rozwiązań** w menu **Widok** .

1. Dodaj nowy plik źródłowy do projektu:

   - Kliknij prawym przyciskiem myszy folder **pliki źródłowe** w **Eksplorator rozwiązań**, wskaż polecenie **Dodaj**i kliknij pozycję **nowy element**.

   - Kliknij pozycję  **C++ plik (. cpp)** i wpisz nazwę pliku, a następnie kliknij przycisk **Dodaj**.

   Plik **. cpp** zostanie wyświetlony w folderze **pliki źródłowe** w **Eksplorator rozwiązań** i zostanie wyświetlone okno z kartami, w którym można wpisać kod, który ma być w tym pliku.

1. Kliknij nowo utworzoną kartę w programie Visual Studio i wpisz prawidłowy program wizualny C++ lub skopiuj i wklej jeden z przykładowych programów.

   Na przykład możesz użyć programu przykładowego [: Napisz plik tekstowyC++(/CLI)](how-to-write-a-text-file-cpp-cli.md) (w węźle **Obsługa plików i we/wy** przewodnika programowania).

   W przypadku korzystania z przykładowego programu należy zauważyć, że użycie słowa kluczowego `gcnew` zamiast `new` podczas tworzenia obiektu .NET, a `gcnew` zwraca dojście (`^`), a nie wskaźnik (`*`):

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Aby uzyskać więcej informacji C++na temat składni/CLI, zobacz [rozszerzenia składników dla platform środowiska uruchomieniowego](../extensions/component-extensions-for-runtime-platforms.md).

1. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

   W oknie **dane wyjściowe** są wyświetlane informacje o postępie kompilacji, takie jak lokalizacja dziennika kompilacji i komunikat informujący o stanie kompilacji.

   Jeśli wprowadzisz zmiany i uruchomisz program bez wykonywania kompilacji, okno dialogowe może wskazywać, że projekt jest nieaktualny. Zaznacz pole wyboru w tym oknie dialogowym przed kliknięciem przycisku **OK** , jeśli chcesz, aby program Visual Studio zawsze używał bieżących wersji plików zamiast monitowania użytkownika za każdym razem, gdy kompiluje aplikację.

1. W menu **debugowanie** kliknij polecenie **Uruchom bez debugowania**.

1. Jeśli użyto przykładowego programu, podczas uruchamiania programu wyświetlane jest okno polecenia, które wskazuje, że plik tekstowy został utworzony.

   Plik tekstowy **textfile. txt** znajduje się teraz w katalogu projektu. Możesz otworzyć ten plik za pomocą Notatnika.

   > [!NOTE]
   > Wybór pustego szablonu projektu CLR powoduje automatyczne ustawienie opcji kompilatora `/clr`. Aby to sprawdzić, kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i kliknij polecenie **Właściwości**, a następnie sprawdź opcję **Obsługa środowiska uruchomieniowego** CLR **General** w węźle ogólne **Właściwości konfiguracji**.

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)<br/>
