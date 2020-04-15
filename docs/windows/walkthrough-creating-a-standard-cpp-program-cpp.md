---
title: 'Przewodnik: tworzenie standardowego programu C++ (C++)'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 105ac62131b45afdea2a445b5888a344f1e4d46c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370227"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Przewodnik: tworzenie standardowego programu C++ (C++)

Za pomocą programu Visual Studio można tworzyć standardowe programy języka C++. Wykonując kroki opisane w tym instruktażu, można utworzyć projekt, dodać nowy plik do projektu, zmodyfikować plik, aby dodać kod C++, a następnie skompilować i uruchomić program przy użyciu programu Visual Studio.

Możesz wpisać własny program C++ lub użyć jednego z przykładowych programów. Przykładowy program w tym instruktażu jest aplikacją konsoli. Ta aplikacja używa `set` kontenera w bibliotece standardowej języka C++.

> [!NOTE]
> Jeśli wymagana `/std:c++14` `/std:c++17` jest zgodność z określoną wersją standardu języka C++ (tj. (Visual Studio 2017 i nowsze).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten instruktaż, musisz rozumieć podstawy języka C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>Aby utworzyć projekt i dodać plik źródłowy

Poniższe kroki różnią się w zależności od używanej wersji programu Visual Studio. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj formantu selektor **wersji.** Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>Aby utworzyć projekt języka C++ w programie Visual Studio 2019

1. Z menu głównego wybierz polecenie **Plik** > **nowego** > **projektu,** aby otworzyć okno **dialogowe Tworzenie nowego projektu.**

1. W górnej części okna dialogowego ustaw **język** na **C++,** ustaw **platformę** na **Windows**i ustaw **typ projektu** na **Konsola**.

1. Z filtru listy typów projektów wybierz pozycję **Aplikacja konsoli,** a następnie wybierz pozycję **Dalej**. Na następnej stronie wprowadź nazwę projektu i określ lokalizację projektu w razie potrzeby.

1. Wybierz przycisk **Utwórz,** aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>Aby utworzyć projekt języka C++ w programie Visual Studio 2017

1. Utwórz projekt, wskazując polecenie **Nowy** w menu **Plik,** a następnie klikając polecenie **Projekt**.

1. W okienku Typy projektów **visual C++** kliknij pozycję **Pulpit systemu Windows**, a następnie kliknij pozycję Aplikacja konsoli **Windows**.

1. Wpisz nazwę projektu. Domyślnie rozwiązanie, które zawiera projekt ma taką samą nazwę jak projekt, ale można wpisać inną nazwę. Można również wpisać inną lokalizację dla projektu.

1. Kliknij przycisk **OK**, aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>Aby utworzyć projekt języka C++ w programie Visual Studio 2015

1. Utwórz projekt, wskazując polecenie **Nowy** w menu **Plik,** a następnie klikając polecenie **Projekt**.

1. W okienku Typy projektów **visual C++** kliknij pozycję **Pulpit systemu Windows**, a następnie kliknij pozycję Aplikacja konsoli **Windows**.

1. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Zainstalowane** > **szablony** > **Visual C++,** a następnie wybierz pozycję **Win32**. W środkowym okienku wybierz pozycję **Aplikacja konsoli Win32**.

1. Wpisz nazwę projektu. Domyślnie rozwiązanie, które zawiera projekt ma taką samą nazwę jak projekt, ale można wpisać inną nazwę. Można również wpisać inną lokalizację dla projektu.

1. Kliknij przycisk **OK**, aby utworzyć projekt.

1. Ukończ **Kreatora aplikacji Win32**.

1. Kliknij **przycisk Dalej**, a następnie upewnij się, że aplikacja **konsoli** jest zaznaczona i wyczyść pole wyboru **Wstępnie skompilowane nagłówki.**

1. Kliknij przycisk **Zakończ**.

::: moniker-end

## <a name="add-a-new-source-file"></a>Dodawanie nowego pliku źródłowego

1. Jeśli **Eksplorator rozwiązań** nie jest wyświetlany, w menu **Widok** kliknij polecenie **Eksplorator rozwiązań**.

1. Dodaj nowy plik źródłowy do projektu w następujący sposób.

   1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy folder **Pliki źródłowe,** wskaż polecenie **Dodaj**, a następnie kliknij polecenie **Nowy element**.

   1. W węźle **Kod** kliknij pozycję **Plik C++ (cpp)**, wpisz nazwę pliku, a następnie kliknij przycisk **Dodaj**.

   Plik cpp pojawi się w folderze **Pliki źródłowe** w **Eksploratorze rozwiązań,** a plik zostanie otwarty w edytorze Programu Visual Studio.

1. W pliku w edytorze wpisz prawidłowy program C++, który używa standardowej biblioteki języka C++ lub skopiuj jeden z przykładowych programów i wklej go do pliku.

1. Zapisz plik.

1. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

   Okno **Dane wyjściowe** wyświetla informacje o postępie kompilacji, na przykład lokalizację dziennika kompilacji i komunikat, który wskazuje stan kompilacji.

1. W menu **Debugowanie** kliknij przycisk **Start bez debugowania**.

   Jeśli użyto przykładowego programu, zostanie wyświetlone okno poleceń, w których zostanie wyświetlone określone liczby całkowite.

## <a name="next-steps"></a>Następne kroki

**Poprzedni:** [Aplikacje konsoli w języku Visual C++](../windows/console-applications-in-visual-cpp.md)<br/>
**Dalej:** [Instruktaż: Kompilowanie natywnego programu C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>Zobacz też

[Odwołanie do języka języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka języka C++](../standard-library/cpp-standard-library-reference.md)
