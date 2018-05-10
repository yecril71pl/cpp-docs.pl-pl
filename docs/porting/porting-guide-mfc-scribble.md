---
title: 'Przewodnik przenoszenia: Aplikacja Scribble MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8ddb517d-89ba-41a1-ab0d-4d2c6d9047e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe0ae0580be4ab062e3ff7ee0cedfb42e201272d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="porting-guide-mfc-scribble"></a>Przewodnik przenoszenia: Aplikacja Scribble MFC
Ten temat jest pierwszy kilka tematów, które przedstawiono procedurę uaktualniania dla projektów Visual C++, które zostały utworzone w starszej wersji programu Visual Studio do programu Visual Studio 2017 r. W tych tematach przedstawiono proces uaktualniania przykładzie, rozpoczynając od projektu bardzo proste i przechodzenia do nich nieco bardziej skomplikowane. W tym temacie pracujemy przez proces uaktualniania dla konkretnego projektu, Bazgroły MFC. Jest on odpowiedni jako podstawowe wprowadzenie do procesu uaktualniania dla projektów C++.  
  
 Każda wersja programu Visual Studio przedstawiono możliwe niezgodności, które skomplikować przenoszenia kodu ze starszej wersji programu Visual Studio na nowszą. Czasami wymagane zmiany są w kodzie, więc należy ponownie skompilować i zaktualizuj kod, a czasami są wymagane zmiany w plikach projektu. Po otwarciu projektu, który został utworzony w poprzedniej wersji programu Visual Studio, Visual Studio automatycznie pyta, czy zaktualizować projekt lub rozwiązanie do najnowszej wersji. Te narzędzia zazwyczaj uaktualnić tylko te pliki projektu; nie należy modyfikować kodu źródłowego.  
  
## <a name="mfc-scribble"></a>Aplikacja Scribble MFC  
 Bazgroły MFC jest dobrze znanego próbki, która została uwzględniona w wielu różnych wersjach programu Visual C++. Jest prostą aplikację rysunku, która ilustruje niektóre podstawowe funkcje MFC. Istnieją różne wersje systemu ją, łącznie z obu zarządzane i kodu natywnego. Na przykład możemy znaleziono starą wersję bazgrołów w kodzie natywnym z programu Visual Studio 2005 i otworzyć go w programie Visual Studio 2017 r.  
  
 Przed rozpoczęciem aktualizacji, upewnij się, że obciążenie pulpitu systemu Windows zainstalowane. Otwórz Instalator programu Visual Studio (vs_installer.exe). Jest jednym ze sposobów Otwórz Instalator, aby wybrać plik | Nowy projekt i przewiń w dół listę szablonów zainstalowanych dopóki zobacz "Otwórz Instalator programu Visual Studio". Po otwarciu Instalator zostanie wyświetlone wszystkie dostępne obciążenia. Jeśli nie zaznaczono pola obciążenia pulpitu systemu Windows, zaznacz go i kliknij przycisk Modyfikuj w dolnej części okna. 


 Następnie należy wykonać kopię zapasową całego rozwiązania i całą jego zawartość. 
 
 Na koniec musimy podejmowanie decyzji o określonej metody uaktualnienia. Dla bardziej złożonych rozwiązań i projektów, które nie zostały uaktualnione przez długi czas należy rozważyć uaktualnienie jednej wersji programu Visual Studio w czasie. W ten sposób można zawęzić wersji programu Visual Studio wprowadzone problem. W projekcie proste warto próby otwarcia go w najnowszej wersji programu Visual Studio, dzięki czemu kreatora można skonwertować projektu. Jeśli to nie zadziała, możesz spróbować uaktualniania jednej wersji jednocześnie, jeśli użytkownik ma dostęp do odpowiedniej wersji programu Visual Studio.  
  
 Należy pamiętać, że można również uruchomić devenv w wierszu polecenia przy użyciu `/Upgrade` opcji, a nie za pomocą kreatora, aby uaktualnić swoje projekty. Zobacz [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe). Może to być przydatne w przypadku automatyzacji procesu uaktualniania dla wielu projektów.  
  
