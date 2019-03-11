---
title: 'Przewodnik przenoszenia: Aplikacja Scribble MFC'
ms.date: 11/19/2018
ms.assetid: 8ddb517d-89ba-41a1-ab0d-4d2c6d9047e8
ms.openlocfilehash: 436dd27d8c2669e21ddc8a9e453f369cdd14f70c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741296"
---
# <a name="porting-guide-mfc-scribble"></a>Przewodnik przenoszenia: Aplikacja Scribble MFC

W tym temacie jest to pierwszy kilku tematów, które służą jako wprowadzenie do procedury uaktualniania dla projektów Visual C++, które zostały utworzone w starszych wersjach programu Visual Studio do programu Visual Studio 2017. Tych tematach przedstawiono proces uaktualniania według przykładu, rozpoczynając od bardzo prosty projekt i przejście do bardziej złożonych z nich. W tym temacie będziemy działać przeprowadzenie procesu aktualizacji dla określonego projektu, klasa Scribble MFC. Jest on odpowiedni jako wstęp do procesu uaktualniania dla projektów C++.

Każda wersja programu Visual Studio wprowadza potencjalne niezgodności, które mogą skomplikować przenoszenie kodu ze starszej wersji programu Visual Studio do nowszej. Czasami wymagane zmiany są w kodzie, więc należy ponownie skompilować i zaktualizować swój kod, a czasami są wymagane zmiany w plikach projektu. Po otwarciu projektu, który został utworzony w poprzedniej wersji programu Visual Studio, Visual Studio automatycznie pyta, czy zaktualizować projekt lub rozwiązanie do najnowszej wersji. Te narzędzia zazwyczaj uaktualnić tylko te pliki projektu; nie należy modyfikować kodu źródłowego.

## <a name="mfc-scribble"></a>Aplikacja Scribble MFC

Klasa Scribble MFC jest dobrze znanych próbki, która została uwzględniona w wielu różnych wersjach programu Visual C++. Jest prostej aplikacji rysowania, który pokazano niektóre z podstawowych funkcji MFC. Istnieją różne wersje niedostępnych, w tym zarządzanych i wersje kodu natywnego. W tym przykładzie firma Microsoft znaleziono starą wersję bazgrołów w kodzie natywnym z programu Visual Studio 2005 i otworzyć go w programie Visual Studio 2017.

Przed rozpoczęciem aktualizacji, upewnij się, że masz zainstalowane obciążenie pulpitu Windows. Otwórz Instalatora programu Visual Studio (vs_installer.exe). Jednym ze sposobów, otwórz Instalator jest wybranie **pliku** > **nowy projekt** i przewiń w dół na liście zainstalowanych szablonów, aż zobaczysz **Otwórz Instalator programu Visual Studio**. Po otwarciu Instalatora zobaczysz wszystkie dostępne obciążeń. Jeśli pole **pulpitu Windows** obciążenia nie jest zaznaczone, a następnie wybierz ją i kliknij przycisk **Modyfikuj** znajdujący się u dołu okna.

Następnie utwórz kopię zapasową całego rozwiązania i całą jego zawartość.

Na koniec potrzebowaliśmy do podejmowania decyzji o określonej metody uaktualniania. Aby uzyskać bardziej złożonych rozwiązań i projektów, które nie zostały uaktualnione przez długi czas należy rozważyć uaktualnienie jednej wersji programu Visual Studio w danym momencie. W ten sposób można zawęzić wersji programu Visual Studio wprowadzone problem. Prosty projekt warto próby otwarcia go w najnowszej wersji programu Visual Studio, dzięki czemu kreatora w celu przekonwertowania projektu. Jeśli to nie zadziała, możesz spróbować uaktualniania jednej wersji w czasie, jeśli masz dostęp do odpowiedniej wersji programu Visual Studio.

Należy pamiętać, że można również uruchomić devenv, w wierszu polecenia przy użyciu `/Upgrade` opcji, a nie za pomocą kreatora, aby uaktualnić swoje projekty. Zobacz [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe). Który może być przydatne w przypadku automatyzacji procesu uaktualniania dużej liczby projektów.

### <a name="step-1-converting-the-project-file"></a>Krok 1. Konwertowanie pliku projektu

Po otwarciu stary plik projektu w programie Visual Studio 2017, Visual Studio oferuje przekonwertować plik projektu do najnowszej wersji, firma Microsoft zaakceptowane. Pojawiły się następujące okno dialogowe:

![Przegląd zmian projektu i rozwiązania](../porting/media/scribbleprojectupgrade.PNG "przegląd zmian projektu i rozwiązania")

Wystąpił błąd powiadamiania nam, że docelowy Itanium nie jest dostępny i nie można przekonwertować.

```Output
Platform 'Itanium' is missing from this project. All the configurations and their file configuration settings specific to this platform will be ignored. If you want this platform converted, please make sure you have the corresponding platform installed under '%vctargetpath%\platforms\Itanium'.Continue to convert this project without this platform?
```

W czasie, utworzony poprzedni projekt Bazgroły Itanium było ważne docelowej platformy. Platforma Windows nie obsługuje już Itanium, więc Wybraliśmy kontynuować bez obsługi platformę Itanium.

Program Visual Studio wyświetlony raport migracji w przypadku wszystkich problemów za pomocą starego pliku projektu.

![Raport o uaktualnieniu](../porting/media/scribblemigrationreport.PNG "raport o uaktualnieniu")

W tym przypadku problemy zostały wszystkie ostrzeżenia, a program Visual Studio wprowadził odpowiednie zmiany w pliku projektu. Istotną różnicą chodzi projektu jest to, że narzędzia do kompilowania zmieniła się z program vcbuild do programu msbuild. Ta zmiana została wprowadzona w programie Visual Studio 2010. Inne zmiany obejmują niektóre zmiany w przepisach sekwencję elementów w samym pliku projektu. Brak problemów wymagane dalsze uwagi dla tego prostego projektu.

