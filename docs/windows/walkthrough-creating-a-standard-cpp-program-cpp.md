---
title: 'Przewodnik: Tworzenie standardowego programu C++ (C++)'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: b3172dd6ed4c438bacedd6760da5ab65228396f3
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400906"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Przewodnik: Tworzenie standardowego programu C++ (C++)

Visual Studio umożliwia tworzenie standardowego C++ programów. Wykonując kroki opisane w tym instruktażu, można utworzyć projektu, Dodaj nowy plik do projektu, zmodyfikuj plik, aby dodać kod języka C++, a następnie skompilować i uruchomić program za pomocą programu Visual Studio.

Można wpisać swój własny program C++ lub użyć jednego z przykładowych programów. Przykładowy program w tym instruktażu jest aplikacją konsoli. Ta aplikacja używa `set` kontenera w standardowej biblioteki języka C++.

> [!NOTE]
> Jeśli zgodność z określoną wersję C++ wymagane jest podanie języka standard (czyli C ++ 14 i C ++ 17), należy użyć `/std:C++14` lub `/std:c++17` — opcja kompilatora. (Visual Studio 2017 i nowsze.)

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten instruktaż, musisz rozumieć podstawy języka C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>Aby utworzyć projekt i dodać plik źródłowy

Poniższe kroki różnią się w zależności od tego, która wersja programu Visual Studio, którego używasz. Upewnij się, że selektor wersji, w lewym górnym rogu tej strony została prawidłowo ustawiona.

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>Aby utworzyć C++ projekt w programie Visual Studio 2019 r.

1. W menu głównym wybierz **pliku** > **New** > **projektu** otworzyć **Utwórz nowy projekt** okna dialogowego pole.

1. W górnej części okna dialogowego, ustaw **języka** do **C++** ustaw **platformy** do **Windows**i ustaw **Typprojektu** do **konsoli**. 

1. Wybierz z listy filtrowanej typów projektów, **aplikacja Konsolowa** wybierz **dalej**. Na następnej stronie podaj nazwę dla projektu, a następnie określ lokalizację projektu, w razie potrzeby.

1. Wybierz **Utwórz** przycisk, aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>Aby utworzyć C++ projektu w programie Visual Studio 2017

1. Utwórz projektu wskazując **New** na **pliku** menu, a następnie klikając polecenie **projektu**.

1. W **Visual C++** okienku typów projektu, kliknij przycisk **pulpitu Windows**, a następnie kliknij przycisk **aplikacji konsoli Windows**.

1. Wpisz nazwę dla projektu. Domyślnie rozwiązanie, zawierający projekt ma taką samą nazwę jak projektu, ale można wpisać inną nazwę. Możesz również wpisać inną lokalizację dla projektu.

1. Kliknij przycisk **OK** do tworzenia projektu.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>Aby utworzyć C++ projektu w programie Visual Studio 2015

1. Utwórz projektu wskazując **New** na **pliku** menu, a następnie klikając polecenie **projektu**.

1. W **Visual C++** okienku typów projektu, kliknij przycisk **pulpitu Windows**, a następnie kliknij przycisk **aplikacji konsoli Windows**.

1. W **nowy projekt** okna dialogowego rozwiń **zainstalowane** > **szablony** > **Visual C++** , i następnie wybierz pozycję **Win32**. W środkowym okienku wybierz **Aplikacja konsoli Win32**.

1. Wpisz nazwę dla projektu. Domyślnie rozwiązanie, zawierający projekt ma taką samą nazwę jak projektu, ale można wpisać inną nazwę. Możesz również wpisać inną lokalizację dla projektu.

1. Kliknij przycisk **OK** do tworzenia projektu.

1. Wykonaj **Kreatora aplikacji Win32**. 

1. Kliknij przycisk **dalej**, upewnij się, **aplikację Konsolową** jest zaznaczone, a następnie usuń zaznaczenie pola wyboru **prekompilowanych nagłówków** pole. 

1. Kliknij przycisk **Zakończ**.

::: moniker-end

## <a name="add-a-new-source-file"></a>Dodaj nowy plik źródłowy

1. Jeśli **Eksploratora rozwiązań** nie jest wyświetlana na **widoku** menu, kliknij przycisk **Eksploratora rozwiązań**.

1. Dodaj nowy plik źródłowy do projektu, w następujący sposób.

   1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pliki źródłowe** folderu, wskaż **Dodaj**, a następnie kliknij przycisk **nowy element**.

   1. W **kodu** węzła, kliknij przycisk **plik C++ (.cpp)** , wpisz nazwę pliku, a następnie kliknij **Dodaj**.

   Plik CPP pojawia się w **pliki źródłowe** folderu w **Solution Explorer**, a plik jest otwarty w edytorze programu Visual Studio.

1. W pliku w edytorze wpisz prawidłowy program w języku C++, który używa standardowej biblioteki C++ lub skopiuj jeden z przykładowych programów i wklej go w pliku.

1. Zapisz plik.

1. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

   **Dane wyjściowe** okna wyświetla informacje o postępie kompilacji, na przykład lokalizacja dziennika kompilacji i komunikat o statusie kompilacji.

1. Na **debugowania** menu, kliknij przycisk **Uruchom bez debugowania**.

   Jeśli użyto przykładowego programu, okno polecenia jest wyświetlane i pokazuje, czy niektóre liczby całkowite znajdują się w zestawie.

## <a name="next-steps"></a>Następne kroki

**Poprzednie:** [Aplikacje konsoli w programie Visual C++](../windows/console-applications-in-visual-cpp.md)<br/>
**Dalej:** [Przewodnik: kompilowanie natywnego programu C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