### <a name="step-1-converting-the-project-file"></a>Krok 1. Konwertowanie pliku projektu  
 Po otwarciu pliku starego projektu w programie Visual Studio 2017 Visual Studio oferuje Skonwertuj plik projektu do najnowszej wersji, możemy akceptowane. Pojawił się następujące okno dialogowe:  
  
 ![Przegląd zmian projektu i rozwiązania](../porting/media/scribbleprojectupgrade.PNG "ScribbleProjectUpgrade")  
  
 Wystąpił błąd podczas powiadamiania nam, że docelowy Itanium nie są dostępne, a nie można przekonwertować.  
  
```Output  
Platform 'Itanium' is missing from this project. All the configurations and their file configuration settings specific to this platform will be ignored. If you want this platform converted, please make sure you have the corresponding platform installed under '%vctargetpath%\platforms\Itanium'.Continue to convert this project without this platform?  
```  
  
 Podczas poprzedniej bazgrołów projekt został utworzony Itanium został platformy docelowej ważne. Platformy systemu Windows nie obsługuje już Itanium, więc Wybraliśmy kontynuować bez obsługi platformy Itanium.  
  
 Visual Studio są następnie wyświetlane w raporcie migracji lista wszystkie problemy z starego pliku projektu.  
  
 ![Raport o uaktualnieniu](../porting/media/scribblemigrationreport.PNG "ScribbleMigrationReport")  
  
 W takim przypadku problemy zostały wszystkie ostrzeżenia i Visual Studio wprowadzone odpowiednie zmiany w pliku projektu. Istotną różnicą chodzi projektu jest jest narzędzie kompilacji zmiana z program vcbuild dla programu msbuild. Ta zmiana została wprowadzona w programie Visual Studio 2010. Inne zmiany obejmują niektóre rozmieszczania sekwencję elementów w samym pliku projektu. Brak problemów wymagane dodatkowe uwagi dla tego prostego projektu.  
  
### <a name="step-2-getting-it-to-build"></a>Krok 2. Wprowadzenie do kompilacji  
 Przed rozpoczęciem budowania, musimy sprawdzić zestaw narzędzi platformy aby było wiadomo, jakiej wersji kompilatora używa system projektu. W oknie dialogowym właściwości projektu w obszarze **właściwości konfiguracji**w **ogólne** kategorii, obejrzyj **zestaw narzędzi platformy** właściwości. Zawiera wersję programu Visual Studio oraz numer wersji narzędzia platformy, w tym przypadku jest v141 dla używanej wersji programu Visual Studio 2017 narzędzi. Podczas konwersji projektu, który pierwotnie został skompilowany z programu Visual C++ 2010 2012, 2013 lub 2015, zestaw narzędzi nie zostanie automatycznie zaktualizowana do narzędzi Visual Studio 2017 r.   
  
  Aby wprowadzić przełącznik Unicode, otwórz właściwości projektu, w obszarze **właściwości konfiguracji**, wybierz **ogólne** , a następnie zlokalizuj **zestaw znaków** właściwości. Zmień od **Użyj wielobajtowego zestawu znaków** do **Użyj kodowania Unicode**. Ta zmiana powoduje, że teraz _unicode — makra UNICODE są zdefiniowane i _MBCS nie jest, który można sprawdzić w oknie dialogowym właściwości, w obszarze **C/C++** kategorii w **wiersza polecenia** właściwości.  
  
