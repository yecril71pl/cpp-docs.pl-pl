---
title: 'Przewodnik przenoszenia: Narzędzie Spy ++ | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e558f759-3017-48a7-95a9-b5b779d5e51d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd85aa6ce1cfee3416d04291d484a7bad6359ea4
ms.sourcegitcommit: 072e12d6b7a242765bdcc9afe4a14a284ade01fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2018
ms.locfileid: "50136188"
---
# <a name="porting-guide-spy"></a>Przewodnik przenoszenia: Narzędzie Spy++

To przenoszenia analiza przypadku jest przeznaczona do daje wyobrażenie o jakie typowym projekcie przenoszenia jest podobna, jakiego rodzaju problemy mogą wystąpić i pewne ogólne porady i wskazówki dotyczące przenoszenia problemów adresowania. Ma nie należy traktować jako ostateczny przewodnik do przenoszenia, ponieważ środowisko Eksportowanie projektu zależy od bardzo szczegółowe informacje na temat kodu.

## <a name="spy"></a>Spy++

Spy ++ to powszechnie używane narzędzie diagnostyczne graficznego interfejsu użytkownika dla pulpitu Windows, który udostępnia wszelkiego rodzaju informacji na temat elementów interfejsu użytkownika na pulpicie Windows. Pokazuje kompletny hierarchii systemu windows i zapewnia dostęp do metadanych dotyczących każdego okna i kontroli. Ta aplikacja przydatne zostało wysłane z programem Visual Studio przez wiele lat. Znaleziono starą wersję go ostatnio został skompilowany w Visual C++ 6.0 i przenieść go do programu Visual Studio 2015. Środowisko programu Visual Studio 2017 powinny być prawie identyczne.

Firma Microsoft uważa za takim być typowe eksportowaniu aplikacje pulpitu Windows, które używają MFC i Win32 API, szczególnie w przypadku starych projektów, które nie były aktualizowane wraz z każdą wersją programu Visual C++ od Visual C++ 6.0.

##  <a name="convert_project_file"></a> Krok 1. Konwertowanie pliku projektu.

Plik projektu dwóch stare pliki .dsw z Visual C++ 6.0, łatwo przekonwertować bez problemów wymagających dalszej uwagi. Jeden projekt jest aplikacją programu Spy ++. Druga to SpyHk, napisany w języku C, obsługi biblioteki DLL. Bardziej złożone projekty nie może uaktualnić równie łatwo, zgodnie z opisem [tutaj](../porting/visual-cpp-porting-and-upgrading-guide.md).

Po uaktualnieniu dwa projekty Nasze rozwiązanie zapoznaniu się następująco:

