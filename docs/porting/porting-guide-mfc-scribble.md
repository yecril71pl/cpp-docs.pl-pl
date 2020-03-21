---
title: 'Przewodnik przenoszenia: Aplikacja Scribble MFC'
ms.date: 10/23/2019
ms.assetid: 8ddb517d-89ba-41a1-ab0d-4d2c6d9047e8
ms.openlocfilehash: 789d29effeea76045a4a10fbca19f20d06778f7c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076966"
---
# <a name="porting-guide-mfc-scribble"></a>Przewodnik przenoszenia: Aplikacja Scribble MFC

Ten temat jest pierwszym z kilku tematów, które wprowadzają do procedury uaktualniania projektów programu Visual Studio C++ , które zostały utworzone we wcześniejszych wersjach programu Visual Studio, do Visual Studio 2017. Te tematy wprowadzają proces uaktualniania na przykład, rozpoczynając od bardzo prostego projektu i przechodzą do nieco bardziej złożonych. W tym temacie opisano proces uaktualniania dla określonego projektu, Bazgroły MFC. Jest to podstawowe wprowadzenie do procesu uaktualniania dla C++ projektów.

Każda wersja programu Visual Studio wprowadza możliwe niezgodności, które mogą poskomplikowanić przeniesienie kodu ze starszej wersji programu Visual Studio do nowszej. Czasami wymagane zmiany są w kodzie, dlatego należy ponownie skompilować i zaktualizować kod, a czasami wymagane zmiany są w plikach projektu. Po otwarciu projektu, który został utworzony przy użyciu poprzedniej wersji programu Visual Studio, program Visual Studio automatycznie wyświetli monit z pytaniem, czy zaktualizować projekt lub rozwiązanie do najnowszej wersji. Te narzędzia zwykle uaktualniają tylko pliki projektu; nie modyfikują kodu źródłowego.

## <a name="mfc-scribble"></a>MFC Scribble

Obiekt Bazgroły MFC jest dobrze znanym przykładem, który został uwzględniony w wielu różnych C++wersjach wizualizacji. Jest to prosta aplikacja do rysowania, która ilustruje niektóre podstawowe funkcje MFC. Dostępne są różne wersje, w tym wersje zarządzane i natywne. W tym przykładzie znaleźliśmy starą wersję Bazgroły w kodzie natywnym z programu Visual Studio 2005 i otwarto ją w programie Visual Studio 2017.

Przed podjęciem próby uaktualnienia upewnij się, że zainstalowano obciążenie pulpitu systemu Windows. Otwórz Instalatora programu Visual Studio (vs_installer. exe). Jednym ze sposobów otwierania Instalatora jest wybranie opcji **plik** > **Nowy projekt** i przewinięcie do dołu listy zainstalowanych szablonów do momentu wyświetlenia **otwartego Instalator programu Visual Studio**. Po otwarciu Instalatora zostaną wyświetlone wszystkie dostępne obciążenia. Jeśli nie wybrano pola dla obciążenia **pulpitu systemu Windows** , wybierz je i kliknij przycisk **Modify** u dołu okna.

Następnie wykonaj kopię zapasową całego rozwiązania i całej jego zawartości.

Na koniec Otwórz rozwiązanie w najnowszej wersji programu Visual Studio i zezwól kreatorowi na konwersję projektu.

Należy pamiętać, że można również uruchomić devenv w wierszu polecenia, korzystając z opcji `/Upgrade`, zamiast korzystać z kreatora w celu uaktualnienia projektów. Zobacz [/Upgrade (devenv. exe)](/visualstudio/ide/reference/upgrade-devenv-exe). Może to być przydatne w automatyzowaniu procesu uaktualniania dla dużej liczby projektów.

### <a name="step-1-converting-the-project-file"></a>Krok 1. Konwertowanie pliku projektu

Gdy otworzysz stary plik projektu w programie Visual Studio, program Visual Studio oferuje możliwość konwersji pliku projektu do najnowszej wersji, która została zaakceptowana. Pojawiło się następujące okno dialogowe:

![Przejrzyj zmiany projektu i rozwiązania](../porting/media/scribbleprojectupgrade.PNG "Przejrzyj zmiany projektu i rozwiązania")

Wystąpił błąd podczas powiadamiania nas, że obiekt docelowy Itanium nie jest dostępny i nie zostanie przekonwertowany.

```Output
Platform 'Itanium' is missing from this project. All the configurations and their file configuration settings specific to this platform will be ignored. If you want this platform converted, please make sure you have the corresponding platform installed under '%vctargetpath%\platforms\Itanium'.Continue to convert this project without this platform?
```

W momencie utworzenia poprzedniego projektu bazgrołów Itanium była ważną platformą docelową. Platforma systemu Windows nie obsługuje już procesorów Itanium, dlatego wybieramy kontynuację bez obsługi platformy Itanium.

Program Visual Studio wyświetli raport dotyczący migracji zawierający listę wszystkich problemów ze starym plikiem projektu.

![Raport o uaktualnieniu](../porting/media/scribblemigrationreport.PNG "Raport o uaktualnieniu")

W takim przypadku problemy były wszystkie ostrzeżeniami, a program Visual Studio wprowadził odpowiednie zmiany w pliku projektu. Istotną różnicą, o ile chodzi o projekt, jest to, że narzędzie kompilacji zmieniło się z vcbuild na MSBuild. Ta zmiana została wprowadzona po raz pierwszy w programie Visual Studio 2010. Inne zmiany obejmują kilka przemieszczenia sekwencji elementów w pliku projektu. Żaden z problemów nie wymagał dalszej uwagi dla tego prostego projektu.