```Output  
/GS /analyze- /W4 /Zc:wchar_t /Zi /Gm- /Od /Fd".\Debug\vc141.pdb" /Zc:inline /fp:precise /D "_AFXDLL" /D "WIN32" /D "_DEBUG" /D "_WINDOWS" /D "_UNICODE" /D "UNICODE" /errorReport:prompt /WX /Zc:forScope /Gd /Oy- /MDd /Fa".\Debug\" /EHsc /nologo /Fo".\Debug\" /Fp".\Debug\Scribble.pch" /diagnostics:classic 
```  
  
 Chociaż bazgrołów projektu nie został skonfigurowany do Kompiluj z użyciem znaków Unicode, plik został już zapisany z tchar — zamiast char, tak faktycznie nie trzeba żadnego ustawienia można zmienić. Projekt pomyślnie kompilacji z zestawu znaków Unicode.  
  
 Teraz Skompiluj rozwiązanie. W oknie danych wyjściowych kompilatora informuje NAS, że _WINNT32_WINNT nie jest zdefiniowany:  
  
```Output  
_WIN32_WINNT not defined. Defaulting to _WIN32_WINNT_MAXVER (see WinSDKVer.h)  
```  
  
 To ostrzeżenie, nie jest błąd, a jest to bardzo powszechne podczas uaktualniania projektu Visual C++. Jest to makro, który definiuje, jakie Najniższa wersja systemu Windows, które naszym aplikacja będzie uruchamiana na. Jeśli firma Microsoft zignorować to ostrzeżenie, możemy zaakceptuj wartość domyślną, _WIN32_WINNT_MAXVER, co oznacza bieżącą wersję systemu Windows. Dla tabeli możliwych wartości, zobacz [korzystanie z nagłówków systemu Windows](https://msdn.microsoft.com/en-us/library/aa383745.aspx). Na przykład możemy ustawić go uruchomić w dowolnej wersji systemu Vista i nowszych wersjach.  
  
```  
#define _WIN32_WINNT _WIN32_WINNT_VISTA  
```  
  
 Jeśli kod korzysta z części interfejsu API systemu Windows, które nie są dostępne w wersji systemu Windows, który można określić za pomocą makra, powinna zostać wyświetlona który jako błąd kompilatora. W przypadku kodu bazgrołów nie było błędu.  
  
### <a name="step-3-testing-and-debugging"></a>Krok 3. Testowanie i debugowanie  
 Brak nie zestawu testów, możemy właśnie uruchomiono aplikację, przetestować jego funkcje ręcznie za pośrednictwem interfejsu użytkownika. Zaobserwowano żadnych problemów.  
  
### <a name="step-4-improve-the-code"></a>Krok 4. Poprawić kod  
 Teraz, po migracji do programu Visual Studio 2017 można wprowadzić kilka zmian, aby móc korzystać z nowych funkcji języka C++. Bieżąca wersja kompilatora C++ jest znacznie więcej zgodność C++ wersji standard, a następnie poprzedniej, jeśli masz zdanie dokonanie kodu zmienia się na wprowadzić kod bardziej bezpiecznej i przenośną inne kompilatory i systemy operacyjne, należy rozważyć niektóre ulepszenia.  
  
## <a name="next-steps"></a>Następne kroki  
 Bazgrołów był aplikacji pulpitu systemu Windows small i proste, a nie był trudny do konwersji. Wiele aplikacji małych, prostych równie łatwo przekonwertować do nowej wersji.  Wiele projektów i bibliotek, niestandardowe kroki procesu kompilacji bardziej złożonych aplikacji o wiele więcej wierszy kodu, starsze starszego kodu, który może nie być aktualne nowoczesnych standardów engineering, lub dla złożonych skryptową kompilacjach zautomatyzowanych potrwa więcej czasu na uaktualnienie. Kontynuuj [następnym przykładzie](../porting/porting-guide-com-spy.md), aplikacji ATL i COM o nazwie Spy modelu COM.  
  
## <a name="see-also"></a>Zobacz też  
 [Przenoszenie i uaktualnianie: przykłady i analizy przypadków:](../porting/porting-and-upgrading-examples-and-case-studies.md)   
 [Następnym przykładzie: Narzędzie Spy modelu COM](../porting/porting-guide-com-spy.md)
