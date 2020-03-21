---
title: 'Przewodnik: Tworzenie programu standardowego C++ (C++)'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 381fa347a4ca2872ef0697d76a1e788c97e8a014
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075437"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Przewodnik: Tworzenie programu standardowego C++ (C++)

Program Visual Studio umożliwia tworzenie standardowych C++ programów. Wykonując kroki opisane w tym instruktażu, można utworzyć projekt, dodać nowy plik do projektu, zmodyfikować plik, aby dodać C++ kod, a następnie skompilować i uruchomić program przy użyciu programu Visual Studio.

Możesz wpisać własny C++ program lub użyć jednego z przykładowych programów. Przykładowy program w tym instruktażu jest aplikacją konsolową. Ta aplikacja używa kontenera `set` w bibliotece C++ standardowej.

> [!NOTE]
> Jeśli jest wymagana zgodność z określoną wersją standardowego C++ języka (tj. c++ 14 lub c++ 17), użyj opcji kompilatora `/std:c++14` lub `/std:c++17`. (Program Visual Studio 2017 lub nowszy).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten instruktaż, musisz rozumieć podstawy języka C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>Aby utworzyć projekt i dodać plik źródłowy

Poniższe kroki różnią się w zależności od używanej wersji programu Visual Studio. Upewnij się, że selektor wersji w lewym górnym rogu tej strony jest poprawnie ustawiony.

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>Aby utworzyć C++ projekt w programie Visual Studio 2019

1. Z menu głównego wybierz kolejno pozycje **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Utwórz nowy projekt** .

1. W górnej części okna dialogowego Ustaw **Język** na **C++** , ustaw **platformę** na **system Windows**i ustaw **Typ projektu** na **Console**.

1. Z listy filtrowane typy projektów wybierz pozycję **Aplikacja konsolowa** , a następnie wybierz przycisk **dalej**. Na następnej stronie Wprowadź nazwę projektu i określ lokalizację projektu w razie potrzeby.

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>Aby utworzyć C++ projekt w programie Visual Studio 2017

1. Utwórz projekt, wskazując pozycję **Nowy** w menu **plik** , a następnie klikając pozycję **projekt**.

1. W okienku typy projektów  **C++ wizualizacji** kliknij pozycję **Windows Desktop**, a następnie kliknij pozycję **Aplikacja konsolowa systemu Windows**.

1. Wpisz nazwę dla projektu. Domyślnie rozwiązanie, które zawiera projekt, ma taką samą nazwę jak projekt, ale można wpisać inną nazwę. Możesz również wpisać inną lokalizację dla projektu.

1. Kliknij przycisk **OK**, aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>Aby utworzyć C++ projekt w programie Visual Studio 2015

1. Utwórz projekt, wskazując pozycję **Nowy** w menu **plik** , a następnie klikając pozycję **projekt**.

1. W okienku typy projektów  **C++ wizualizacji** kliknij pozycję **Windows Desktop**, a następnie kliknij pozycję **Aplikacja konsolowa systemu Windows**.

1. W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowane** > **Szablony** > **Wizualizacja C++** , a następnie wybierz opcję **Win32**. W środkowym okienku wybierz pozycję **aplikacja konsoli Win32**.

1. Wpisz nazwę dla projektu. Domyślnie rozwiązanie, które zawiera projekt, ma taką samą nazwę jak projekt, ale można wpisać inną nazwę. Możesz również wpisać inną lokalizację dla projektu.

1. Kliknij przycisk **OK**, aby utworzyć projekt.

1. Ukończ pracę **Kreatora aplikacji Win32**.

1. Kliknij przycisk **dalej**, upewnij się, że **Aplikacja konsolowa** jest zaznaczona i usuń zaznaczenie pola **prekompilowane nagłówki** .

1. Kliknij przycisk **Finish** (Zakończ).

::: moniker-end

## <a name="add-a-new-source-file"></a>Dodaj nowy plik źródłowy

1. Jeśli **Eksplorator rozwiązań** nie jest wyświetlany, w menu **widok** kliknij pozycję **Eksplorator rozwiązań**.

1. Dodaj nowy plik źródłowy do projektu w następujący sposób.

   1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder **pliki źródłowe** , wskaż polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**.

   1. W węźle **kod** kliknij  **C++ plik (. cpp)** , wpisz nazwę pliku, a następnie kliknij przycisk **Dodaj**.

   Plik. cpp zostanie wyświetlony w folderze **pliki źródłowe** w **Eksplorator rozwiązań**, a plik zostanie otwarty w edytorze programu Visual Studio.

1. W pliku w edytorze wpisz prawidłowy C++ program używający biblioteki C++ standardowej lub skopiuj jeden z przykładowych programów i wklej go w pliku.

1. Zapisz plik.

1. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

   W oknie **dane wyjściowe** są wyświetlane informacje o postępie kompilacji, na przykład lokalizacja dziennika kompilacji i komunikat informujący o stanie kompilacji.

1. W menu **debugowanie** kliknij polecenie **Uruchom bez debugowania**.

   Jeśli użyto przykładowego programu, wyświetlane jest okno poleceń i pokazuje, czy niektóre liczby całkowite znajdują się w zestawie.

## <a name="next-steps"></a>Następne kroki

**Poprzedni:** [aplikacje konsolowe w C++ wizualizacji](../windows/console-applications-in-visual-cpp.md)<br/>
**Dalej:** [Przewodnik: kompilowanie programu C++ natywnego w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