### <a name="step-2-getting-it-to-build"></a>Krok 2. Trwa przygotowywanie do kompilacji

Przed rozpoczęciem kompilowania sprawdzimy zestaw narzędzi platformy, aby poznać, która wersja kompilatora używa systemu projektu. W oknie dialogowym właściwości projektu, w obszarze **Właściwości konfiguracji**, w kategorii **Ogólne** Sprawdź właściwość zestaw **narzędzi platformy** . Zawiera wersję programu Visual Studio i numer wersji narzędzia platformy, która w tym przypadku jest najnowsze 141 dla narzędzia Visual Studio 2017. Podczas konwersji projektu, który został pierwotnie skompilowany przy użyciu programu Visual Studio 2010, 2012, 2013 lub 2015, zestaw narzędzi nie jest automatycznie aktualizowany do najnowszego zestawu narzędzi.

Aby przełączyć się na format Unicode, Otwórz właściwości projektu, w obszarze **Właściwości konfiguracji**, wybierz sekcję **Ogólne** i Znajdź właściwość **zestaw znaków** . Zmień tę wartość przy **użyciu zestawu znaków wielobajtowych** , aby **użyć zestawu znaków Unicode**. Efektem tej zmiany jest to, że teraz makra _UNICODE i Unicode są zdefiniowane i nie _MBCS, które można sprawdzić w oknie dialogowym właściwości w kategorii **C/C++**  w właściwości **wiersza polecenia** .

```Output
/GS /analyze- /W4 /Zc:wchar_t /Zi /Gm- /Od /Fd".\Debug\vc141.pdb" /Zc:inline /fp:precise /D "_AFXDLL" /D "WIN32" /D "_DEBUG" /D "_WINDOWS" /D "_UNICODE" /D "UNICODE" /errorReport:prompt /WX /Zc:forScope /Gd /Oy- /MDd /Fa".\Debug\" /EHsc /nologo /Fo".\Debug\" /Fp".\Debug\Scribble.pch" /diagnostics:classic
```

Mimo że projekt bazgroł nie został skonfigurowany do kompilowania przy użyciu znaków Unicode, został już wpisany przy użyciu używanie TCHAR zamiast char, więc niczego nie trzeba zmieniać. Projekt został pomyślnie skompilowany z zestawem znaków Unicode.

Teraz Skompiluj rozwiązanie. W oknie dane wyjściowe kompilator informuje nas, że _WINNT32_WINNT nie jest zdefiniowany:

```Output
_WIN32_WINNT not defined. Defaulting to _WIN32_WINNT_MAXVER (see WinSDKVer.h)
```

Jest to ostrzeżenie, a nie błąd i jest bardzo powszechne podczas uaktualniania projektu programu Visual Studio C++ . Jest to makro definiujące najmniejszą wersję systemu Windows, na której będzie działać aplikacja. Jeśli zignorujesz ostrzeżenie, przyjmie wartość domyślną _WIN32_WINNT_MAXVER, co oznacza bieżącą wersję systemu Windows. Aby zapoznać się z tabelą możliwych wartości, zobacz [Używanie nagłówków systemu Windows](/windows/win32/WinProg/using-the-windows-headers). Można na przykład skonfigurować go do uruchamiania w dowolnej wersji z systemu Vista.

```cpp
#define _WIN32_WINNT _WIN32_WINNT_VISTA
```

Jeśli kod używa części interfejsu API systemu Windows, które nie są dostępne w wersji systemu Windows, która jest określona za pomocą tego makra, należy zobaczyć, że jako błąd kompilatora. W przypadku kodu bazgrołów nie ma błędów.

### <a name="step-3-testing-and-debugging"></a>Krok 3. Testowanie i debugowanie

Nie ma zestawu testów, dlatego właśnie uruchomił aplikację, przetestował jej funkcje ręcznie za pomocą interfejsu użytkownika. Nie zaobserwowano żadnych problemów.

### <a name="step-4-improve-the-code"></a>Krok 4. Ulepszanie kodu

Po przeprowadzeniu migracji do programu Visual Studio 2017 warto wprowadzić pewne zmiany, aby skorzystać z nowych C++ funkcji. Bieżąca wersja C++ kompilatora jest znacznie bardziej zgodna ze C++ standardem i poprzednimi wersjami, więc jeśli chcesz wprowadzić pewne zmiany w kodzie, aby zwiększyć bezpieczeństwo kodu i zwiększyć ich przenośność do innych kompilatorów i systemów operacyjnych, należy wziąć pod uwagę pewne ulepszenia.

## <a name="next-steps"></a>Następne kroki

Bazgroły były małymi i prostymi aplikacjami klasycznymi systemu Windows i nie było trudne do przekonwertowania. Wiele małych, prostych aplikacji, które są konwertowane równie łatwo, jak w przypadku nowej wersji.  W przypadku bardziej złożonych aplikacji z wieloma dodatkowymi wierszami kodu starszy starszy kod, który może nie mieć do nowoczesnych standardów inżynieryjnych, wielu projektów i bibliotek, niestandardowych kroków kompilacji lub złożonych zautomatyzowanych kompilacji inicjowanych przez skrypty, zajmie więcej czasu na uaktualnienie. Przejdź do [następnego przykładu](../porting/porting-guide-com-spy.md)— aplikacji ATL/com o nazwie com Spy.

## <a name="see-also"></a>Zobacz też

[Przenoszenie i uaktualnianie: Przykłady i analizy przypadków](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Następny przykład: COM Spy](../porting/porting-guide-com-spy.md)
