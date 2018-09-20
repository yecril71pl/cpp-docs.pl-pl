---
title: Kompilowanie programu C++ przeznaczonego dla CLR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18e9b0c4e23516e763d8dab532e9862cad0177df
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416035"
---
# <a name="walkthrough-compiling-a-c-program-that-targets-the-clr-in-visual-studio"></a>Wskazówki: kompilowanie programu C++ przeznaczonego dla CLR w Visual Studio

Można tworzyć programy Visual C++, które używają klas .NET i skompilować je przy użyciu środowiska programistycznego Visual Studio.

Do wykonania tej procedury możesz wpisać swój własny program Visual C++ lub użyć jednego z przykładowych programów. Przykładowy program używanego w tej procedurze tworzy plik tekstowy o nazwie textfile.txt i zapisuje go do katalogu projektu.

## <a name="prerequisites"></a>Wymagania wstępne

Te tematy założono, że rozumiesz podstawy języka C++.

### <a name="to-create-a-new-project-in-visual-studio-and-add-a-new-source-file"></a>Aby utworzyć nowy projekt w programie Visual Studio i Dodaj nowy plik źródłowy

1. Utwórz nowy projekt. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.

1. Typy projektów Visual C++, kliknij **CLR**, a następnie kliknij przycisk **pusty projekt CLR**.

1. Wpisz nazwę projektu.

   Domyślnie rozwiązanie, zawierający projekt ma taką samą nazwę jak nowy projekt, ale można wprowadzić inną nazwę. Jeśli chcesz, możesz wprowadzić inną lokalizację dla projektu.

   Kliknij przycisk **OK** Aby utworzyć nowy projekt.

1. Jeśli w Eksploratorze rozwiązań nie jest widoczny, kliknij przycisk **Eksploratora rozwiązań** na **widoku** menu.

1. Dodaj nowy plik źródłowy do projektu:

   - Kliknij prawym przyciskiem myszy **pliki źródłowe** folder w Eksploratorze rozwiązań, wskaż polecenie **Dodaj** i kliknij przycisk **nowy element**.

   - Kliknij przycisk **plik C++ (.cpp)** i wpisz nazwę pliku, a następnie kliknij przycisk **Dodaj**.

   **.Cpp** plik pojawia się w **pliki źródłowe** folder w Eksploratorze rozwiązań i okien z zakładkami, pojawi się miejscem, gdzie wpisujesz kod ma w tym pliku.

1. Kliknij nowo utworzoną karcie w programie Visual Studio i wpisz prawidłowy program Visual C++ lub skopiuj i Wklej jeden z przykładowych programów.

   Na przykład, można użyć [porady: wpisywanie tekstu do pliku (C + +/ interfejsu wiersza polecenia)](../dotnet/how-to-write-a-text-file-cpp-cli.md) przykładowy program (w **Obsługa plików i we/wy** węzła Programming Guide).

   Jeśli korzystasz z przykładowego program, zwróć uwagę, że używasz `gcnew` słowa kluczowego zamiast `new` podczas tworzenia obiektu platformy .NET, a `gcnew` zwraca uchwyt (`^`) zamiast wskaźnik (`*`):

     `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Aby uzyskać więcej informacji na temat nowej składni języka Visual C++, zobacz [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md).

1. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

   **Dane wyjściowe** okna wyświetla informacje o postępie kompilacji, takie jak lokalizacja dziennika kompilacji i komunikat o statusie kompilacji.

   Jeśli wprowadzono zmiany i uruchom program bez wykonania tej operacji kompilacji, okno dialogowe może oznaczać, że projekt jest nieaktualny. Zaznacz pole wyboru, w tym oknie dialogowym, zanim klikniesz pozycję **OK** Jeśli chcesz, aby Visual Studio, aby zawsze używać bieżącej wersji plików, zamiast monitowania użytkownika za każdym razem, tworzy on aplikacji.

1. Na **debugowania** menu, kliknij przycisk **Uruchom bez debugowania**.

9. Jeśli użyto przykładowego programu, po uruchomieniu program zostanie wyświetlone okno polecenia, który wskazuje, że utworzono plik tekstowy. Naciśnij dowolny klawisz, aby zamknąć okno polecenia.

   **Textfile.txt** plik tekstowy znajduje się teraz w katalogu projektu. Możesz otworzyć ten plik za pomocą Notatnika.

   > [!NOTE]
   >  Wybieranie CLR pusty szablon projektu automatycznie ustawiony **/CLR** — opcja kompilatora. Aby to sprawdzić, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i klikając **właściwości**, a następnie sprawdź, **Obsługa środowiska uruchomieniowego języka wspólnego** opcji  **Ogólne** węźle **właściwości konfiguracji**.

## <a name="whats-next"></a>Jaka jest przyszłość

**Poprzedni:** [wskazówki: kompilowanie natywnego programu C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md) &#124; **dalej:**[wskazówki: kompilowanie programu C w wierszu polecenia](../build/walkthrough-compile-a-c-program-on-the-command-line.md)

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br>
[Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)