---
title: 'Wskazówki: Kompilowanie programu C w wierszu polecenia | Dokumentacja firmy Microsoft'
ms.custom: conceptual
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 033c29ff9871a427222b59fbf5c8350794a9bbe2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Wskazówki: Kompilowanie programu C w wierszu polecenia
Visual C++ obejmuje kompilatora C, który służy do tworzenia wszystko z programów podstawowe konsoli pełne aplikacje pulpitu systemu Windows, aplikacje mobilne i inne.  
  
 W tym przewodniku przedstawiono sposób tworzenia prostej "Hello, World" — styl C program przy użyciu tekstu Edytor i skompiluj go w wierszu polecenia. Czy raczej pracy w języku C++ w wierszu polecenia, zobacz [wskazówki: kompilowanie natywnego programu C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Jeśli chcesz spróbować programu Visual Studio IDE, a nie przy użyciu wiersza polecenia, zobacz [wskazówki: Praca z projektami i rozwiązaniami (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) lub [za pomocą środowiska IDE programu Visual Studio dla programowania w języku C++ pulpitu](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku, należy zainstalować program Visual Studio i opcjonalne składniki Visual C++ lub Microsoft Visual C++ kompilacji narzędzia.  
  
 Program Visual Studio jest wydajne zintegrowane środowisko projektowe obsługującego edytorze kompletne, menedżerowie zasobów, debugery i kompilatory dla wielu języków i platform. Aby uzyskać informacje o tych funkcjach i jak pobrać i zainstalować program Visual Studio, w tym bezpłatna wersja programu Visual Studio Community, zobacz [VisualStudio.com](https://www.visualstudio.com/).  
  
 Visual Studio Tools kompilacji instaluje tylko kompilatory w wierszu polecenia, narzędzia i biblioteki należy utworzyć programów C i C++. Doskonale w laboratoriach kompilacji lub klasą wykonuje i instaluje stosunkowo szybko. Aby zainstalować tylko narzędzia wiersza polecenia, Pobierz [programu Visual Studio Tools kompilacji](https://go.microsoft.com/fwlink/p/?linkid=840931) i uruchom Instalatora. Aby uzyskać więcej informacji, zobacz [Visual C++ Build Tools](http://landinghub.visualstudio.com/visual-cpp-build-tools).  
  
 Przed dokonaniem kompilacji programu C lub C++ w wierszu polecenia, należy sprawdzić, czy są zainstalowane narzędzia i czy użytkownik może uzyskiwać do nich dostęp z poziomu wiersza polecenia. Visual C++ ma złożonych wymagań dotyczących środowiska wiersza polecenia, aby odnaleźć narzędzia nagłówków i bibliotek, które są używane. **Nie można użyć programu Visual C++ w oknie wiersza polecenia zwykły**. Należy *wiersza polecenia dewelopera* okno jest oknem regularne wiersza polecenia, które zawiera wszystkie zmienne środowiskowe wymagane, ustaw. Na szczęście Visual C++ instaluje skróty należy uruchomić wiersz polecenia dewelopera mających środowiska dla kompilacji wiersza polecenia. Niestety nazwy skrótów wiersza polecenia dewelopera i gdzie znajdują się różnią się w praktycznie każdej wersji programu Visual C++ i w różnych wersjach systemu Windows. Jest pierwsze zadanie wskazówki można znaleźć prawo skrótu do użycia.  
  
> [!NOTE]
>  Skrót do wiersza polecenia dewelopera automatycznie ustawia prawidłowe ścieżki do narzędzi i kompilatora i wszystkie wymagane nagłówków i bibliotek. Niektóre z tych wartości są różne dla każdej konfiguracji kompilacji. Należy ustawić te wartości środowiska użytkownika, jeśli nie używasz skróty. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji wiersza polecenia](../build/setting-the-path-and-environment-variables-for-command-line-builds.md). Ponieważ środowisko kompilacji jest złożone, zaleca się, że można użyć zamiast tworzenia własnych skrótów wiersza polecenia dewelopera.  
  
## <a name="open-a-developer-command-prompt"></a>Otwórz okno wiersza polecenia dewelopera  
  
1.  Po zainstalowaniu programu Visual Studio 2017 w systemie Windows 10, otwórz Start menu, a następnie przewiń w dół a **programu Visual Studio 2017** folder (a nie aplikacji Visual Studio 2017). Wybierz **wiersz polecenia dla programu VS 2017 deweloperów** aby otworzyć okno wiersza polecenia.  
  
     Jeśli zainstalowano program Microsoft Visual C++ kompilacji narzędzia 2015 w systemie Windows 10, otwórz **Start** menu, a następnie przewiń w dół i Otwórz **Visual C++ Build Tools** folderu. Wybierz **wiersz polecenia narzędzi natywnego programu Visual C++ 2015 x86** aby otworzyć okno wiersza polecenia.  
  
     Jeśli używasz innej wersji programu Visual Studio lub innej wersji systemu Windows, Szukaj w Start menu lub uruchomić strony do folderu narzędzi Visual Studio, który zawiera skrót do wiersza polecenia dewelopera. Funkcja wyszukiwania systemu Windows umożliwia również wyszukiwanie "wiersz polecenia dla deweloperów" i wybierz, który odpowiada zainstalowanej wersji programu Visual Studio. Użyj skrótu, aby otworzyć okno wiersza polecenia.  
  
2.  Następnie sprawdź, czy wiersza polecenia dewelopera Visual C++ jest prawidłowo skonfigurowane. W oknie wiersza polecenia wprowadź `cl` i sprawdź, czy dane wyjściowe wygląda następująco:  
  
    ```Output  
    C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl  
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86  
    Copyright (C) Microsoft Corporation.  All rights reserved.  
    
    usage: cl [ option... ] filename... [ /link linkoption... ]  
    
    C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>  
    ```  
  
     Może to być różnic w bieżącym katalogu i numery wersji, w zależności od wersji programu Visual C++ i zainstalowane jakiekolwiek aktualizacje. Jeśli jest to podobne do zostanie wyświetlony, następnie można przystąpić do tworzenia programów C lub C++ w wierszu polecenia.  
  
    > [!NOTE]
    >  Jeśli zostanie wyświetlony błąd, takie jak "'cl' nie jest rozpoznawana jako polecenie wewnętrzne lub zewnętrzne, program wykonywalny lub plik wsadowy" Błąd C1034 lub błąd LNK1104 po uruchomieniu **cl** polecenia, a następnie albo nie używasz wiersz polecenia dewelopera lub Czasami występują problemy z instalacją programu Visual C++. Przed kontynuowaniem musisz naprawić ten problem.  
  
     Jeśli nie możesz znaleźć dewelopera skrót do wiersza polecenia lub jeśli zostanie wyświetlony komunikat o błędzie podczas wprowadzania `cl`, a następnie instalację programu Visual C++ może wystąpić problem. Spróbuj ponownie zainstalować składnik Visual C++ w programie Visual Studio, lub zainstaluj ponownie Visual Studio Tools kompilacji. Nie przejdź do następnej sekcji, dopóki działa to. Aby uzyskać więcej informacji o instalowaniu i rozwiązywanie problemów z języka Visual C++, zobacz [program Visual Studio](/visualstudio/install/install-visual-studio).  
  
    > [!NOTE]
    >  W zależności od wersji systemu Windows na komputerze oraz konfiguracji zabezpieczeń systemu, może być konieczne kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla deweloperów skrót do wiersza polecenia, a następnie wybierz pozycję **Uruchom jako Administrator** do pomyślnie skompilować i uruchomić program, który utworzonych za pomocą tego przewodnika.  
  
## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Tworzenie źródłowego pliku C i skompiluj go w wierszu polecenia  
  
1.  W oknie wiersza polecenia dewelopera wprowadź **cd c:\\**  można zmienić bieżący katalog roboczy na katalog główny dysku C:. Następnie wprowadź **md c:\simple** do tworzenia katalogu, a następnie wprowadź **cd c:\simple** zmiany do tego katalogu. To jest katalog, który będzie zawierać pliku źródłowego i skompilowany program.  
  
2.  Wprowadź **simple.c Notatnik** w wierszu polecenia dewelopera. W Notatniku alertu oknie wyskakującym, wybierz **tak** do utworzenia nowego pliku simple.c w katalogu roboczym.  
  
3.  W programie Notatnik wprowadź następujące wiersze kodu:  
  
    ```C  
    #include <stdio.h>  
  
    int main()  
    {  
        printf("Hello, World! This is a native C program compiled on the command line.\n");  
        return 0;  
    }   
    ```  
  
4.  Na pasku menu programu Notatnik wybierz **pliku**, **zapisać** zapisać simple.c w katalogu roboczym.  
  
5.  Przejdź do okna wiersza polecenia dewelopera. Wprowadź **dir** w wierszu polecenia, aby wyświetlić zawartość katalogu c:\simple. Powinny pojawić się simple.c pliku źródłowego w liście zawartości katalogu, który wygląda następująco:  
  
    ```Output  
    C:\simple>dir  
     Volume in drive C has no label.  
     Volume Serial Number is CC62-6545  
  
     Directory of C:\simple  
  
    10/02/2017  03:46 PM    <DIR>          .  
    10/02/2017  03:46 PM    <DIR>          ..  
    10/02/2017  03:36 PM               143 simple.c  
                   1 File(s)            143 bytes  
                   2 Dir(s)  514,900,566,016 bytes free  
  
    ```  
  
     Daty i inne szczegóły różnią się na komputerze. Jeśli nie widzisz pliku kodu źródłowego, simple.c, upewnij się, że zostały zmienione, aby nowo utworzony katalog c:\simple i w programie Notatnik, upewnij się, zapisać pliku źródłowego w tym katalogu. Upewnij się również kod źródłowy został zapisany z rozszerzeniem nazwy pliku .c, nie rozszerzenia .txt.  
  
6.  Aby skompilować programu, wprowadź **cl simple.c** w wierszu polecenia dewelopera.  
  
     Można wyświetlić nazwę programu wykonywalnego simple.exe w wierszach kompilator wyświetlane informacje danych wyjściowych:  
  
    ```Output  
    c:\simple>cl simple.c  
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86  
    Copyright (C) Microsoft Corporation.  All rights reserved.  
  
    simple.c  
    Microsoft (R) Incremental Linker Version 14.10.25017.0  
    Copyright (C) Microsoft Corporation.  All rights reserved.  
  
    /out:simple.exe  
    simple.obj  
    ```  
  
    > [!NOTE]
    >  Jeśli zostanie wyświetlony błąd, takie jak "'cl' nie jest rozpoznawana jako polecenie wewnętrzne lub zewnętrzne, program wykonywalny lub plik wsadowy" Błąd C1034 lub błąd LNK1104, wiersza polecenia dewelopera jest nieprawidłowo skonfigurowane. Aby uzyskać informacje na temat rozwiązać ten problem, przejdź wstecz do **Otwórz okno wiersza polecenia dewelopera** sekcji.  
  
    > [!NOTE]
    >  Jeśli inny kompilatora lub konsolidatora błąd lub ostrzeżenie, przejrzeć kod źródłowy poprawić błędy, zapisać go i ponownie uruchom kompilatora. Aby uzyskać informacje o określonych błędach Użyj pola wyszukiwania na tej stronie MSDN szukać numer błędu.  
  
7.  Aby uruchomić program, należy wprowadzić **proste** w wierszu polecenia.  
  
     Program wyświetla ten tekst, a następnie kończy działanie:  
  
    ```Output  
    Hello, World! This is a native C program compiled on the command line.  
    ```  
  
     Gratulacje, zostały tylko skompilować i uruchomić C program za pomocą wiersza polecenia.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przykładzie "Hello, World" jest około tak proste, jak pobrać C program. Rzeczywistych programy posiadają pliki nagłówka i więcej plików źródłowych, łącze w bibliotekach i przydatne pracę.  
  
 Kroki opisane w tym przewodniku służy do tworzenia własnego kodu C zamiast wpisywać kod przykładowych pokazano. Można również tworzyć wiele C kod przykładowy programy, które można znaleźć w innym miejscu. Aby skompilować program, który ma wiele plików kodu źródłowego, wprowadź je w wierszu polecenia następujący:  
  
 `cl file1.c file2.c file3.c`  
  
 Kompilator generuje program o nazwie file1.exe. Aby zmienić nazwę program1.exe, Dodaj [/out](../build/reference/out-output-file-name.md) — opcja konsolidatora:  
  
 `cl file1.c file2.c file3.c /link /out:program1.exe`  
  
 I aby wykryć automatycznie więcej błędów programowania, zaleca się skompilować przy użyciu [/W3](../build/reference/compiler-option-warning-level.md) lub [/W4](../build/reference/compiler-option-warning-level.md) ostrzeżenie opcję poziomu:  
  
 `cl /W4 file1.c file2.c file3.c /link /out:program1.exe`  
  
 Kompilator, cl.exe, ma wiele więcej opcji dotyczą kompilacji, optymalizacja, debugowania i analizowania kodu. Lista szybki, wprowadź **cl /?** w wierszu polecenia dewelopera. Można również skompilować i połączyć oddzielnie i zastosować opcje konsolidatora w bardziej złożonych scenariuszach kompilacji. Aby uzyskać więcej informacji na kompilatora i opcje konsolidatora i użycia, zobacz [odwołanie kompilacji C/C++](../build/reference/c-cpp-building-reference.md).  
  
 NMAKE i pliki reguł programu make lub MSBuild i pliki projektu można użyć do konfigurowania i kompilacji projektów bardziej złożone w wierszu polecenia. Aby uzyskać więcej informacji na temat używania tych narzędzi, zobacz [odwołanie NMAKE](../build/nmake-reference.md) i [MSBuild](../build/msbuild-visual-cpp.md).  
  
 Języki C i C++ są podobne, ale nie sam. Kompilator Visual C++ używa Prosta reguła, aby określić język, który będzie używany podczas kompiluje kod. Domyślnie kompilatora Visual C++ traktuje wszystkie pliki, które kończą się .c jako kodu źródłowego C i wszystkich plików, które kończą się .cpp jako kodu źródłowego języka C++. Aby wymusić kompilatorowi na traktowanie wszystkich plików c niezależnie od rozszerzenia nazwy pliku, użyj [/TC](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) — opcja kompilatora.  
  
 Kompilator Visual C++ C jest zazwyczaj zgodne ze standardem ISO C99, ale nie jest ściśle zgodna. W większości przypadków przenośne kod w języku C skompilować i uruchomić zgodnie z oczekiwaniami. Visual C++ nie obsługuje większość zmian w ISO C11. Niektóre funkcje bibliotek i nazwy funkcji POSIX są używane przez kompilator języka Visual C++. Funkcje są obsługiwane, ale preferowaną nazwy zostały zmienione. Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md) i [C4996 ostrzeżenie kompilatora (poziom 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie standardowego programu C++ (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)   
 [Dokumentacja języka C](../c-language/c-language-reference.md)   
 [Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)   
 [Zgodność](../c-runtime-library/compatibility.md)