### <a name="step-2-getting-it-to-build"></a>Krok 2. Wprowadzenie do kompilacji

Przed kompilacją, możemy sprawdzić zestaw narzędzi platformy, aby było wiadomo, jakiej wersji kompilatora system projektu używa. W oknie dialogowym właściwości projektu w obszarze **właściwości konfiguracji**w **ogólne** kategorii przyjrzeć **zestawu narzędzi platformy** właściwości. Zawiera wersję programu Visual Studio i numeru wersji narzędzi platformy, która w tym przypadku jest w wersji 141 dla Visual Studio 2017 wersja narzędzi. Podczas konwersji projektu, który pierwotnie został skompilowany przy użyciu programu Visual C++ 2010, 2012, 2013 lub 2015 r. zestaw narzędzi nie jest automatycznie aktualizowany na zestaw narzędzi Visual Studio 2017.

Aby wprowadzić przełącznika Unicode, otwórz właściwości projektu w obszarze **właściwości konfiguracji**, wybierz **ogólne** sekcji, a następnie zlokalizuj **zestaw znaków** właściwości. Zmień ten program z **zestaw znaków wielobajtowych** do **Użyj kodowania Unicode**. Ta zmiana powoduje to teraz _UNICODE UNICODE makra są zdefiniowane i _MBCS nie jest dostępna, którą można sprawdzić w oknie dialogowym właściwości, w obszarze **C/C++** kategorii przy **wiersza polecenia** właściwości.

```Output
/GS /analyze- /W4 /Zc:wchar_t /Zi /Gm- /Od /Fd".\Debug\vc141.pdb" /Zc:inline /fp:precise /D "_AFXDLL" /D "WIN32" /D "_DEBUG" /D "_WINDOWS" /D "_UNICODE" /D "UNICODE" /errorReport:prompt /WX /Zc:forScope /Gd /Oy- /MDd /Fa".\Debug\" /EHsc /nologo /Fo".\Debug\" /Fp".\Debug\Scribble.pch" /diagnostics:classic
```

Mimo że bazgrołów projekt nie został skonfigurowany do kompilowania ze znakami Unicode, został on już zapisany z TCHAR zamiast char, więc nic faktycznie musi zostać zmienione. Projekt zostanie skompilowany poprawnie przy użyciu zestawu znaków Unicode.

Teraz można tworzyć rozwiązania. W oknie danych wyjściowych kompilatora informuje NAS, że tego _WINNT32_WINNT nie jest zdefiniowany:

```Output
_WIN32_WINNT not defined. Defaulting to _WIN32_WINNT_MAXVER (see WinSDKVer.h)
```

Jest to ostrzeżenie nie jest błąd i często zdarza się po uaktualnieniu projektu Visual C++. To makro, które określa jakie najniższy wersję Windows działającego na naszej aplikacji. Jeśli firma Microsoft zignorować to ostrzeżenie, firma Microsoft zaakceptuj wartość domyślną, _WIN32_WINNT_MAXVER, co oznacza bieżącą wersję systemu Windows. Dla tabeli możliwych wartości, zobacz [przy użyciu nagłówków Windows](/windows/desktop/WinProg/using-the-windows-headers). Na przykład możemy ustawić jego uruchomienie w dowolnej wersji systemu Vista i nowszych wersjach.

```cpp
#define _WIN32_WINNT _WIN32_WINNT_VISTA
```

Jeśli kod używa części interfejsu Windows API, które nie są dostępne w wersji systemu Windows, określ za pomocą makra, powinien zostać wyświetlony, jako błąd kompilatora. W przypadku kodu Bazgroły nie ma błędów.

### <a name="step-3-testing-and-debugging"></a>Krok 3. Testowanie i debugowanie

Ma nie testów, tak właśnie zaczynaliśmy aplikacji, przetestowane jego funkcje ręcznie za pomocą interfejsu użytkownika. Nie zaobserwowano żadnych problemów.

### <a name="step-4-improve-the-code"></a>Krok 4. Do poprawienia kodu

Teraz, gdy zostały poddane migracji do programu Visual Studio 2017, można wprowadzić pewne zmiany, aby móc korzystać z nowych funkcji języka C++. Bieżącej wersji kompilatora języka C++ jest znacznie większą zgodność C++ wersji standardowa, a następnie poprzedniej, więc w przypadku Pamiętaj się jakiś kod zmienia się na sprawić, że kod bardziej bezpiecznej i bardziej przenośny innych kompilatorach i systemów operacyjnych, należy rozważyć niektóre ulepszenia.

## <a name="next-steps"></a>Następne kroki

Bazgrołów został aplikacji pulpitu Windows małe i proste, a nie był trudny do konwersji. Wiele małych, prostych aplikacji równie łatwo przekonwertować do nowej wersji.  W przypadku bardziej złożonych aplikacji o wiele większą liczbę linii kodu, starsze starszego kodu, który może być maksymalnie nowoczesnych standardów inżynieryjnych, wiele projektów i bibliotek niestandardowych kroków kompilacji lub w przypadku złożonych inicjowanych przez skrypty kompilacji automatycznych zajmie więcej czasu na uaktualnienie. Kontynuuj [kolejny przykład](../porting/porting-guide-com-spy.md), ATL/aplikacji modelu COM wywołuje się, narzędzie Spy modelu COM.

## <a name="see-also"></a>Zobacz także

[Przenoszenie i uaktualnianie: Przykłady i analizy przypadków](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Następny przykład: Narzędzie Spy modelu COM](../porting/porting-guide-com-spy.md)
