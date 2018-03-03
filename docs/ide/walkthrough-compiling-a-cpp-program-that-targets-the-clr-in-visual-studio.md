---
title: Kompilowanie programu C++ przeznaczonego dla CLR | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eca6960d23c43fbe27d753ab4f79a27dea7bd7e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-compiling-a-c-program-that-targets-the-clr-in-visual-studio"></a>Wskazówki: kompilowanie programu C++ przeznaczonego dla CLR w Visual Studio
Można utworzyć programy Visual C++, które używać klas .NET i kompilowania ich przy użyciu środowiska programowania Visual Studio.  
  
 Do wykonania tej procedury można wpisać programu Visual C++, lub użyj jednego z programów przykładowych. Przykładowy program używanego w tej procedurze tworzy plik tekstowy o nazwie textfile.txt i zapisuje go w katalogu projektu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Tych tematach przyjęto założenie, że rozumiesz podstawowe informacje na temat języka C++.  
  
### <a name="to-create-a-new-project-in-visual-studio-and-add-a-new-source-file"></a>Utwórz nowy projekt w programie Visual Studio i Dodaj nowy plik źródłowy  
  
1.  Utwórz nowy projekt. Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
2.  Typy projektów Visual C++, kliknij **CLR**, a następnie kliknij przycisk **CLR pusty projekt**.  
  
3.  Wpisz nazwę projektu.  
  
     Domyślnie rozwiązanie, które zawiera projekt ma taką samą nazwę jak nowy projekt, ale można wprowadzić inną nazwę. Jeśli chcesz, możesz wprowadzić inną lokalizację dla projektu.  
  
     Kliknij przycisk **OK** do utworzenia nowego projektu.  
  
4.  Jeśli w Eksploratorze rozwiązań nie jest widoczny, kliknij przycisk **Eksploratora rozwiązań** na **widoku** menu.  
  
5.  Dodaj nowy plik źródłowy do projektu:  
  
    -   Kliknij prawym przyciskiem myszy **pliki źródłowe** folder w Eksploratorze rozwiązań, wskaż pozycję **Dodaj** i kliknij przycisk **nowy element**.  
  
    -   Kliknij przycisk **plik C++ (.cpp)** i wpisz nazwę pliku, a następnie kliknij przycisk **Dodaj**.  
  
     **.Cpp** plik zostanie wyświetlony w **pliki źródłowe** folder w Eksploratorze rozwiązań i okno z kartami pojawia się, należy wpisać kod ma w tym pliku.  
  
6.  Kliknij na karcie nowo utworzony w programie Visual Studio wpisz prawidłowy program Visual C++ lub kopiowanie i wklejanie jednego z programów próbki.  
  
     Na przykład można użyć [porady: wpisywanie tekstu do pliku (C + +/ CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md) przykładowy program (w **Obsługa plików i we/wy** węzła przewodnik programowania w języku).  
  
     Użycie przykładowego programu, zwróć uwagę, że używasz `gcnew` słowa kluczowego zamiast `new` podczas tworzenia obiektu .NET, a `gcnew` zwraca uchwyt (`^`) zamiast wskaźnik (`*`):  
  
     `StreamWriter^ sw = gcnew StreamWriter(fileName);`  
  
     Aby uzyskać więcej informacji o nowej składni Visual C++, zobacz [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md).  
  
7.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     **Dane wyjściowe** okno wyświetla informacje o postępie kompilacji, takie jak lokalizacja dziennika kompilacji i komunikat, który wskazuje stan kompilacji.  
  
     Jeśli wprowadzono zmiany i uruchom program bez wykonania tej kompilacji, okno dialogowe może wskazywać, że projekt jest nieaktualny. Zaznacz pole wyboru w tym oknie dialogowym, przed kliknięciem przycisku **OK** Jeśli chcesz Visual Studio, aby zawsze używać bieżącej wersji plików zamiast pytania użytkownika za każdym razem tworzenia aplikacji.  
  
8.  Na **debugowania** menu, kliknij przycisk **uruchomić bez debugowania**.  
  
9. Jeśli program próbki są używane po uruchomieniu programu jest wyświetlane okno poleceń, który wskazuje, że utworzono plik tekstowy. Naciśnij dowolny klawisz, aby zamknąć okno polecenia.  
  
     **Textfile.txt** pliku tekstowego znajduje się teraz w katalogu projektu. Ten plik można otworzyć za pomocą Notatnika.  
  
    > [!NOTE]
    >  Wybieranie CLR pusty szablon projektu automatycznie ustawione **/CLR** — opcja kompilatora. Aby to sprawdzić, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i klikając **właściwości**, a następnie sprawdź **Obsługa środowisko uruchomieniowe języka wspólnego** opcji w  **Ogólne** węzła **właściwości konfiguracji**.  
  
## <a name="whats-next"></a>Co to jest dalej  
 **Poprzedni:** [wskazówki: kompilowanie natywnego programu C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md) &#124; **Dalej:**[wskazówki: kompilowanie programu C w wierszu polecenia](../build/walkthrough-compile-a-c-program-on-the-command-line.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)