---
title: 'Wskazówki: Kompilowanie natywnego programu C++ w wierszu polecenia | Dokumentacja firmy Microsoft'
ms.custom: conceptual
ms.date: 06/08/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3fd65dff0a354ebbed4435b8867271091211279d
ms.sourcegitcommit: 1c2e035f98fb55d9b3c08ec3bb562179a368d0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35253834"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Wskazówki: kompilowanie natywnego programu C++ na wiersz polecenia
Visual C++ obejmuje wiersza polecenia kompilatora C++, którego można używać do tworzenia wszystko z aplikacji konsoli podstawowe do aplikacji platformy uniwersalnej systemu Windows, aplikacje komputerowe, sterowników urządzeń i składniki platformy .NET.  
  
 W tym przewodniku, Utwórz basic, "tekst Hello, World" — styl programu C++ przy użyciu tekstu Edytor i skompiluj go w wierszu polecenia. Jeśli chcesz spróbować programu Visual Studio IDE, a nie przy użyciu wiersza polecenia, zobacz [wskazówki: Praca z projektami i rozwiązaniami (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) lub [za pomocą środowiska IDE programu Visual Studio dla programowania w języku C++ pulpitu](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
 W ramach tego przewodnika można użyć programu Visual C++, zamiast wpisując ten, który jest wyświetlany, lub skorzystać z próbki kodu Visual C++ z innego artykułu pomocy.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku, należy zainstalować program Visual Studio i opcjonalne tworzenia klasycznych aplikacji z C++ obciążenia lub kompilacji narzędzia wiersza polecenia dla programu Visual Studio.  
  
 Program Visual Studio jest wydajne zintegrowane środowisko projektowe (IDE) obsługującego edytorze kompletne, menedżerowie zasobów, debugery i kompilatory dla wielu języków i platform. Aby uzyskać informacje na temat, aby pobrać i zainstalować program Visual Studio, w tym bezpłatna wersja programu Visual Studio Community i obejmują obsługę programowania w języku C/C++, zobacz [zainstalować obsługi języka C++ w programie Visual Studio](../build/vscpp-step-0-installation.md).  
  
 Narzędzia kompilacji dla programu Visual Studio instaluje tylko kompilatory w wierszu polecenia, narzędzia i biblioteki należy utworzyć programów C i C++. Doskonale w laboratoriach kompilacji lub klasą wykonuje i instaluje stosunkowo szybko. Aby zainstalować tylko narzędzia wiersza polecenia, Pobierz [Build Tools dla programu Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=840931).  
  
 Przed dokonaniem kompilacji programu C lub C++ w wierszu polecenia, należy sprawdzić, czy są zainstalowane narzędzia i czy użytkownik może uzyskiwać do nich dostęp z poziomu wiersza polecenia. Visual C++ ma złożonych wymagań dotyczących środowiska wiersza polecenia, aby odnaleźć narzędzia nagłówków i bibliotek, które są używane. **Nie można użyć programu Visual C++ w oknie wiersza polecenia zwykły** nie robiąc pewne przygotowania. Na szczęście Visual C++ instaluje skróty klawiaturowe do uruchamiania wiersza polecenia dewelopera ma środowisko dla kompilacji wiersza polecenia. Niestety nazwy skrótów wiersza polecenia dewelopera i gdzie znajdują się różnią się w praktycznie każdej wersji programu Visual C++ i w różnych wersjach systemu Windows. Pierwsze zadanie wskazówki jest znajdowania właściwy do użycia.  
  
> [!NOTE]
>  Skrót do wiersza polecenia dewelopera automatycznie ustawia prawidłowe ścieżki do narzędzi i kompilatora i wszystkie wymagane nagłówków i bibliotek. Należy ustawić te wartości środowiska samodzielnie użycie regularne okno wiersza polecenia. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji wiersza polecenia](../build/setting-the-path-and-environment-variables-for-command-line-builds.md). Firma Microsoft zaleca się, że można użyć zamiast tworzenia własnych skrótów wiersza polecenia dewelopera.  
  
### <a name="open-a-developer-command-prompt"></a>Otwórz okno wiersza polecenia dewelopera  
  
1.  Po zainstalowaniu programu Visual Studio 2017 w systemie Windows 10, otwórz Start menu i wybierz polecenie **wszystkie aplikacje**. Przewiń w dół i Otwórz **programu Visual Studio 2017** folder (a nie aplikacji Visual Studio 2017). Wybierz **wiersz polecenia dla programu VS 2017 deweloperów** aby otworzyć okno wiersza polecenia.  
  
     Jeśli zainstalowano program Microsoft Visual C++ kompilacji narzędzia 2015 w systemie Windows 10, otwórz **Start** menu i wybierz polecenie **wszystkie aplikacje**. Przewiń w dół i Otwórz **Visual C++ Build Tools** folderu. Wybierz **wiersz polecenia narzędzi natywnego programu Visual C++ 2015 x86** aby otworzyć okno wiersza polecenia.  
  
     Jeśli używasz innej wersji programu Visual Studio lub innej wersji systemu Windows, Szukaj w Start menu lub uruchomić strony do folderu narzędzi Visual Studio, który zawiera skrót do wiersza polecenia dewelopera. Funkcja wyszukiwania systemu Windows umożliwia również wyszukiwanie "wiersz polecenia dla deweloperów" i wybierz, który odpowiada zainstalowanej wersji programu Visual Studio. Użyj skrótu, aby otworzyć okno wiersza polecenia.  
  
2.  Następnie sprawdź, czy wiersza polecenia dewelopera Visual C++ jest prawidłowo skonfigurowane. W oknie wiersza polecenia wprowadź `cl` i sprawdź, czy dane wyjściowe wygląda następująco:  
  
    ```Output  
    C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl  
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86  
    Copyright (C) Microsoft Corporation.  All rights reserved.  
    
    usage: cl [ option... ] filename... [ /link linkoption... ]  
    ```  
  
     Może to być różnic w bieżącym katalogu i numery wersji, w zależności od wersji programu Visual C++ i zainstalowane jakiekolwiek aktualizacje. Jeśli jest to podobne do zostanie wyświetlony, następnie można przystąpić do tworzenia programów C lub C++ w wierszu polecenia.  
  
    > [!NOTE]
    >  Jeśli zostanie wyświetlony błąd, takie jak "'cl' nie jest rozpoznawana jako polecenie wewnętrzne lub zewnętrzne, program wykonywalny lub plik wsadowy" Błąd C1034 lub błąd LNK1104 po uruchomieniu **cl** polecenia, a następnie albo nie używasz wiersz polecenia dewelopera lub Czasami występują problemy z instalacją programu Visual C++. Przed kontynuowaniem musisz naprawić ten problem.  
  
     Jeśli nie możesz znaleźć dewelopera skrót do wiersza polecenia lub jeśli zostanie wyświetlony komunikat o błędzie podczas wprowadzania `cl`, a następnie instalację programu Visual C++ może wystąpić problem. Spróbuj ponownie zainstalować składnik Visual C++ w programie Visual Studio lub ponownie zainstaluj program Microsoft Visual C++ kompilacji narzędzia. Nie przejdź do następnej sekcji, dopóki działa to. Aby uzyskać więcej informacji o instalowaniu i rozwiązywanie problemów z języka Visual C++, zobacz [program Visual Studio](/visualstudio/install/install-visual-studio).  
  
    > [!NOTE]
    >  W zależności od wersji systemu Windows na komputerze oraz konfiguracji zabezpieczeń systemu, może być konieczne kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla deweloperów skrót do wiersza polecenia, a następnie wybierz pozycję **Uruchom jako Administrator** do pomyślnie skompilować i uruchomić program, który utworzonych za pomocą tego przewodnika.  
  
### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Utwórz plik źródłowy języka Visual C++ i skompiluj go w wierszu polecenia  
  
1.  W oknie wiersza polecenia dewelopera wprowadź **md c:\hello** do tworzenia katalogu, a następnie wprowadź **cd c:\hello** zmiany do tego katalogu. Jest to pliku źródłowego i skompilowany program są tworzone w katalogu.  
  
2.  Wprowadź **hello.cpp Notatnik** w oknie wiersza polecenia.  
  
     Wybierz **tak** gdy pojawi się monit o utworzenie pliku Notatnika. Spowoduje to otwarcie puste okno programu Notatnik, gotowe do wprowadzenia kodu w pliku o nazwie hello.cpp.  
  
3.  W programie Notatnik wprowadź następujące wiersze kodu:  
  
    ```cpp  
    #include <iostream>  
    using namespace std;  
    void main()  
    {  
        cout << "Hello, world, from Visual C++!" << endl;  
    }  
    ```  
  
     To jest bardzo prosty program, który będzie zapisu jednego wiersza tekstu na ekranie, a następnie zamknij. Aby zminimalizować błędy, skopiuj ten kod i wklej go do Notatnika.  
  
4.  Zapisz swoją pracę! W Notatniku na **pliku** menu, wybierz **zapisać**.  
  
     Gratulacje, utworzono plik źródłowy języka Visual C++, hello.cpp, który jest gotowy do skompilowania.  
  
5.  Przejdź do okna wiersza polecenia dewelopera. Wprowadź **dir** w wierszu polecenia, aby wyświetlić zawartość katalogu c:\hello. Powinny pojawić się hello.cpp pliku źródłowego w liście zawartości katalogu, który wygląda następująco:  
  
    ```Output  
    c:\hello>dir  
     Volume in drive C has no label.  
     Volume Serial Number is CC62-6545  
  
     Directory of c:\hello  
  
    05/24/2016  05:36 PM    <DIR>          .  
    05/24/2016  05:36 PM    <DIR>          ..  
    05/24/2016  05:37 PM               115 hello.cpp  
                   1 File(s)            115 bytes  
                   2 Dir(s)  571,343,446,016 bytes free  
  
    ```  
  
     Daty i inne szczegóły różnią się na komputerze. Jeśli nie widzisz pliku kodu źródłowego, hello.cpp, upewnij się, że zostały zmienione, aby nowo utworzony katalog c:\hello i w programie Notatnik, upewnij się, zapisać pliku źródłowego w tym katalogu. Upewnij się również kod źródłowy został zapisany z rozszerzeniem nazwy pliku .cpp, nie rozszerzenia .txt.  
  
6.  W wierszu polecenia dewelopera wprowadź `cl /EHsc hello.cpp` do skompilowania programu.  
  
     Cl.exe — kompilator generuje plik .obj, który zawiera skompilowany kod, a następnie uruchomi konsolidator, aby utworzyć program wykonywalny o nazwie hello.exe. Ta nazwa pojawi się w wierszach kompilator wyświetlane informacje danych wyjściowych. Dane wyjściowe kompilatora powinien wyglądać następująco:  
  
    ```Output  
    c:\hello>cl /EHsc hello.cpp  
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86  
    Copyright (C) Microsoft Corporation.  All rights reserved.  
  
    hello.cpp  
    Microsoft (R) Incremental Linker Version 14.10.25017.0  
    Copyright (C) Microsoft Corporation.  All rights reserved.  
  
    /out:hello.exe  
    hello.obj  
    ```  
  
    > [!NOTE]
    >  Jeśli zostanie wyświetlony błąd, takie jak "'cl' nie jest rozpoznawana jako polecenie wewnętrzne lub zewnętrzne, program wykonywalny lub plik wsadowy" Błąd C1034 lub błąd LNK1104, wiersza polecenia dewelopera jest nieprawidłowo skonfigurowane. Aby uzyskać informacje na temat rozwiązać ten problem, przejdź wstecz do **Otwórz okno wiersza polecenia dewelopera** sekcji.  
  
    > [!NOTE]
    >  Jeśli inny kompilatora lub konsolidatora błąd lub ostrzeżenie, przejrzeć kod źródłowy poprawić błędy, zapisać go i ponownie uruchom kompilatora. Aby uzyskać informacje o określonych błędach Użyj pola wyszukiwania na tej stronie MSDN szukać numer błędu.  
  
7.  Aby uruchomić hello.exe program, w wierszu polecenia, wpisz `hello`.  
  
     Program wyświetla ten tekst i kończy działanie:  
  
    ```Output  
    Hello, world, from Visual C++!  
    ```  
  
     Gratulacje, po prostu został skompilowany i uruchom program w języku C++ za pomocą narzędzia wiersza polecenia.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przykładzie "Hello, World" jest około tak proste, jak pobrać program w języku C++. Rzeczywistych programy posiadają pliki nagłówka i więcej plików źródłowych, łącze w bibliotekach i przydatne pracę.  
  
 Kroki opisane w tym przewodniku służy do tworzenia własnego kodu C++, zamiast wpisywać kod przykładowych pokazano. Można również tworzyć wiele C++ kod przykładowy programy, które można znaleźć w innym miejscu. Można umieścić kodu źródłowego i tworzenia aplikacji w taki sposób, w dowolnym katalogu zapisywalny. Domyślnie środowiska IDE programu Visual Studio tworzy projekty w folderze dokumenty w podfolderze projektów programu Visual Studio folder o nazwie dla używanej wersji programu Visual Studio.  
  
 Aby skompilować program, który ma wiele plików kodu źródłowego, wprowadź je w wierszu polecenia następujący:  
  
 `cl /EHsc file1.cpp file2.cpp file3.cpp`  
  
 **/Ehsc** opcji wiersza polecenia instruuje kompilator, aby włączyć C++, obsługa wyjątków. Aby uzyskać więcej informacji, zobacz [/EH (Model obsługi wyjątku)](../build/reference/eh-exception-handling-model.md).  
  
 Jeśli podasz wiele plików źródłowych, takich jak to kompilator używa pierwszego pliku wejściowego do utworzenia nazwę programu. W takim przypadku danych wyjściowych program o nazwie file1.exe. Aby zmienić nazwę program1.exe, Dodaj [/out](../build/reference/out-output-file-name.md) — opcja konsolidatora:  
  
 `cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`  
  
 I aby wykryć automatycznie więcej błędów programowania, zaleca się skompilować przy użyciu [/W3](../build/reference/compiler-option-warning-level.md) lub [/W4](../build/reference/compiler-option-warning-level.md) ostrzeżenie opcję poziomu:  
  
 `cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`  
  
 Kompilator, cl.exe, ma wiele więcej opcji dotyczą kompilacji, optymalizacja, debugowania i analizowania kodu. Lista szybki, wprowadź **cl /?** w wierszu polecenia dewelopera. Można również skompilować i połączyć oddzielnie i zastosować opcje konsolidatora w bardziej złożonych scenariuszach kompilacji. Aby uzyskać więcej informacji na kompilatora i opcje konsolidatora i użycia, zobacz [odwołanie kompilacji C/C++](../build/reference/c-cpp-building-reference.md).  
  
 NMAKE i pliki reguł programu make lub MSBuild i pliki projektu można użyć do konfigurowania i kompilacji projektów bardziej złożone w wierszu polecenia. Aby uzyskać więcej informacji na temat używania tych narzędzi, zobacz [odwołanie NMAKE](../build/nmake-reference.md) i [MSBuild](../build/msbuild-visual-cpp.md).  
  
 Języki C i C++ są podobne, ale nie sam. Kompilator Visual C++ używa Prosta reguła, aby określić język, który będzie używany podczas kompiluje kod. Domyślnie kompilatora Visual C++ traktuje wszystkie pliki, które kończą się .c jako kodu źródłowego C i wszystkich plików, które kończą się .cpp jako kodu źródłowego języka C++. Aby wymusić kompilatorowi na traktowanie wszystkich plików jako C++ niezależnie od rozszerzenia nazwy pliku, użyj [/TC](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) — opcja kompilatora.  
  
 Kompilator Visual C++ obejmuje C Runtime biblioteki (CRT) ogólnie zgodne ze standardem ISO C99, ale nie jest ściśle zgodna. W większości przypadków kod przenośny skompilować i uruchomić zgodnie z oczekiwaniami. Visual C++ nie obsługuje pewnych zmian CRT ISO C11. Niektóre funkcje bibliotek i nazwy funkcji POSIX są używane przez kompilator języka Visual C++. Funkcje są obsługiwane, ale preferowaną nazwy zostały zmienione. Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md) i [C4996 ostrzeżenie kompilatora (poziom 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)   
 [Opcje kompilatora](../build/reference/compiler-options.md)