![Szpieguj&#43; &#43; rozwiązania](../porting/media/spyxxsolution.PNG "SpyxxSolution")

Firma Microsoft ma dwa projekty, jeden z dużą liczbą plików języka C++, a drugi biblioteki DLL, który jest zapisywany w C.

##  <a name="header_file_problems"></a> Krok 2. Problemy pliku nagłówka

Podczas tworzenia nowo przekonwertowanego projektu, jedną z pierwszych czynności, które często okazuje się, nie znaleziono plików nagłówkowych, które używa projekt.

Jeden z plików, których nie można znaleźć w programie Spy ++ był verstamp.h. Z wyszukiwania w Internecie Ustaliliśmy, to pochodzą z zestawu SDK DAO technologia przestarzałe dane. Chcemy dowiedzieć się, jakie symbole zostały użyte z tego pliku nagłówka, aby zobaczyć, czy ten plik był naprawdę potrzebne, czy te symbole zostały zdefiniowane w innym miejscu, dzięki czemu możemy komentarzami deklaracji pliku nagłówka i ponownie kompilowana. Okazuje się tylko jeden symbol, który jest potrzebny w VER_FILEFLAGSMASK.

```Output
1>C:\Program Files (x86)\Windows Kits\8.1\Include\shared\common.ver(212): error RC2104: undefined keyword or key name: VER_FILEFLAGSMASK
```

Najprostszym sposobem znalezienia symbolu w plikach dołączonych dostępne jest użycie **Znajdź w plikach** (**Ctrl**+**Shift**+**F**) a następnie określ **Visual C++ Dołącz katalogi**. Firma Microsoft uznała, że w ntverp.h. Zastąpiliśmy verstamp.h dołączone ntverp.h i zniknął tego błędu.

##  <a name="linker_output_settings"></a> Krok 3. Ustawienie Plik_wyjściowy konsolidatora

Starsze projekty mają czasami pliki umieszczone w niekonwencjonalne lokalizacje, które mogą być przyczyną problemów po uaktualnieniu. W tym przypadku mamy do dodania `$(SolutionDir)` do **Include** ścieżkę we właściwościach projektu, aby upewnić się, że program Visual Studio można znaleźć pliki nagłówkowe, które są umieszczane w tym folderze, a nie w jednym z folderów projektu.

MSBuild narzeka, **Link.OutputFile** właściwość jest niezgodna **TargetPath** i **TargetName** wartości, wydawanie MSB8012.

```Output
warning MSB8012: TargetPath(...\spyxx\spyxxhk\.\..\Debug\SpyxxHk.dll) does not match the Linker's OutputFile property value (...\spyxx\Debug\SpyHk55.dll). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).warning MSB8012: TargetName(SpyxxHk) does not match the Linker's OutputFile property value (SpyHk55). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).
```

**Link.OutputFile** znajdują się dane wyjściowe kompilacji (EXE, DLL, na przykład) i zwykle jest zbudowany z `$(TargetDir)$(TargetName)$(TargetExt)`, podając ścieżkę, nazwa_pliku i rozszerzenia. To jest typowym błędem podczas migrowania projektów ze starego Visual C++ kompilacji narzędzia (vcbuild.exe) nowe narzędzia do kompilowania (MSBuild.exe). Ponieważ zmiana narzędzia kompilacji została wprowadzona w programie Visual Studio 2010, może wystąpić ten problem, zawsze wtedy, gdy migracja projektu pre-2010 do 2010 lub nowszej wersji. Podstawowego problemu jest, że Kreator migracji projektu nie jest aktualizowany **Link.OutputFile** wartości, ponieważ nie zawsze jest możliwe ustalenie, co jej wartość powinna być zgodnie z ustawieniami projektu. W związku z tym zazwyczaj należy ręcznie ustawić. Aby uzyskać więcej informacji, zobacz ten [wpis](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx) na blogu Visual C++.

W tym przypadku **Link.OutputFile** ustawiono właściwość w projekcie przekonwertowanego.\Debug\Spyxx.exe i.\Release\Spyxx.exe dla Spy ++ projektu, w zależności od konfiguracji. Najlepiej pasujących, jest po prostu zastąpić te wartości zapisane na stałe za pomocą `$(TargetDir)$(TargetName)$(TargetExt)` dla **wszystkie konfiguracje**. Jeśli to nie zadziała, można dostosować w tym miejscu lub zmienić właściwości w **ogólne** sekcji, w którym te wartości są ustawiane (właściwości są **katalog wyjściowy**, **Nazwa docelowego**, i **docelowe rozszerzenie**. Należy pamiętać, że jeśli właściwość wyświetlasz używa makra, możesz wybrać **Edytuj** na liście rozwijanej, aby wyświetlić okno dialogowe, które wyświetla ostatni ciąg podstawienia — makro wprowadzone. Wszystkich dostępnych makr oraz ich bieżących wartości można wyświetlić, wybierając **makra** przycisku.

##  <a name="updating_winver"></a> Krok 4. Aktualizowanie wersji Windows docelowej

Następny błąd wskazuje, że wersja WINVER nie jest już obsługiwana w MFC. Polecenie WINVER systemu Windows XP jest 0x0501.

```Output
C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxv_w32.h(40): fatal error C1189: #error:  MFC does not support WINVER less than 0x0501.  Please change the definition of WINVER in your project properties or precompiled header.
```

Windows XP nie jest już obsługiwana przez firmę Microsoft, więc mimo, że jego celem jest dozwolony w programie Visual Studio, należy być wycofanie pomocy technicznej dla niego w swoich aplikacjach i zachęcanie użytkowników podczas wdrażania nowej wersji systemu Windows.

Aby pozbyć się błąd, należy zdefiniować WINVER, aktualizując **właściwości projektu** ustawienie Najniższa wersja systemu Windows, które obecnie ma pod kątem. Znajdź tabelę wartości dla różnych wersji Windows [tutaj](/windows/desktop/WinProg/using-the-windows-headers).

W pliku stdafx.h zawiera niektóre z tych definicji makra.

```cpp
#define WINVER       0x0500  // these defines are set so that we get the
#define _WIN32_WINNT 0x0500  // maximum set of message/flag definitions,
#define _WIN32_IE    0x0400  // from both winuser.h and commctrl.h.
```

Polecenie WINVER firma Microsoft ustawi Windows 7. Jest łatwiejsza do odczytania kodu później użycie makra dla Windows 7 (_WIN32_WINNT_WIN7) zamiast sama (0x0601) wartość.

```cpp
#define WINVER _WINNT_WIN32_WIN7 // Minimum targeted Windows version is Windows 7
```

##  <a name="linker_errors"></a> Krok 5. Błędy konsolidatora

Za pomocą tych zmian kompilacji projektu SpyHk (DLL), ale powoduje błąd konsolidatora.

```Output
LINK : warning LNK4216: Exported entry point _DLLEntryPoint@12
```

Punkt wejścia dla biblioteki DLL powinny nie można wyeksportować. Punkt wejścia jest przeznaczona tylko do wywoływana przez moduł ładujący, gdy biblioteki DLL, najpierw jest ładowany do pamięci, dlatego nie powinny być w tabeli eksportu dla innych klientów. Musimy upewnić się, że nie ma **__declspec(dllexport)** dyrektywy dołączono do niego. Spyxxhk.c, firma Microsoft musi usunąć ją z dwoma miejscami, deklaracji i definicji `DLLEntryPoint`. Nigdy nie przeprowadza warto użyć tej dyrektywy, ale poprzednie wersje kompilatora i konsolidatora nie Flaga go jako problem. Nowsze wersje konsolidator ostrzeżenie.

```cpp
// deleted __declspec(dllexport)
BOOL WINAPI DLLEntryPoint(HINSTANCE hinstDLL,DWORD fdwReason, LPVOID lpvReserved);
```

Projekt DLL języka C, SpyHK.dll, teraz kompiluje i łączy bez błędów.

##  <a name="outdated_header_files"></a> Krok 6. Więcej nieaktualne pliki nagłówkowe

W tym momencie Rozpoczniemy pracę nad główny projekt wykonywalny Spyxx.

Nie można odnaleźć kilka inne pliki include: ctl3d.h i penwin.h. Może być przydatne do wyszukiwania w Internecie w celu zidentyfikowania, co jest wliczane nagłówka, czasami dane nie jest to przydatne. Znaleźliśmy ctl3d.h było częścią Development Kit programu Exchange i zapewniono obsługę dla stylu kontrolki w Windows 95 i penwin.h odnosi się do okna Pióro obliczenia, interfejs API przestarzały. W tym przypadku możemy po prostu komentarz `#include` wiersza i przeciwdziałania niezdefiniowane symbole, ile My mieliśmy z verstamp.h. Wszystko, co odnosi się do formantów 3D lub korzystania z pióra został usunięty z projektu.

Biorąc pod uwagę projekt o wiele błędów kompilacji, które są stopniowo wyeliminowanie, nie jest realistyczne, aby znaleźć wszystkie przypadki użycia interfejsu API nieaktualne natychmiast, gdy usuniesz `#include` dyrektywy. Nie wykryliśmy ją od razu, ale raczej w pewnym momencie później dołączone jako błąd, że WM_DLGBORDER nie została zdefiniowana. Jest to w rzeczywistości po prostu jeden wiele niezdefiniowanych symboli, które pochodzą z ctl3d.h. Gdy Ustaliliśmy został on odnosi się do interfejsu API nieaktualne, firma Microsoft usunęła wszystkie odwołania w kodzie do niego.

##  <a name="updating_iostreams_code"></a> Krok 7. Aktualizowanie stary kod iostream

Następny błąd jest powszechne starego kodu C++, który używa iostream.

```Output
mstream.h(40): fatal error C1083: Cannot open include file: 'iostream.h': No such file or directory
```

Problem jest, że stary biblioteki iostreams został usunięty i zastąpiony. Mamy zastąp stare iostreams nowszej standardy.

```cpp
#include <iostream.h>
#include <strstrea.h>
#include <iomanip.h>
```

Oto zaktualizowany obejmuje:

```cpp
#include <iostream>
#include <sstream>
#include <iomanip>
```

Dzięki tej zmianie mamy problemy z `ostrstream`, który nie jest już używana. Odpowiednie zastąpienia jest ostringstream. Możemy spróbować dodać **typedef** dla `ostrstream` w celu uniknięcia modyfikacji kodu zbyt dużo przynajmniej rozpoczęcia.

```cpp
typedef std::basic_ostringstream<TCHAR> ostrstream;
```

Obecnie projekt jest kompilowany przy użyciu MBCS (wielobajtowego zestawu znaków), więc **char** jest odpowiednich danych znakowych. Jednakże, aby umożliwić łatwiejsze aktualizacji kodu Unicode UTF-16, aktualizujemy ten element, aby `TCHAR`, która jest rozpoznawana jako **char** lub **wchar_t** zależności od tego, czy **zestawznaków** w ustawieniach projektu jest właściwością MBCS lub Unicode.

Kilka fragmentów kodu, muszą zostać zaktualizowane.  Zastąpiliśmy klasy bazowej `ios` z `ios_base`, i zastąpiliśmy ostream polega na basic_ostream\<T >. Możemy dodać dwie dodatkowe definicje typów, a następnie kompiluje w tej sekcji.

```cpp
typedef std::basic_ostream<TCHAR> ostream;
typedef ios_base ios;
```

Za pomocą tych definicji typów to rozwiązanie tymczasowe. W przypadku bardziej trwałych rozwiązania firma Microsoft może zaktualizować każde odwołanie do interfejsu API nieaktualne lub zmieniono jego nazwę.

Oto następny błąd.

```Output
error C2039: 'freeze': is not a member of 'std::basic_stringbuf<char,std::char_traits<char>,std::allocator<char>>'
```

Następny problem jest to, że `basic_stringbuf` nie ma `freeze` metody. `freeze` Metoda jest używana, aby uniknąć przecieku pamięci w starym `ostream`. Nie potrzebujemy jej teraz, gdy firma Microsoft korzysta z nowym `ostringstream`. Usuniemy wywołanie `freeze`.

```cpp
//rdbuf()->freeze(0);
```

Następne dwa wystąpiły błędy w wierszach sąsiadująco. Pierwszy narzeka o używaniu `ends`, czyli starego `iostream` manipulator we/wy biblioteki, który dodaje terminator o wartości null na ciąg. Drugi z tych błędów wyjaśniono, że dane wyjściowe `str` metody nie można przypisać do wskaźnika niebędącego stałą.

```cpp
// Null terminate the string in the buffer and
// get a pointer to it.
//
*this << ends;
LPSTR psz = str();
```

```Output
2>mstream.cpp(167): error C2065: 'ends': undeclared identifier2>mstream.cpp(168): error C2440: 'initializing': cannot convert from 'std::basic_string<char,std::char_traits<char>,std::allocator<char>>' to 'LPSTR'
```

Przy użyciu nowej biblioteki strumienia `ends` nie jest potrzebna, ponieważ ciąg jest zawsze zakończony znakiem null, dzięki czemu można usunąć wiersza. Dla drugiego problemu problemu jest to, że teraz `str()` nie zwracają wskaźnik do tablicy znaków ciągu; zwraca `std::string` typu. Rozwiązanie do drugiego jest Zmień typ na `LPCSTR` i użyj `c_str()` metodę, aby zażądać wskaźnika.

```cpp
//*this << ends;
LPCTSTR psz = str().c_str();
```

Błąd, który puzzled nam od pewnego czasu podczas tego kodu.

```cpp
MOUT << _T(" chUser:'") << chUser
<< _T("' (") << (INT)(UCHAR)chUser << _T(')');
```

Makra MOUT jest rozpoznawana jako `*g_pmout` czyli obiektu typu `mstream`. `mstream` Klasa pochodzi od klasy ciąg standardowego wyjścia `std::basic_ostream<TCHAR>`. Jednak za pomocą \_T wokół literału ciągu, na którym umieściliśmy w ramach przygotowania do konwersji na format Unicode, rozdzielczość przeciążenia dla **operator <<** kończy się niepowodzeniem z następujący komunikat o błędzie:

```Output
1>winmsgs.cpp(4612): error C2666: 'mstream::operator <<': 2 overloads have similar conversions
1>  c:\source\spyxx\spyxx\mstream.h(120): note: could be 'mstream &mstream::operator <<(ios &(__cdecl *)(ios &))'
1>  c:\source\spyxx\spyxx\mstream.h(118): note: or       'mstream &mstream::operator <<(ostream &(__cdecl *)(ostream &))'
1>  c:\source\spyxx\spyxx\mstream.h(116): note: or       'mstream &mstream::operator <<(ostrstream &(__cdecl *)(ostrstream &))'
1>  c:\source\spyxx\spyxx\mstream.h(114): note: or       'mstream &mstream::operator <<(mstream &(__cdecl *)(mstream &))'
1>  c:\source\spyxx\spyxx\mstream.h(109): note: or       'mstream &mstream::operator <<(LPTSTR)'
1>  c:\source\spyxx\spyxx\mstream.h(104): note: or       'mstream &mstream::operator <<(TCHAR)'
1>  c:\source\spyxx\spyxx\mstream.h(102): note: or       'mstream &mstream::operator <<(DWORD)'
1>  c:\source\spyxx\spyxx\mstream.h(101): note: or       'mstream &mstream::operator <<(WORD)'
1>  c:\source\spyxx\spyxx\mstream.h(100): note: or       'mstream &mstream::operator <<(BYTE)'
1>  c:\source\spyxx\spyxx\mstream.h(95): note: or       'mstream &mstream::operator <<(long)'
1>  c:\source\spyxx\spyxx\mstream.h(90): note: or       'mstream &mstream::operator <<(unsigned int)'
1>  c:\source\spyxx\spyxx\mstream.h(85): note: or       'mstream &mstream::operator <<(int)'
1>  c:\source\spyxx\spyxx\mstream.h(83): note: or       'mstream &mstream::operator <<(HWND)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1132): note: or       'CDumpContext &operator <<(CDumpContext &,COleSafeArray &)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1044): note: or       'CArchive &operator <<(CArchive &,ATL::COleDateTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1042): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::COleDateTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1037): note: or       'CArchive &operator <<(CArchive &,ATL::COleDateTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1035): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::COleDateTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1030): note: or       'CArchive &operator <<(CArchive &,COleCurrency)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1028): note: or       'CDumpContext &operator <<(CDumpContext &,COleCurrency)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(955): note: or       'CArchive &operator <<(CArchive &,ATL::CComBSTR)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(951): note: or       'CArchive &operator <<(CArchive &,COleVariant)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(949): note: or       'CDumpContext &operator <<(CDumpContext &,COleVariant)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(248): note: or       'CArchive &operator <<(CArchive &,const RECT &)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(247): note: or       'CArchive &operator <<(CArchive &,POINT)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(246): note: or       'CArchive &operator <<(CArchive &,SIZE)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(242): note: or       'CDumpContext &operator <<(CDumpContext &,const RECT &)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(241): note: or       'CDumpContext &operator <<(CDumpContext &,POINT)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(240): note: or       'CDumpContext &operator <<(CDumpContext &,SIZE)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1639): note: or       'CArchive &operator <<(CArchive &,const CObject *)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1425): note: or       'CArchive &operator <<(CArchive &,ATL::CTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1423): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::CTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1418): note: or       'CArchive &operator <<(CArchive &,ATL::CTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1416): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::CTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(694): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,const char *)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(741): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(866): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,const _Elem *)'
1>          with
1>          [
1>              _Elem=wchar_t
1>          ]
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(983): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>,wchar_t[10]>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &&,const _Ty (&))'
1>          with
1>          [
1>              _Ty=wchar_t [10]
1>          ]
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(1021): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,const std::error_code &)'
1>  winmsgs.cpp(4612): note: while trying to match the argument list '(CMsgStream, const wchar_t [10])'
```

Istnieje wiele **operator <<** definicje, że ten rodzaj błędu może mieć OPORY przed. Po Przyglądając się dokładniej dostępnych przeciążeń, widzimy, że większość z nich są bez znaczenia i wyglądających dokładniej w `mstream` klasy definicji, firma Microsoft ustaliła, następującą funkcję, która uważamy, że powinna być wywoływana w tym przypadku.

```cpp
mstream& operator<<(LPTSTR psz)
{
  return (mstream&)ostrstream::operator<<(psz);
}
```

Przyczyną nie jest ona wywoływana jest literał ciągu ma typ `const wchar_t[10]` jak widać w ostatnim wierszu komunikat o błędzie długi, dlatego konwersji do wskaźnika niebędącego stałą nie jest automatyczna. Jednak ten operator nie należy modyfikować parametr wejściowy, dzięki czemu jest bardziej odpowiednia typ parametru `LPCTSTR` (`const char*` podczas kompilowania kodu jako MBCS, i `const wchar_t*` jako Unicode), a nie `LPTSTR` (`char*` podczas kompilowania kodu jako MBCS i `wchar_t*` jako Unicode). Wprowadzenie tej zmiany naprawia ten błąd.

Ten typ konwersji był dozwolony w obszarze kompilatora starsze, mniej rygorystyczne nowszą grupę zmian zgodności wymaga jednak bardziej poprawny kod.

##  <a name="stricter_conversions"></a> Krok 8. Konwersje bardziej rygorystyczne kompilatora

Możemy również otrzymać wiele błędów, jak pokazano poniżej:

```Output
error C2440: 'static_cast': cannot convert from 'UINT (__thiscall CHotLinkCtrl::* )(CPoint)' to 'LRESULT (__thiscall CWnd::* )(CPoint)'
```

Ten błąd występuje w mapie komunikatów, który jest po prostu makra:

```cpp
BEGIN_MESSAGE_MAP(CFindToolIcon, CWnd)
// other messages omitted...
ON_WM_NCHITTEST() // Error occurs on this line.
END_MESSAGE_MAP()
```

Przechodzenie do definicji to makro, zobaczymy, odwołuje się funkcja `OnNcHitTest`.

```cpp
#define ON_WM_NCHITTEST() \
{ WM_NCHITTEST, 0, 0, 0, AfxSig_l_p, \
(AFX_PMSG)(AFX_PMSGW) \
(static_cast< LRESULT (AFX_MSG_CALL CWnd::*)(CPoint) > (&ThisClass :: OnNcHitTest)) },
```

Ma problem z niezgodności we wskaźniku na typy funkcji elementu członkowskiego. Ten problem nie jest konwersja z `CHotLinkCtrl` jako typ klasy `CWnd` jako typ klasy, ponieważ jest prawidłowa konwersja pochodnych do podstawowego. Problem jest typem zwracanym: UINT programu vs. LRESULT. LRESULT jest rozpoznawany jako LONG_PTR, czyli wskaźnika 64-bitowego lub wskaźnik 32-bitowe, w zależności od typu binary docelowy, więc UINT nie konwertuje do tego typu. To nie jest niczym niezwykłym podczas uaktualniania kod napisany przed 2005, ponieważ zwracany typ wiele metod mapy wiadomości zmieniła się z UINT do LRESULT w programie Visual Studio 2005 jako część zmiany 64-bitowej zgodności. Możemy zmienić typ zwracany z UINT w poniższym kodzie na LRESULT:

```cpp
afx_msg UINT OnNcHitTest(CPoint point);
```

Po zmianie mamy następujący kod:

```cpp
afx_msg LRESULT OnNcHitTest(CPoint point);
```

Ponieważ około dziesięciu wystąpień tej funkcji w różnych klas pochodzące od CWnd, warto użyć **przejdź do definicji** (klawiatura: **F12**) i **przejdź do deklaracji** (Klawiatura: **Ctrl**+**F12**) gdy kursor znajduje się w funkcji w edytorze aby zlokalizować i przejdź do nich z **Znajdź Symbol** okna narzędzi. **Przejdź do definicji** jest zazwyczaj bardziej użyteczne dwóch. **Przejdź do deklaracji** będzie deklaracji Znajdź inne niż Definiowanie klasy deklaracji, takich jak przyjazne deklaracje klas lub przekazywać odwołania.

##  <a name="mfc_changes"></a> Krok 9. Zmiany w MFC

Następny błąd również odnosi się do typu deklaracji zmienione i występuje także w makrze.

```Output
error C2440: 'static_cast': cannot convert from 'void (__thiscall CFindWindowDlg::* )(BOOL,HTASK)' to 'void (__thiscall CWnd::* )(BOOL,DWORD)'
```

Problem jest drugi parametr `CWnd::OnActivateApp` zmieniła się z HTASK typu DWORD. Ta zmiana została wprowadzona w wersji programu Visual Studio, Visual Studio .NET 2002.

```cpp
afx_msg void OnActivateApp(BOOL bActive, HTASK hTask);
```

Mamy deklaracje OnActivateApp w klasach pochodnych odpowiednio zaktualizować w następujący sposób:

```cpp
afx_msg void OnActivateApp(BOOL bActive, DWORD dwThreadId);
```

W tym momencie możemy do skompilowania projektu. Istnieje kilka ostrzeżeń, aby trzymać się kolejności, jednak wiąże się z opcjonalnych części uaktualnienia, takich jak konwertowanie z MBCS na Unicode lub ulepszania zabezpieczeń za pomocą funkcji CRT bezpieczny.

##  <a name="compiler_warnings"></a> Krok 10. Adresowanie ostrzeżenia kompilatora

Aby uzyskać pełną listę ostrzeżeń, należy wykonać **Kompiluj wszystko ponownie** na rozwiązanie, a nie zwykłe kompilacji, tak, aby upewnić się, że wszystko, co wcześniej skompilowany zostaną ponownie skompilowane, ponieważ ostrzeżenie raportów można pobierać tylko z bieżącego Kompilacja. Inne pytania jest o akceptacji bieżący poziom ostrzeżeń lub użyj wyższy poziom ostrzeżeń.  Przenoszenie dużej ilości kodu, szczególnie poprzedni kod, za pomocą wyższy poziom ostrzeżeń może być odpowiednie.  Możesz również chcieć zaczynać domyślnym poziomem ostrzeżeń, a dopiero potem zwiększyć jej poziom ostrzeżeń, aby wyświetlić wszystkie ostrzeżenia. Jeśli używasz `/Wall`, otrzymujesz pewne ostrzeżenia w systemie plików nagłówkowych, tak wiele osób `/W4` Aby uzyskać najbardziej ostrzeżenia na kodzie bez wyświetlanie ostrzeżeń dla nagłówków systemu. Jeśli ostrzeżenia pojawienie się jako błędy, należy dodać `/WX` opcji. Te ustawienia znajdują się w **C/C++** części **właściwości projektu** okno dialogowe.

Jedną z metod w `CSpyApp` klasy generuje ostrzeżenia o funkcję, która nie jest już obsługiwana.

```cpp
void SetDialogBkColor() {CWinApp::SetDialogBkColor(::GetSysColor(COLOR_BTNFACE));}
```

To ostrzeżenie jest w następujący sposób.

```Output
warning C4996: 'CWinApp::SetDialogBkColor': CWinApp::SetDialogBkColor is no longer supported. Instead, handle WM_CTLCOLORDLG in your dialog
```

Komunikat WM_CTLCOLORDLG już został obsłużony w kodzie programu Spy ++, więc tylko wymagana zmiana została można usunąć wszystkie odwołania do `SetDialogBkColor`, który nie jest już potrzebny.

Następne ostrzeżenie była prosta rozwiązać problem, zakomentowując nazwę zmiennej. Otrzymaliśmy następujące ostrzeżenie:

```Output
warning C4456: declaration of 'lpszBuffer' hides previous local declaration
```

Kod, który generuje ten obejmuje makra.

```cpp
DECODEPARM(CB_GETLBTEXT)
{
  P2WPOUT();

  P2LPOUTPTRSTR;
  P2IFDATA()
  {
    PARM(lpszBuffer, PPACK_STRINGORD, ED2);

    INDENT();

    P2IFISORD(lpszBuffer)
    {
      P2OUTORD(lpszBuffer);
    }
    else
    {
      PARM(lpszBuffer, LPTSTR, ED2);
      P2OUTS(lpszBuffer);
    }
  }
}
```

Intensywne użycie makra, tak jak w tym kodzie zwykle uczynić kod trudniejszym do zachowania. W tym przypadku dostępne są następujące makra deklaracje zmiennych. PARAMETR makro jest zdefiniowany następująco:

```cpp
#define PARM(var, type, src)type var = (type)src
```

W związku z tym `lpszBuffer` pobiera zadeklarowana zmienna dwa razy w tej samej funkcji. Nie jest tym straightfoward, aby rozwiązać ten problem, jakim byłaby, jeśli kod nie była używana makra (po prostu usuń drugi deklaracji typu). Po wykonaniu, mamy niefortunne wybór konieczności zdecyduj, czy chcesz ponownie pisać kodu makra jako zwykły kod (zadanie żmudnym i prawdopodobnie obarczone ryzykiem błędów) lub wyłącz ostrzeżenia.

W tym przypadku możemy zoptymalizowany pod kątem Aby wyłączyć ostrzeżenia. Można to zrobić, dodając pragmy w następujący sposób:

```cpp
#pragma warning(disable : 4456)
```

Po wyłączeniu ostrzeżenie, możesz chcieć ograniczyć, wyłączając efektu tylko kod, generuje ostrzeżenie, aby uniknąć pomijanie ostrzeżenia, gdy może on zawierają przydatne informacje. Możemy dodać kod, aby przywrócić ostrzeżenia zaraz po wierszu, który tworzy go lub jeszcze lepiej, ponieważ ostrzeżenie to pojawia się w makrze, należy użyć **__pragma** słowo kluczowe, które działa w makrach (`#pragma` nie działa w makrach).

```cpp
#define PARM(var, type, src)__pragma(warning(disable : 4456))  \
type var = (type)src \
__pragma(warning(default : 4456))
```

Następne ostrzeżenie wymaga niektóre wersje kodu. Win32 API `GetVersion` (i `GetVersionEx`) jest przestarzały.

```Output
warning C4996: 'GetVersion': was declared deprecated
```

Poniższy kod przedstawia sposób uzyskiwania wersji.

```cpp
// check Windows version and set m_bIsWindows9x/m_bIsWindows4x/m_bIsWindows5x flags accordingly.
DWORD dwWindowsVersion = GetVersion();
```

To następuje duże ilości kodu, która sprawdza, czy wartość dwWindowsVersion, aby ustalić, czy jest uruchomiony na Windows 95 i wersji systemu Windows NT. Ponieważ jest to wszystkie przestarzałe, możemy usunąć kod oraz dotyczącej wszelkie odwołania do tych zmiennych.

Artykuł [zmiany wersji systemu operacyjnego Windows 8.1 i Windows Server 2012 R2](https://msdn.microsoft.com/library/windows/desktop/dn302074.aspx) opisano tę sytuację.

Brak metody `CSpyApp` klasy, które zbadać wersję systemu operacyjnego: `IsWindows9x`, `IsWindows4x`, i `IsWindows5x`. Dobry punkt wyjścia jest założenie, że wersje systemu Windows, które firma Microsoft zamierza obsługiwać (Windows 7 i nowsze) są wszystkie Zamknij, aby zainteresowanym 5 Windows NT, jak daleko technologie, które są używane w tej starszej aplikacji. Korzysta z tych metod były do czynienia z ograniczeniami starszych systemów operacyjnych. Więc zmienione tych metod zwraca wartość TRUE dla `IsWindows5x` i FALSE dla pozostałych.

```cpp
BOOL IsWindows9x() {/*return(m_bIsWindows9x);*/ return FALSE;  }
BOOL IsWindows4x() {/*return(m_bIsWindows4x);*/ return FALSE;  }
BOOL IsWindows5x() {/*return(m_bIsWindows5x);*/ return TRUE;  }
```

Która pozostanie tylko kilku miejscach, w którym wewnętrznych zmiennych były używane bezpośrednio. Usunęliśmy tych zmiennych, uzyskujemy kilka błędów, które zajmują się jawnie.

```Output
error C2065: 'm_bIsWindows9x': undeclared identifier
```

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(m_bIsWindows9x || hToolhelp32 != NULL);
}
```

Firma Microsoft może Zastąp to wywołanie metody lub po prostu Przekaż wartość TRUE lub usunąć stare szczególny przypadek Windows 9 x.

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(TRUE /*!m_bIsWindows9x || hToolhelp32 != NULL*/);
}
```

Końcowe ostrzeżenie na poziomie domyślnym (3) związana z bitfield.

```Output
treectl.cpp(1656): warning C4463: overflow; assigning 1 to bit-field that can only hold values from -1 to 0
```

Kod, który wyzwala to wygląda następująco:

```cpp
m_bStdMouse = TRUE;
```

Deklaracja `m_bStdMouse` wskazuje, że jest bitfield.

```cpp
class CTreeListBox : public CListBox
{
  DECLARE_DYNCREATE(CTreeListBox)

  CTreeListBox();

  private:
  int ItemFromPoint(const CPoint& point);

  class CTreeCtl* m_pTree;
  BOOL m_bGotMouseDown : 1;
  BOOL m_bDeferedDeselection : 1;
  BOOL m_bStdMouse : 1;
```

Ten kod został napisany przed typu logicznego wbudowanych była obsługiwana w programie Visual C++. W takich kod był BOOL **typedef** dla **int**. Typ **int** jest **podpisany** typu i bitowa reprezentacja **podpisany int** jest użycie pierwszego bitu jako bitu znaku, dzięki czemu bitfield typu int może zostać zinterpretowane jako reprezentuje 0 albo -1, prawdopodobnie nie co zamierzony sposób.

Nie wiesz, patrząc na kod dlaczego są to pola bitów. Został zamiar zachować mały rozmiar obiektu lub czy istnieje wszędzie gdzie układ binarny obiektu jest używana? Zmieniliśmy je do zwykłych członków BOOL, ponieważ firma Microsoft nie może zobaczyć jakiegokolwiek powodu do użytku bitfield. Użycie pola bitów, aby zapewnić mały rozmiar obiektu nie jest gwarantowane. Zależy to od jak kompilator decydujących o typie.

Być może zastanawiasz się, jeśli przy użyciu standardowego typu **bool** przez cały czas w mogą być przydatne. Wiele stare wzorców kodu, takie jak typ BOOL zostały utworzoną do rozwiązywania problemów, które później zostały rozwiązane w standardzie języka C++, więc zmiany bool do **bool** wbudowany typ jest tylko jeden przykład takiej zmiany, należy rozważyć wykonanie tej po przekazywanie kodu do pierwotnie uruchomiona w nowej wersji.

Gdy firma Microsoft zostały omówione wszystkie ostrzeżenia, które pojawiają się na poziomie domyślnym (poziom 3) zmieniliśmy na poziomie 4, aby przechwycić kilka dodatkowych ostrzeżeń. Pierwszy pojawiają się to w następujący sposób:

```Output
warning C4100: 'nTab': unreferenced formal parameter
```

Kod, który to ostrzeżenie jest w następujący sposób.

```cpp
virtual void OnSelectTab(int nTab) {};
```

Zajmuje to nieco wystarczająco nieszkodliwe, ale ponieważ Chcieliśmy czysta kompilacja z `/W4` i `/WX` ustawiona, możemy po prostu komentarzami nazwę zmiennej równoczesnym pozostawieniu ich dla czytelności.

```cpp
virtual void OnSelectTab(int /*nTab*/) {};
```

Inne ostrzeżenia, które odebraliśmy były przydatne w przypadku ogólnych kod czyszczenia. Istnieje wiele niejawne konwersje z elementu **int** lub **unsigned int** do programu WORD (czyli element typedef dla **typ unsigned short**). Obejmują one możliwa utrata danych. W takiej sytuacji dodaliśmy rzutowanie do programu WORD.

Jest innym ostrzeżenia poziomu 4, którą mamy dla tego kodu:

```Output
warning C4211: nonstandard extension used: redefined extern to static
```

Ten problem występuje, gdy najpierw zadeklarowano zmienną **extern**, później zadeklarowana **statyczne**. Znaczenie tych dwóch specyfikatory klas magazynu jest wzajemnie wykluczających się, ale jest to dozwolone jako rozszerzeń firmy Microsoft. Potrzebowała kod będzie działał w innych kompilatorach, czy chcesz skompilować go za pomocą `/Za` (zgodność z ANSI), należy zmienić deklaracje specyfikatory klas magazynu pasujących do siebie.

##  <a name="porting_to_unicode"></a> Krok 11. Eksportowanie z MBCS na Unicode

Należy pamiętać, że w środowisku Windows, gdy mówimy Unicode, zwykle rozumie UTF-16. Inne systemy operacyjne, takie jak Linux Użyj UTF-8, ale Windows nie jest zazwyczaj. Wersja MBCS MFC została zakończona w programie Visual Studio 2013 i 2015, ale nie jest już przestarzałe w programie Visual Studio 2017. Jeśli przed wykonaniem kroku do faktycznie portu kodu MBCS na Unicode UTF-16 za pomocą programu Visual Studio 2013 lub 2015 r., firma Microsoft może być tymczasowo wyeliminować ostrzeżenia, że MBCS jest przestarzała, aby można było wykonywać inne czynności lub odłożyć, przenoszenie do momentu dogodnym momencie. Bieżący kod używa MBCS i aby kontynuować, musimy zainstalować wersję ANSI/MBCS MFC. Zamiast dużej biblioteki MFC nie jest częścią domyślnej programu Visual Studio **programowanie aplikacji klasycznych w języku C++** instalacji, więc musi ona zostać wybrana za pomocą opcjonalnych składników w Instalatorze. Zobacz [dodatek MFC MBCS DLL](../mfc/mfc-mbcs-dll-add-on.md). Gdy możesz pobrać ten program i uruchom ponownie program Visual Studio można kompilować, a także połączyć się z wersją MBCS MFC, ale wszelkiego ostrzeżenia dotyczące MBCS — Jeśli używasz programu Visual Studio 2013 lub 2015, NO_WARN_MBCS_MFC_DEPRECATION należy również dodać do listy wstępnie zdefiniowanych makra w **preprocesora** sekcji we właściwościach projektu lub na początku pliku nagłówka pliku stdafx.h lub innych wspólnego pliku nagłówkowego.

W efekcie powstał błędy konsolidatora.

```Output
fatal error LNK1181: cannot open input file 'mfc42d.lib'
```

LNK1181 występuje, ponieważ nieaktualne biblioteki statycznej wersji biblioteki mfc znajduje się na konsolidatora danych wejściowych. Nie jest to wymagane dłużej, ponieważ firma Microsoft dynamicznie łączy biblioteki MFC, musimy Usuń wszystkie biblioteki statycznej MFC z **dane wejściowe** właściwość **konsolidatora** sekcji we właściwościach projektu. Ten projekt jest również za pomocą `/NODEFAULTLIB` opcji, a zamiast tego zawiera listę wszystkich zależności biblioteki.

```
msvcrtd.lib;msvcirtd.lib;kernel32.lib;user32.lib;gdi32.lib;advapi32.lib;Debug\SpyHk55.lib;%(AdditionalDependencies)
```

Teraz Daj nam faktycznie aktualizować stary kod zestawu znaków wielobajtowych (MBCS) na Unicode. Ponieważ jest to aplikacja Windows, ściśle powiązane na platformę Windows desktop, firma Microsoft będzie portu na Unicode UTF-16, który korzysta z Windows. Jeśli piszesz kod dla wielu platform lub przenoszenie aplikacji Windows, do innej platformy, należy wziąć pod uwagę przenoszenie UTF-8, która jest powszechnie używana w innych systemach operacyjnych.

Przenoszenie Unicode UTF-16, firma Microsoft należy zdecydować, czy nadal chcemy możliwość kompilowania do MBCS, czy nie.  Jeśli chcemy mieć możliwość obsługi MBCS powinniśmy skorzystać — makro tchar — jako typ znaku, który jest rozpoznawany jako celu **char** lub **wchar_t**, w zależności od tego, czy \_MBCS lub \_UNICODE jest definiowany podczas kompilacji. Przełączanie do TCHAR i TCHAR wersje różnych interfejsów API, zamiast **wchar_t** i jego skojarzone interfejsy API oznacza, że możesz wrócić do MBCS wersję kodu poprzez definiowanie \_makro MBCS zamiast \_ UNICODE. Oprócz TCHAR istnieje wiele wersji tchar — takich jak definicje powszechnie używanych typów, makra i funkcje. Na przykład LPCTSTR zamiast LPCSTR i tak dalej. W oknie dialogowym właściwości projektu w obszarze **właściwości konfiguracji**w **ogólne** sekcji, zmień **zestaw znaków** właściwość **Użyj MBCS Zestaw znaków** do **Użyj kodowania Unicode**. To ustawienie ma wpływ na wstępnie zdefiniowane makra, które podczas kompilacji. Jest makrem UNICODE i \_makro UNICODE. Właściwość projektu ma wpływ na oba spójne. Używaj UNICODE, gdzie Użyj nagłówków Visual C++, takie jak MFC w nagłówki Windows \_UNICODE, ale jeśli jest zdefiniowana, drugi zawsze jest definiowany.

Jest dobrą [przewodnik](https://msdn.microsoft.com/library/cc194801.aspx) przenoszenie z MBCS na Unicode UTF-16 za pomocą TCHAR istnieje. Wybraliśmy tę trasę. Po pierwsze zmienimy **zestaw znaków** właściwości **zestaw znaków Unicode, użyj** i skompiluj ponownie projekt.

Niektóre miejsca w kodzie była już używana TCHAR, najwyraźniej oczekując na końcu obsługi standardu Unicode. Niektóre nie były dostępne. Przeszukaliśmy dla wystąpień CHAR, czyli **typedef** dla **char**i zastąpione większość z nich TCHAR. Ponadto firma Microsoft wyszukiwanego `sizeof(CHAR)`. Zawsze, gdy zmieniliśmy z CHAR do tchar — zwykle mieliśmy można zmienić na `sizeof(TCHAR)` ponieważ był to często używane do określenia liczby znaków w ciągu. W tym miejscu przy użyciu nieprawidłowego typu nie generuje błąd kompilatora, aby poświęcić nieco uwagi w tym przypadku zwracając.

Tego typu błędu jest bardzo częsty zaraz po przełączenie na Unicode.

```Output
error C2664: 'int wsprintfW(LPWSTR,LPCWSTR,...)': cannot convert argument 1 from 'CHAR [16]' to 'LPWSTR'
```

Poniżej przedstawiono przykładowy kod, który produkuje to:

```cpp
wsprintf(szTmp, "%d.%2.2d.%4.4d", rmj, rmm, rup);
```

Umieściliśmy \_T wokół literału ciągu, aby usunąć ten błąd.

```cpp
wsprintf(szTmp, _T("%d.%2.2d.%4.4d"), rmj, rmm, rup);
```

\_Makro T ma sprawia kompilacji literału ciągu, jako **char** ciągu lub **wchar_t** ciągu, w zależności od ustawienia MBCS lub UNICODE. Aby zamienić wszystkie ciągi zawierające \_T w programie Visual Studio, najpierw otwórz **szybkiego zamieniania** (klawiatura: **Ctrl**+**F**) pole lub  **Zamienianie w plikach** (klawiatura: **Ctrl**+**Shift**+**H**), następnie wybierz **użycia Wyrażenia regularne** pola wyboru. Wprowadź `((\".*?\")|('.+?'))` jako tekst wyszukiwania i `_T($1)` jako tekst zastępczy. Jeśli masz już \_makro T niektóre ciągi, tej procedurze zostanie dodane ponownie, a także znajdzie przypadki, w których nie chcesz, \_T, na przykład przy użyciu `#include`, dlatego najlepiej użyć **Zamień następny**zamiast **Zamień wszystkie**.

Tej określonej funkcji [wsprintf](/windows/desktop/api/winuser/nf-winuser-wsprintfa), faktycznie jest zdefiniowany w nagłówki Windows i dokumentacji, aby zaleca się, że jej nie używane, z powodu przepełnienia buforu możliwe. Nie podano rozmiaru dla `szTmp` buforu, więc nie ma możliwości dla funkcji sprawdzić, czy bufor może zawierać wszystkie dane, które ma zostać zapisana. Zobacz następną sekcję o przenoszenie do bezpiecznego CRT, w którym naprawiony inne podobne problemy. Firma Microsoft zakończył się zastąpienie go za pomocą [_stprintf_s —](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md).

Innym typowym błędem, będzie widocznych na konwersji do formatu Unicode jest to.

```Output
error C2440: '=': cannot convert from 'char *' to 'TCHAR *'
```

Kod, który go generuje jest następująca:

```cpp
pParentNode->m_szText = new char[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

Mimo że `_tcscpy` funkcja została użyta, czyli TCHAR strcpy — funkcja kopiowania ciągu, bufor, która została przydzielona był **char** buforu. Jest to prosty sposób zmienić na TCHAR.

```cpp
pParentNode->m_szText = new TCHAR[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

Podobnie zmieniliśmy LPSTR (Long wskaźnik do ciągu) i LPCSTR (Long wskaźnik ze stałym ciągiem) LPTSTR (wskaźnik długi ciąg TCHAR) i LPCTSTR (Long wskaźnik ze stałym ciągiem TCHAR) odpowiednio w błąd kompilatora. Wybraliśmy nie dokonywać takiego zastąpienia przy użyciu wyszukiwania globalnego i Zamień, ponieważ do badania oddzielnie każdą sytuację. W niektórych przypadkach **char** wyznaczony wersji, takie jak kiedy przetwarzanie niektórych Windows komunikatów, w której użyty struktury Windows, które mają **A** sufiks. W interfejsie API Windows sufiks **A** oznacza ASCII, ANSI (i ma zastosowanie również do MBCS), a sufiksem **W** oznacza, że znaki dwubajtowe lub Unicode UTF-16. Ten wzorzec nazewnictwa jest używany w nagłówkach Windows, ale możemy również przestrzegać go w kodzie programu Spy ++ podczas Musieliśmy dodać wersję Unicode, funkcji, która została już zdefiniowana w MBCS wersji.

W niektórych przypadkach firma Microsoft było zastąpienie typu do korzystania z wersji, który jest rozpoznawany jako poprawnie (WNDCLASS zamiast WNDCLASSA, na przykład).

W wielu przypadkach mieliśmy do używania wersji ogólnych (makro) interfejsu API Win32, takich jak `GetClassName` (zamiast `GetClassNameA`). W instrukcji switch procedury obsługi komunikatów, niektóre komunikaty dotyczą MBCS lub Unicode, w tych przypadkach, mieliśmy zmienić kod, aby jawnie wywołać wersji MBCS, ponieważ zastąpiliśmy objęty nazwane funkcje z **A** i **W** określonych funkcji i dodaje makro dla nazwy ogólnej, który jest rozpoznawany jako poprawny **A** lub **W** nazwę opartą na czy UNICODE jest zdefiniowana.  W wielu częściach kodu, gdy przeszliśmy do definiowania \_UNICODE, wersja W jest teraz wybrane nawet wtedy, gdy **A** wersja to, co chcę teraz.

Istnieje kilka miejsc, gdy miały stosowanie specjalnych działań do wykonania. Jakiekolwiek wykorzystanie `WideCharToMultiByte` lub `MultiByteToWideChar` mogą wymagać bliżej. Poniżej przedstawiono przykładowy gdzie `WideCharToMultiByte` było ono używane.

```cpp
BOOL C3dDialogTemplate::GetFont(CString& strFace, WORD& nFontSize)
{
  ASSERT(m_hTemplate != NULL);

  DLGTEMPLATE* pTemplate = (DLGTEMPLATE*)GlobalLock(m_hTemplate);
  if ((pTemplate->style & DS_SETFONT) == 0)
  {
    GlobalUnlock(m_hTemplate);
    return FALSE;
  }

  BYTE* pb = GetFontSizeField(pTemplate);
  nFontSize = *(WORD*)pb;
  pb += sizeof (WORD);
  WideCharToMultiByte(CP_ACP, 0, (LPCWSTR)pb, -1,
  strFace.GetBufferSetLength(LF_FACESIZE), LF_FACESIZE, NULL, NULL);
  strFace.ReleaseBuffer();
  GlobalUnlock(m_hTemplate);
  return TRUE;
}
```

Aby rozwiązać ten problem, mieliśmy zrozumienie przyczyn jest to możliwe było skopiować szeroki ciąg znaków reprezentujący nazwę czcionki do wewnętrznego buforu elementu `CString`, `strFace`. Wymaga to nieco inny kod dla znaków wielobajtowych `CString` ciągi, jak w przypadku szerokich `CString` ciągów, dlatego dodaliśmy `#ifdef` w tym przypadku.

```cpp
#ifdef _MBCS
WideCharToMultiByte(CP_ACP, 0, (LPCWSTR)pb, -1,
strFace.GetBufferSetLength(LF_FACESIZE), LF_FACESIZE, NULL, NULL);
strFace.ReleaseBuffer();
#else
wcscpy(strFace.GetBufferSetLength(LF_FACESIZE), (LPCWSTR)pb);
strFace.ReleaseBuffer();
#endif
```

Oczywiście, a nie z `wcscpy` naprawdę powinniśmy skorzystać w `wcscpy_s`, bardziej bezpieczna wersja. Następna sekcja rozwiązuje ten problem.

W celu sprawdzenia naszej pracy, firma Microsoft należy zresetować **zestaw znaków** do **zestaw znaków wielobajtowych użyj** i upewnij się, że kod nadal będzie się kompilować przy użyciu MBCS, jak również Unicode. Needless, że przebieg pełnego testu powinien być wykonywany ponownej kompilacji aplikacji po tych zmian.

W naszych pracach za pomocą tego rozwiązania programu Spy ++, jaki zajęło około dwóch dni roboczych dla średniej dewelopera języka C++ przekonwertować kod Unicode. Który nie zawiera retesting czasu.

##  <a name="porting_to_secure_crt"></a> Krok 12. Przenoszenie do użycia zabezpieczenia CRT

Przenoszenie kodu do użycia bezpieczne wersje (wersje **_s** sufiks) funkcje CRT jest dalej. W tym przypadku jest ogólną strategią zastąpić funkcji z **_s** wersji, a następnie, zwykle, Dodaj parametry rozmiar wymaganego buforu dodatkowe. W wielu przypadkach to proste, ponieważ rozmiar jest znany. W innych przypadkach, w których rozmiar nie jest natychmiast dostępna, jest konieczne dodanie dodatkowych parametrów do funkcji, która używa funkcji CRT lub prawdopodobnie zużycie buforu miejsca docelowego i zobacz jakie odpowiedniego rozmiaru obowiązują limity.

Visual C++ zapewnia sposobem, aby ułatwić uzyskiwanie kodzie bezpieczeństwa bez dodawania tyle parametrów rozmiar, a przy użyciu przeciążenia szablonu. Ponieważ te przeciążenia szablonów, są one dostępne podczas kompilowania kodu jako C++, nie się C. Spyxxhk projekt C, aby lewy nie będzie działać w tym.  Jednak nie jest Spyxx i używamy lewy. Lewy jest dodać taki wiersz w miejscu, gdzie go zostanie skompilowany w każdym pliku projektu, takie jak w pliku stdafx.h:

```cpp
#define _CRT_SECURE_TEMPLATE_OVERLOADS 1
```

Po zdefiniowaniu, zawsze wtedy, gdy rozmiar buforu jest tablicą, a nie wskaźnik surowy jego rozmiar jest wnioskowany z typu tablicy i używany jako parametr rozmiaru bez konieczności dostarczenia go. Która pozwala zmniejszyć złożoność ponowne napisanie kodu. Nadal trzeba zastąpić nazwy funkcji za pomocą **_s** wersji, ale często może odbywać się za pomocą wyszukiwania oraz operację zamiany.

Zmienić wartości zwrócone przez niektóre funkcje. Na przykład `_itoa_s` (i `_itow_s` i makra `_itot_s`) zwraca kod błędu (`errno_t`), zamiast ciągu. Dlatego w tych przypadkach należy przenieść wywołanie `_itoa_s` na oddzielnym wierszy i zastąp go z identyfikatorem buforu.

Niektóre typowe przypadki: dla `memcpy`, podczas przełączania `memcpy_s`, dodaliśmy często rozmiar struktury kopiowane do. Podobnie dla większości ciągów i bufory rozmiaru tablicy lub buforu łatwo zależy od deklaracji buforu lub znajdując, gdzie pierwotnie został przydzielony rozmiar buforu. W niektórych sytuacjach należy określić sposób dużych bufora jest aktualnie dostępna i jeśli te informacje nie są dostępne w zakresie funkcji, który jest modyfikowany, powinny zostać dodane jako dodatkowy parametr i należy zmodyfikować kod wywołujący, aby Podaj informacje.

Za pomocą tych metod zajęło to około pół dnia można przekonwertować kod, aby użyć bezpieczne funkcje CRT. Jeśli nie zdecydujesz się na przeciążenia szablonu, aby ręcznie dodać parametry rozmiar, będzie ona prawdopodobnie należy wykonać dwa razy lub trzy razy więcej czasu.

##  <a name="deprecated_forscope"></a> Krok 13. /Zc:forScope-jest przestarzała.

Od czasu Visual C++ 6.0 kompilator jest zgodny z bieżącym standardem, co ogranicza zakres zmiennych zadeklarowanych w pętli do zakresu pętli. Opcja kompilatora [/Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) (**Wymuszaj zgodność w zakresie pętli for** we właściwościach projektu) określa, czy jest to raportowane jako błąd. Firma Microsoft należy zaktualizować naszego kodu jako zgodność, a następnie dodaj deklaracje tylko poza pętlę. Aby uniknąć wprowadzania zmian w kodzie, można zmienić to ustawienie w **języka** sekcji właściwości projektu C++, aby `No (/Zc:forScope-)`. Jednak należy pamiętać, że `/Zc:forScope-` może zostać usunięte w przyszłej wersji programu Visual C++, więc po pewnym czasie kodu będą musieli zmienić są zgodne ze standardem.

Te problemy są stosunkowo łatwo rozwiązać, ale w zależności od kodu, to może wpłynąć na duże ilości kodu. Oto typowy problem.

```cpp
int CPerfTextDataBase::NumStrings(LPCTSTR mszStrings) const
{
  for (int n = 0; mszStrings[0] != 0; n++)
  mszStrings = _tcschr(mszStrings, 0) + 1;
  return(n);
}
```

Powyższy kod generuje błąd:

```Output
'n': undeclared identifier
```

Dzieje się tak, ponieważ kompilator jest przestarzała opcję kompilatora, która może kod, który nie jest już zgodny ze standardem C++. W standardzie zadeklarowanie zmiennej wewnątrz pętli, ogranicza jego zakres do pętli, więc powszechną praktyką użycia licznika pętli, poza pętlą wymagają, że deklaracja licznika także przenosić poza pętlę, jak w poniższym kodzie poprawione :

```cpp
int CPerfTextDataBase::NumStrings(LPCTSTR mszStrings) const
{
  int n;
  for (n = 0; mszStrings[0] != 0; n++)
  mszStrings = _tcschr(mszStrings, 0) + 1;
  return(n);
}
```

## <a name="summary"></a>Podsumowanie

Przenoszenie programu Spy ++ od oryginalnego kodu Visual C++ 6.0 najnowszą wersję kompilatora trwało około 20 godzin kodowania czasu w ciągu około tygodnia. Możemy uaktualnić bezpośrednio w ramach ośmiu wersjach produktu programu Visual Studio 6.0 do programu Visual Studio 2015. Teraz jest to zalecane podejście do wszystkich uaktualnień w projektach dużych i małych.

## <a name="see-also"></a>Zobacz też

[Przenoszenie i uaktualnianie: Przykłady i analizy przypadków](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Poprzednie analiza przypadku: narzędzie Spy modelu COM](../porting/porting-guide-com-spy.md)
