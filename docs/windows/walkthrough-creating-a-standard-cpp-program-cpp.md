---
title: 'Przewodnik: tworzenie standardowego programu C++ (C++)'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: bf2a3fac92b756b395eda236ed4968608319823c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509605"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Przewodnik: tworzenie standardowego programu C++ (C++)

Program Visual Studio służy do tworzenia standardowych programów C++. Wykonując kroki opisane w tym instruktażu, można utworzyć projekt, dodać nowy plik do projektu, zmodyfikować plik w celu dodania kodu C++, a następnie skompilować i uruchomić program przy użyciu programu Visual Studio.

Możesz wpisać własny program w języku C++ lub użyć jednego z przykładowych programów. Przykładowy program w tym instruktażu jest aplikacją konsolową. Ta aplikacja używa `set` kontenera w standardowej bibliotece języka C++.

> [!NOTE]
> Jeśli jest wymagana zgodność z określoną wersją Standard języka C++ (tj. C++ 14 lub C++ 17), użyj `/std:c++14` `/std:c++17` opcji kompilatora lub. (Program Visual Studio 2017 lub nowszy).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten instruktaż, musisz rozumieć podstawy języka C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>Aby utworzyć projekt i dodać plik źródłowy

Poniższe kroki różnią się w zależności od używanej wersji programu Visual Studio. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj kontrolki selektora **wersji** . Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>Aby utworzyć projekt języka C++ w programie Visual Studio 2019

1. Z menu głównego wybierz pozycję **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Tworzenie nowego projektu** .

1. W górnej części okna dialogowego Ustaw  **Język** na **C++**, ustaw **platformę** na **Windows**i ustaw **Typ projektu** na **Console**.

1. Z listy filtrowane typy projektów wybierz pozycję **Aplikacja konsolowa** , a następnie wybierz przycisk **dalej**. Na następnej stronie Wprowadź nazwę projektu i określ lokalizację projektu w razie potrzeby.

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>Aby utworzyć projekt języka C++ w programie Visual Studio 2017

1. Utwórz projekt, wskazując pozycję **Nowy** w menu **plik** , a następnie klikając pozycję **projekt**.

1. W okienku **Visual C++** typy projektów kliknij pozycję **Windows Desktop**, a następnie kliknij pozycję **Aplikacja konsolowa systemu Windows**.

1. Wpisz nazwę dla projektu. Domyślnie rozwiązanie, które zawiera projekt, ma taką samą nazwę jak projekt, ale można wpisać inną nazwę. Możesz również wpisać inną lokalizację dla projektu.

1. Kliknij przycisk **OK**, aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>Aby utworzyć projekt języka C++ w programie Visual Studio 2015

1. Utwórz projekt, wskazując pozycję **Nowy** w menu **plik** , a następnie klikając pozycję **projekt**.

1. W okienku **Visual C++** typy projektów kliknij pozycję **Windows Desktop**, a następnie kliknij pozycję **Aplikacja konsolowa systemu Windows**.

1. W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowane**  >  **Szablony**  >  **Visual C++** a następnie wybierz opcję **Win32**. W środkowym okienku wybierz pozycję **aplikacja konsoli Win32**.

1. Wpisz nazwę dla projektu. Domyślnie rozwiązanie, które zawiera projekt, ma taką samą nazwę jak projekt, ale można wpisać inną nazwę. Możesz również wpisać inną lokalizację dla projektu.

1. Kliknij przycisk **OK**, aby utworzyć projekt.

1. Ukończ pracę **Kreatora aplikacji Win32**.

1. Kliknij przycisk **dalej**, upewnij się, że **Aplikacja konsolowa** jest zaznaczona i usuń zaznaczenie pola **prekompilowane nagłówki** .

1. Kliknij przycisk **Zakończ**.

::: moniker-end

## <a name="add-a-new-source-file"></a>Dodaj nowy plik źródłowy

1. Jeśli **Eksplorator rozwiązań** nie jest wyświetlany, w menu **widok** kliknij pozycję **Eksplorator rozwiązań**.

1. Dodaj nowy plik źródłowy do projektu w następujący sposób.

   1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder **pliki źródłowe** , wskaż polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**.

   1. W węźle **kod** kliknij **plik C++ (. cpp)**, wpisz nazwę pliku, a następnie kliknij przycisk **Dodaj**.

   Plik. cpp zostanie wyświetlony w folderze **pliki źródłowe** w **Eksplorator rozwiązań**, a plik zostanie otwarty w edytorze programu Visual Studio.

1. W pliku w edytorze wpisz prawidłowy program w języku C++, który używa standardowej biblioteki języka C++, lub skopiuj jeden z przykładowych programów i wklej go do pliku.

1. Zapisz plik.

1. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

   W oknie **dane wyjściowe** są wyświetlane informacje o postępie kompilacji, na przykład lokalizacja dziennika kompilacji i komunikat informujący o stanie kompilacji.

1. W menu **debugowanie** kliknij polecenie **Uruchom bez debugowania**.

   Jeśli użyto przykładowego programu, wyświetlane jest okno poleceń i pokazuje, czy niektóre liczby całkowite znajdują się w zestawie.

## <a name="next-steps"></a>Następne kroki

**Poprzednie:** [aplikacje konsolowe w Visual C++](./overview-of-windows-programming-in-cpp.md)<br/>
**Dalej:** [Przewodnik: kompilowanie natywnego programu C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka języka C++](../standard-library/cpp-standard-library-reference.md)
