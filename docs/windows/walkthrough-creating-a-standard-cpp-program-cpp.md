---
title: 'Wskazówki: Tworzenie standardowego programu C++ (C++)'
ms.custom: get-started-article
ms.date: 09/18/2018
f1_keywords:
- vcfirstapp
- vccreatefirst
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 78d19a277f8bedcdbd098a662c69d6fc622a7cff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647476"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Wskazówki: Tworzenie standardowego programu C++ (C++)

Aby tworzyć programy standardowego C++, można użyć Visual C++ w programie Visual Studio zintegrowane środowisko programistyczne (IDE). Wykonując kroki opisane w tym instruktażu, można utworzyć projektu, Dodaj nowy plik do projektu, zmodyfikuj plik, aby dodać kod języka C++, a następnie skompilować i uruchomić program za pomocą programu Visual Studio.

Można wpisać swój własny program C++ lub użyć jednego z przykładowych programów. Przykładowy program w tym instruktażu jest aplikacją konsoli. Ta aplikacja używa `set` kontenera w standardowej biblioteki języka C++.

Visual C++ następuje standardem C++ 2003, z tymi wyjątkami: dwuetapowego odnośnik do nazwy, specyfikacja wyjątku i eksport. Ponadto Visual C++ obsługuje kilka C ++ 0 x funkcji, na przykład wyrażenia lambda, auto, static_assert, odwołania rvalue i szablony extern.

> [!NOTE]
> Jeśli wymagana jest zgodność ze standardem, użyj `/Za` opcję kompilatora, aby wyłączyć rozszerzenia Microsoft do standardu. Aby uzyskać więcej informacji, zobacz [/za, /Ze (Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten instruktaż, musisz rozumieć podstawy języka C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>Aby utworzyć projekt i dodać plik źródłowy

1. Utwórz projektu wskazując **New** na **pliku** menu, a następnie klikając polecenie **projektu**.

1. W **Visual C++** okienku typów projektu, kliknij przycisk **pulpitu Windows**, a następnie kliknij przycisk **aplikacji konsoli Windows**.

   > [!NOTE]
   > W przypadku wersji sprzed 2017, Visual Studio w **nowy projekt** okna dialogowego rozwiń **zainstalowane** > **szablony**  >  **Visual C++**, a następnie wybierz pozycję **Win32**. W środkowym okienku wybierz **Aplikacja konsoli Win32**.

   Wpisz nazwę dla projektu.

   Domyślnie rozwiązanie, zawierający projekt ma taką samą nazwę jak projektu, ale można wpisać inną nazwę. Możesz również wpisać inną lokalizację dla projektu.

   Kliknij przycisk **OK** do tworzenia projektu.

   > [!NOTE]
   > W przypadku wersji sprzed 2017 Visual Studio, należy wykonać **Kreatora aplikacji Win32**. Kliknij przycisk **dalej**, upewnij się, **aplikację Konsolową** jest zaznaczone, a następnie usuń zaznaczenie pola wyboru **prekompilowanych nagłówków** pole. Kliknij przycisk **Zakończ**.

1. Jeśli **Eksploratora rozwiązań** nie jest wyświetlana na **widoku** menu, kliknij przycisk **Eksploratora rozwiązań**.

1. Dodaj nowy plik źródłowy do projektu, w następujący sposób.

   1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pliki źródłowe** folderu, wskaż **Dodaj**, a następnie kliknij przycisk **nowy element**.

   1. W **kodu** węzła, kliknij przycisk **plik C++ (.cpp)**, wpisz nazwę pliku, a następnie kliknij **Dodaj**.

   Plik CPP pojawia się w **pliki źródłowe** folderu w **Solution Explorer**, a plik jest otwarty w edytorze programu Visual Studio.

1. W pliku w edytorze wpisz prawidłowy program w języku C++, który używa standardowej biblioteki C++ lub skopiuj jeden z przykładowych programów i wklej go w pliku.

1. Zapisz plik.

1. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

   **Dane wyjściowe** okna wyświetla informacje o postępie kompilacji, na przykład lokalizacja dziennika kompilacji i komunikat o statusie kompilacji.

1. Na **debugowania** menu, kliknij przycisk **Uruchom bez debugowania**.

   Jeśli użyto przykładowego programu, okno polecenia jest wyświetlane i pokazuje, czy niektóre liczby całkowite znajdują się w zestawie.

## <a name="next-steps"></a>Następne kroki

**Poprzedni:** [konsoli aplikacji w języku Visual C++](../windows/console-applications-in-visual-cpp.md)<br/>
**Następnie:** [wskazówki: kompilowanie natywnego programu C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)<br/>
