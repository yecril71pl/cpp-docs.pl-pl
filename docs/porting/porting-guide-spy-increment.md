---
title: 'Przewodnik przenoszenia: Narzędzie Spy++'
ms.date: 10/23/2019
ms.assetid: e558f759-3017-48a7-95a9-b5b779d5e51d
ms.openlocfilehash: 5505e0dbf23dd02f4ae5924ff4f2bacff3f11eea
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416985"
---
# <a name="porting-guide-spy"></a>Przewodnik przenoszenia: Narzędzie Spy++

Ta analiza przypadku portów została zaprojektowana z myślą o tym, co jest typowym projektem portów, rodzajami problemów, które mogą wystąpić, a także z niektórymi ogólnymi wskazówkami i wskazówki dotyczące rozwiązywania problemów z portami. Nie jest to jednak ostateczny Przewodnik dotyczący przenoszenia, ponieważ środowisko przenoszenia projektu jest zależne od konkretnego kodu.

## <a name="spy"></a>Spy++

Program Spy + + jest szeroko używanym graficznym interfejsem użytkownika narzędzia diagnostycznego dla pulpitu systemu Windows, który udostępnia wszystkie informacje o elementach interfejsu użytkownika na pulpicie systemu Windows. Pokazuje kompletną hierarchię systemu Windows i zapewnia dostęp do metadanych każdego okna i kontroli. Ta przydatna aplikacja jest dostarczana z programem Visual Studio przez wiele lat. Znaleźliśmy starą wersję, która była ostatnio skompilowana w programie Visual C++ 6,0 i przeprowadzono jej port do programu visual Studio 2015. Środowisko dla programu Visual Studio 2017 lub Visual Studio 2019 powinno być niemal identyczne.

Uważamy, że jest to typowe dla portów aplikacji klasycznych systemu Windows korzystających z MFC i Win32 API, szczególnie w przypadku starych projektów, które nie zostały zaktualizowane przy użyciu poszczególnych C++ wersji wizualizacji od Visual C++ 6,0.

##  <a name="convert_project_file"></a>Krok 1. Konwertowanie pliku projektu.

Plik projektu, dwa stare pliki DSW z programu Visual C++ 6,0, można łatwo skonwertować bez problemów, które wymagają dalszej uwagi. Jeden projekt jest aplikacją programu Spy + +. Druga to SpyHk, zapisywana w C, Pomocnicza biblioteka DLL. Bardziej złożone projekty mogą nie zostać uaktualnione tak szybko, jak opisano [tutaj](../porting/visual-cpp-porting-and-upgrading-guide.md).

Po uaktualnieniu dwóch projektów nasze rozwiązanie wygląda następująco:

![Rozwiązanie Spy&#43; &#43;](../porting/media/spyxxsolution.PNG "Rozwiązanie Spy&#43; &#43;")

Mamy dwa projekty, jeden z dużą liczbą C++ plików, a inna dll, która jest zapisywana w C.

##  <a name="header_file_problems"></a>Krok 2. Problemy z plikiem nagłówka

Po utworzeniu nowo przekonwertowanego projektu jedną z pierwszych rzeczy, które często się znajdują, jest to, że nie można odnaleźć plików nagłówkowych używanych przez projekt.

Jeden z plików, których nie można znaleźć w programie Spy + +, to verstamp. h. W wyszukiwaniu internetowym firma Microsoft ustaliła, że pochodzi ona z zestawu DAO SDK, czyli przestarzałej technologii danych. Chcemy dowiedzieć się, jakie symbole zostały użyte z tego pliku nagłówka, aby sprawdzić, czy ten plik był rzeczywiście wymagany lub czy te symbole zostały zdefiniowane w innym miejscu, dlatego komentarz do deklaracji pliku nagłówka i ponownej kompilacji. Spowoduje to, że jest wymagany tylko jeden symbol, VER_FILEFLAGSMASK.

```Output
1>C:\Program Files (x86)\Windows Kits\8.1\Include\shared\common.ver(212): error RC2104: undefined keyword or key name: VER_FILEFLAGSMASK
```

Najprostszym sposobem znalezienia symbolu w dostępnych plikach dołączania jest użycie **Znajdź w plikach** (**Ctrl**+**SHIFT**+**F**) i określanie **katalogów dołączania wizualizacji C++** . Znaleźliśmy ją w ntverp. h. Zamieniono verstamp. h na ntverp. h i ten błąd znika.

##  <a name="linker_output_settings"></a>Krok 3. Ustawienie Plik_wyjściowy konsolidatora

Starsze projekty czasami mają pliki umieszczane w niekonwencjonalnych lokalizacjach, które mogą spowodować problemy po uaktualnieniu. W takim przypadku należy dodać `$(SolutionDir)` do ścieżki **dołączania** we właściwościach projektu, aby upewnić się, że program Visual Studio może znaleźć w tym miejscu pliki nagłówkowe, a nie w jednym z folderów projektu.

Program MSBuild zgłasza, że właściwość **link. plik_wyjściowy** nie pasuje do wartości **TargetPath** i **TargetName** , wystawiając MSB8012.

```Output
warning MSB8012: TargetPath(...\spyxx\spyxxhk\.\..\Debug\SpyxxHk.dll) does not match the Linker's OutputFile property value (...\spyxx\Debug\SpyHk55.dll). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).warning MSB8012: TargetName(SpyxxHk) does not match the Linker's OutputFile property value (SpyHk55). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).
```

**Link. plik_wyjściowy** to dane wyjściowe kompilacji (exe, DLL, na przykład) i są zwykle konstruowane z `$(TargetDir)$(TargetName)$(TargetExt)`, podając ścieżkę, nazwę pliku i rozszerzenie. Jest to typowy błąd podczas migrowania projektów ze starego narzędzia do C++ kompilacji wizualizacji (vcbuild. exe) do nowego narzędzia kompilacji (MSBuild. exe). Ze względu na to, że narzędzie kompilacji zmieniło się w programie Visual Studio 2010, ten problem może wystąpić po każdym przeprowadzeniu migracji projektu poprzedzającego 2010 do wersji 2010 lub nowszej. Podstawowy problem polega na tym, że Kreator migracji projektu nie aktualizuje wartości **link. plik_wyjściowy** , ponieważ nie zawsze jest możliwe ustalenie, jaka wartość powinna być oparta na innych ustawieniach projektu. W związku z tym zazwyczaj trzeba ustawić ją ręcznie. Aby uzyskać więcej informacji, zobacz ten [wpis](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/) w blogu C++ wizualnym.

W takim przypadku Właściwość **link. plik_wyjściowy** w przekonwertowanym projekcie została ustawiona na .\Debug\Spyxx.exe i .\Release\Spyxx.exe dla projektu Spy + +, w zależności od konfiguracji. Najlepszym trafieniem jest po prostu zastąpienie tych wartości stałe `$(TargetDir)$(TargetName)$(TargetExt)` dla **wszystkich konfiguracji**. Jeśli to nie zadziała, można dostosować się z tego miejsca lub zmienić właściwości w sekcji **Ogólne** , w której są ustawione wartości (właściwości są **katalogiem wyjściowym**, **nazwą docelową**i **rozszerzeniem docelowym**. Pamiętaj, że jeśli właściwość, którą przeglądasz, używa makr, możesz wybrać opcję **Edytuj** na liście rozwijanej, aby wyświetlić okno dialogowe, w którym jest wyświetlany ostatni ciąg z utworzonymi podstawieniami makr. Możesz wyświetlić wszystkie dostępne makra i ich bieżące wartości, wybierając przycisk **makra** .

##  <a name="updating_winver"></a>Krok 4. Aktualizowanie docelowej wersji systemu Windows

Następny błąd wskazuje, że wersja programu WINVER nie jest już obsługiwana w MFC. W programie WINVER dla systemu Windows XP jest 0x0501.

```Output
C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxv_w32.h(40): fatal error C1189: #error:  MFC does not support WINVER less than 0x0501.  Please change the definition of WINVER in your project properties or precompiled header.
```

System Windows XP nie jest już obsługiwany przez firmę Microsoft, więc mimo że jest to dozwolone w programie Visual Studio, należy wypróbować wsparcie dla niego w swoich aplikacjach i zachęcać użytkowników do przyjmowania nowych wersji systemu Windows.

Aby usunąć błąd, zdefiniuj polecenie WINVER, aktualizując ustawienie **właściwości projektu** do najmniejszej wersji systemu Windows, która jest obecnie przeznaczona do użycia. W [tym miejscu](/windows/win32/WinProg/using-the-windows-headers)znajdziesz tabelę wartości dla różnych wersji systemu Windows.

Plik *stdafx. h* zawiera niektóre z tych definicji makr.

```cpp
#define WINVER       0x0500  // these defines are set so that we get the
#define _WIN32_WINNT 0x0500  // maximum set of message/flag definitions,
#define _WIN32_IE    0x0400  // from both winuser.h and commctrl.h.
```

WINVER ustawimy na system Windows 7. Można łatwiej odczytywać kod później, jeśli używasz makra dla systemu Windows 7 (_WIN32_WINNT_WIN7), a nie samego wartości (0x0601).

```cpp
#define WINVER _WINNT_WIN32_WIN7 // Minimum targeted Windows version is Windows 7
```

##  <a name="linker_errors"></a>Krok 5. Błędy konsolidatora

Po wprowadzeniu tych zmian projekt SpyHk (DLL) kompiluje, ale generuje błąd konsolidatora.

```Output
LINK : warning LNK4216: Exported entry point _DLLEntryPoint@12
```

Nie należy eksportować punktu wejścia dla biblioteki DLL. Punkt wejścia jest przeznaczony tylko do wywoływania przez moduł ładujący, gdy biblioteka DLL jest najpierw ładowana do pamięci, dlatego nie powinna znajdować się w tabeli eksportu, która jest przeznaczona dla innych obiektów wywołujących. Wystarczy upewnić się, że nie ma do niej dołączonej dyrektywy **__declspec (dllexport)** . W Spyxxhk. c musimy usunąć ją z dwóch miejsc, deklaracji i definicji `DLLEntryPoint`. Nigdy nie ma sensu używania tej dyrektywy, ale poprzednie wersje konsolidatora i kompilatora nie oflagują go jako problemu. Nowsze wersje konsolidatora dają ostrzeżenie.

```cpp
// deleted __declspec(dllexport)
BOOL WINAPI DLLEntryPoint(HINSTANCE hinstDLL,DWORD fdwReason, LPVOID lpvReserved);
```

Projekt C DLL, SpyHK. dll, teraz kompiluje i łączy bez błędu.

##  <a name="outdated_header_files"></a>Krok 6. Więcej nieaktualnych plików nagłówkowych

W tym momencie rozpoczynamy pracę nad głównym projektem wykonywalnym, spyxx.

Nie można znaleźć kilku innych plików dołączanych: ctl3d. h i penwin. h. Mimo że pomocne może być przeszukanie Internetu w celu zidentyfikowania elementów uwzględnionych w nagłówku, czasami te informacje nie są przydatne. Znaleźliśmy, że ctl3d. h była częścią zestawu Exchange Development Kit i zapewnia obsługę pewnego stylu formantów w systemie Windows 95, a penwin. h odnosi się do przetwarzania piórem okien, przestarzałego interfejsu API. W tym przypadku po prostu dodamy komentarz do linii `#include` i zachodzimy z niezdefiniowanymi symbolami, tak jak w verstamp. h. Wszystkie elementy, które odnoszą się do kontrolek 3D lub obliczeń pióra, zostały usunięte z projektu.

W przypadku projektu z wieloma błędami kompilacji, które stopniowo eliminują, nie jest to realistyczne, aby znaleźć wszystkie zastosowania nieaktualnego interfejsu API natychmiast po usunięciu dyrektywy `#include`. Nie wykryjemy go natychmiast, ale zamiast tego w późniejszym momencie wystąpił błąd, który WM_DLGBORDER był niezdefiniowany. W rzeczywistości jest tylko jeden niezdefiniowany symbol, który pochodzi z ctl3d. h. Po ustaleniu, że odnosi się on do nieaktualnego interfejsu API, usunęliśmy wszystkie odwołania w kodzie.

##  <a name="updating_iostreams_code"></a>Krok 7. Aktualizowanie starego kodu iostreams

Następny błąd jest typowy dla starego C++ kodu, który używa iostreams.

```Output
mstream.h(40): fatal error C1083: Cannot open include file: 'iostream.h': No such file or directory
```

Problem polega na tym, że stara Biblioteka iostreams została usunięta i zastąpiona. Musimy zastąpić stary iostreams nowszymi standardami.

```cpp
#include <iostream.h>
#include <strstrea.h>
#include <iomanip.h>
```

Dostępne są następujące aktualizacje:

```cpp
#include <iostream>
#include <sstream>
#include <iomanip>
```

W przypadku tej zmiany mamy problemy z `ostrstream`, które nie są już używane. Odpowiednim zastąpieniem jest ostringstream —. Spróbujemy dodać **element typedef** dla `ostrstream`, aby uniknąć zbyt dużej modyfikacji kodu, co najmniej jako początek.

```cpp
typedef std::basic_ostringstream<TCHAR> ostrstream;
```

Obecnie projekt został skompilowany przy użyciu MBCS (zestaw znaków wielobajtowych), więc **char** jest odpowiednim typem danych znakowych. Aby jednak ułatwić aktualizację kodu UTF-16 Unicode, zaktualizujemy ten element do `TCHAR`, który jest rozpoznawany jako **char** lub **wchar_t** w zależności od tego, czy właściwość **zestawu znaków** w ustawieniach projektu jest ustawiona na MBCS czy Unicode.

Należy zaktualizować kilka innych fragmentów kodu.  Zamienimy klasę bazową `ios` z `ios_base`, a ostream zastępujemy basic_ostream\<T >. Dodamy dwa dodatkowe definicje typów i ta sekcja zostanie skompilowana.

```cpp
typedef std::basic_ostream<TCHAR> ostream;
typedef ios_base ios;
```

Korzystanie z tych typów typedef jest tylko tymczasowym rozwiązaniem. W przypadku bardziej trwałego rozwiązania możemy zaktualizować każde odwołanie do nazwy lub nieaktualnego interfejsu API.

Poniżej przedstawiono następny błąd.

```Output
error C2039: 'freeze': is not a member of 'std::basic_stringbuf<char,std::char_traits<char>,std::allocator<char>>'
```

Następny problem polega na tym, że `basic_stringbuf` nie ma metody `freeze`. Metoda `freeze` służy do zapobiegania wyciekowi pamięci w starym `ostream`. Nie potrzebujemy teraz, aby korzystać z nowych `ostringstream`. Możemy usunąć wywołanie do `freeze`.

```cpp
//rdbuf()->freeze(0);
```

Dwa następne błędy wystąpiły w sąsiednich wierszach. Pierwszy zażalenie dotyczące używania `ends`, który jest starym Manipulator biblioteki `iostream` we/wy, który dodaje terminator o wartości null do ciągu. W drugim z tych błędów wyjaśniono, że dane wyjściowe metody `str` nie mogą być przypisane do wskaźnika niebędącego stałą.

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

Przy użyciu nowej biblioteki strumieni `ends` nie jest wymagana, ponieważ ciąg jest zawsze zakończony zerem, aby można było usunąć wiersz. W drugim problemie występuje problem polegający na tym, że teraz `str()` nie zwraca wskaźnika do tablicy znaków dla ciągu; zwraca typ `std::string`. Rozwiązaniem drugim jest zmiana typu na `LPCSTR` i użycie metody `c_str()` w celu zażądania wskaźnika.

```cpp
//*this << ends;
LPCTSTR psz = str().c_str();
```

Wystąpił błąd, który został pozostały przez nas dla elementu while w tym kodzie.

```cpp
MOUT << _T(" chUser:'") << chUser
<< _T("' (") << (INT)(UCHAR)chUser << _T(')');
```

MOUT makro rozpoznaje do `*g_pmout`, który jest obiektem typu `mstream`. Klasa `mstream` jest pochodną klasy standardowego ciągu wyjściowego, `std::basic_ostream<TCHAR>`. Jednak w przypadku \_T wokół literału ciągu, który jest przygotowywany do konwersji na Unicode, rozpoznawanie przeciążenia dla **operatora < <** kończy się niepowodzeniem z następującym komunikatem o błędzie:

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

Istnieje wiele **< operatora <** definicje, których ten rodzaj błędu może być zastraszanie. Po dokładniejszym zajrzeć od dostępnych przeciążeń można zobaczyć, że większość z nich nie jest istotna i że dokładniej jest w definicji klasy `mstream`, zidentyfikowano następującą funkcję, która zdaniem powinna zostać wywołana w tym przypadku.

```cpp
mstream& operator<<(LPTSTR psz)
{
  return (mstream&)ostrstream::operator<<(psz);
}
```

Powód, dla którego nie jest wywoływany, jest spowodowany tym, że literał ciągu ma typ `const wchar_t[10]`, jak widać w ostatnim wierszu tego długiego komunikatu o błędzie, dlatego konwersja na wskaźnik niestały nie jest automatyczna. Jednak operator nie powinien modyfikować parametru wejściowego, więc bardziej odpowiedni typ parametru jest `LPCTSTR` (`const char*` podczas kompilowania jako MBCS, i `const wchar_t*` jako Unicode), a nie `LPTSTR` (`char*` podczas kompilowania jako MBCS i `wchar_t*` jako Unicode). Wprowadzenie tej zmiany spowoduje usunięcie tego błędu.

Ten typ konwersji jest dozwolony w ramach starszego, mniej rygorystycznego kompilatora, ale więcej najnowszych zmian zgodności wymaga bardziej poprawnego kodu.

##  <a name="stricter_conversions"></a>Krok 8. Bardziej rygorystyczne konwersje kompilatora

Występuje również wiele błędów, takich jak następujące:

```Output
error C2440: 'static_cast': cannot convert from 'UINT (__thiscall CHotLinkCtrl::* )(CPoint)' to 'LRESULT (__thiscall CWnd::* )(CPoint)'
```

Ten błąd występuje w mapie komunikatów, która jest po prostu makro:

```cpp
BEGIN_MESSAGE_MAP(CFindToolIcon, CWnd)
// other messages omitted...
ON_WM_NCHITTEST() // Error occurs on this line.
END_MESSAGE_MAP()
```

Po przejściu do definicji tego makra zobaczymy, że odwołuje się do `OnNcHitTest`funkcji.

```cpp
#define ON_WM_NCHITTEST() \
{ WM_NCHITTEST, 0, 0, 0, AfxSig_l_p, \
(AFX_PMSG)(AFX_PMSGW) \
(static_cast< LRESULT (AFX_MSG_CALL CWnd::*)(CPoint) > (&ThisClass :: OnNcHitTest)) },
```

Problem należy wykonać z niezgodnością we wskaźnikach do typów funkcji Członkowskich. Problem nie jest konwersją z `CHotLinkCtrl` jako typ klasy do `CWnd` jako typ klasy, ponieważ jest to prawidłowa konwersja pochodna-podstawowa. Problem jest typem zwracanym: UINT a LRESULT. LRESULT jest rozpoznawana jako LONG_PTR, który jest wskaźnikiem 64-bitowym lub 32-bitowym, w zależności od docelowego typu binarnego, więc UINT nie jest konwertowany na ten typ. Jest to nietypowe w przypadku uaktualniania kodu pisanego przed 2005, ponieważ typ zwracany wielu metod mapy komunikatów zmienił się z UINT na LRESULT w programie Visual Studio 2005 w ramach aktualizacji zgodności z 64-bitową. Zmienimy Typ zwracany z UINT w poniższym kodzie na LRESULT:

```cpp
afx_msg UINT OnNcHitTest(CPoint point);
```

Po zmianie mamy następujący kod:

```cpp
afx_msg LRESULT OnNcHitTest(CPoint point);
```

Ponieważ istnieje około dziesięciu wystąpień tej funkcji w różnych klasach pochodzących od CWnd, warto użyć **Przejdź do definicji** (klawiatura: **F12**) i **Przejdź do deklaracji** (klawiatura: **Ctrl**+**F12**), gdy kursor znajduje się w funkcji w edytorze, aby je zlokalizować, i przejdź do nich w oknie narzędzia **Znajdowanie symboli** . **Przechodzenie do definicji** jest zazwyczaj bardziej przydatne w przypadku obu tych elementów. Polecenie **Przejdź do deklaracji** będzie znajdować deklaracje inne niż definicje klasy definiującej, takie jak zaprzyjaźnione deklaracje klas lub odwołania do przodu.

##  <a name="mfc_changes"></a>Krok 9. Zmiany MFC

Następny błąd dotyczy również zmienionego typu deklaracji i występuje również w makrze.

```Output
error C2440: 'static_cast': cannot convert from 'void (__thiscall CFindWindowDlg::* )(BOOL,HTASK)' to 'void (__thiscall CWnd::* )(BOOL,DWORD)'
```

Problem polega na tym, że drugi parametr `CWnd::OnActivateApp` zmieniony z HTASK na DWORD. Ta zmiana nastąpiła w wersji 2002 programu Visual Studio, Visual Studio .NET.

```cpp
afx_msg void OnActivateApp(BOOL bActive, HTASK hTask);
```

Konieczne jest zaktualizowanie deklaracji OnActivateApp w klasach pochodnych w następujący sposób:

```cpp
afx_msg void OnActivateApp(BOOL bActive, DWORD dwThreadId);
```

W tym momencie możemy skompilować projekt. Istnieje kilka ostrzeżeń, które mogą być wykonywane przez program, ale istnieją opcjonalne części uaktualnienia, takie jak konwertowanie z MBCS na Unicode lub zwiększanie bezpieczeństwa przy użyciu funkcji Secure CRT.

##  <a name="compiler_warnings"></a>Krok 10. Rozwiązywanie ostrzeżeń kompilatora

Aby uzyskać pełną listę ostrzeżeń, należy wykonać ponowną kompilację **wszystkich** rozwiązań w rozwiązaniu zamiast zwykłej kompilacji, aby upewnić się, że wszystkie skompilowane wcześniej elementy zostaną ponownie skompilowane, ponieważ tylko raporty z bieżącej kompilacji są wyświetlane. Innym pytaniem jest zaakceptowanie bieżącego poziomu ostrzeżeń lub użycie wyższego poziomu ostrzeżeń.  W przypadku przenoszenia dużej ilości kodu, szczególnie starego kodu, może być odpowiednie użycie wyższego poziomu ostrzegawczego.  Możesz również zacząć od domyślnego poziomu ostrzeżeń, a następnie zwiększyć poziom ostrzeżeń w celu uzyskania wszystkich ostrzeżeń. Jeśli używasz `/Wall`, otrzymujesz ostrzeżenia w plikach nagłówkowych systemu, więc wiele osób używa `/W4`, aby uzyskać najwięcej ostrzeżeń dotyczących kodu bez otrzymywania ostrzeżeń dotyczących nagłówków systemowych. Jeśli chcesz, aby ostrzeżenia były wyświetlane jako błędy, Dodaj opcję `/WX`. Te ustawienia znajdują się w sekcji **C/C++**  okna dialogowego **właściwości projektu** .

Jedna z metod w klasie `CSpyApp` generuje ostrzeżenie o funkcji, która nie jest już obsługiwana.

```cpp
void SetDialogBkColor() {CWinApp::SetDialogBkColor(::GetSysColor(COLOR_BTNFACE));}
```

Ostrzeżenie jest następujące.

```Output
warning C4996: 'CWinApp::SetDialogBkColor': CWinApp::SetDialogBkColor is no longer supported. Instead, handle WM_CTLCOLORDLG in your dialog
```

Komunikat WM_CTLCOLORDLG został już obsłużony w kodzie Spy + +, więc jedyną wymaganą zmianą było usunięcie wszelkich odwołań do `SetDialogBkColor`, które nie są już potrzebne.

Następne ostrzeżenie było bardzo proste, aby rozwiązać problem, dodając komentarz do nazwy zmiennej. Otrzymaliśmy następujące ostrzeżenie:

```Output
warning C4456: declaration of 'lpszBuffer' hides previous local declaration
```

Kod, który generuje ten element, obejmuje makro.

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

Duże użycie makr, jak w tym kodzie, sprawia, że kod jest trudniejszy do utrzymania. W takim przypadku makra zawierają deklaracje zmiennych. PARAMETR makro jest zdefiniowane w następujący sposób:

```cpp
#define PARM(var, type, src)type var = (type)src
```

W związku z tym zmienna `lpszBuffer` jest zadeklarowana dwukrotnie w tej samej funkcji. Nie jest to proste, aby rozwiązać ten problem tak, jak gdyby kod nie używa makr (po prostu usuń deklarację drugiego typu). W takim przypadku mamy możliwość podjęcia decyzji o tym, czy należy ponownie napisać kod makra jako zwykły kod (żmudnym i ewentualnie podatne na błędy zadanie), czy wyłączyć ostrzeżenie.

W takim przypadku wybieramy ostrzeżenie. Możemy to zrobić przez dodanie dyrektywy pragma w następujący sposób:

```cpp
#pragma warning(disable : 4456)
```

Podczas wyłączania ostrzeżenia można ograniczyć efekt wyłączenia tylko do kodu, który generuje ostrzeżenie, aby uniknąć pomijania ostrzeżenia, gdy może on dostarczyć przydatne informacje. Dodaliśmy kod, aby przywrócić ostrzeżenie tuż po wierszu, który go generuje, lub lepiej, ponieważ to ostrzeżenie występuje w makrze, użyj słowa kluczowego **__pragma** , które działa w makrach (`#pragma` nie działa w makrach).

```cpp
#define PARM(var, type, src)__pragma(warning(disable : 4456))  \
type var = (type)src \
__pragma(warning(default : 4456))
```

Następne ostrzeżenie wymaga wprowadzenia zmian w kodzie. `GetVersion` Win32 API (i `GetVersionEx`) są przestarzałe.

```Output
warning C4996: 'GetVersion': was declared deprecated
```

Poniższy kod przedstawia sposób uzyskiwania wersji.

```cpp
// check Windows version and set m_bIsWindows9x/m_bIsWindows4x/m_bIsWindows5x flags accordingly.
DWORD dwWindowsVersion = GetVersion();
```

Następuje to wiele kodu, który analizuje wartość dwWindowsVersion, aby określić, czy pracujemy w systemie Windows 95 i która wersja systemu Windows NT. Ponieważ to wszystko jest nieaktualne, firma Microsoft usuwa kod i zajmuje się wszelkimi odwołaniami do tych zmiennych.

W artykule [zmiany wersji systemu operacyjnego w systemach Windows 8.1 i Windows Server 2012 R2](/windows/win32/w8cookbook/operating-system-version-changes-in-windows-8-1) opisano sytuację.

W klasie `CSpyApp` są dostępne metody, które wysyłają zapytania do wersji systemu operacyjnego: `IsWindows9x`, `IsWindows4x`i `IsWindows5x`. Dobrym punktem początkowym jest założenie, że wersje systemu Windows, które mają być obsługiwane (system Windows 7 i nowsze), są blisko systemu Windows NT 5, ponieważ technologie używane w tej starszej aplikacji są odpowiednie. Zastosowanie tych metod było związane z ograniczeniami starszych systemów operacyjnych. Dlatego zmieniono te metody, aby zwracały wartość TRUE dla `IsWindows5x` i FALSE dla innych.

```cpp
BOOL IsWindows9x() {/*return(m_bIsWindows9x);*/ return FALSE;  }
BOOL IsWindows4x() {/*return(m_bIsWindows4x);*/ return FALSE;  }
BOOL IsWindows5x() {/*return(m_bIsWindows5x);*/ return TRUE;  }
```

To tylko kilka miejsc, w których zmienne wewnętrzne były używane bezpośrednio. Ze względu na to, że usunięto te zmienne, wystąpimy kilka błędów, które muszą być w sposób jawny.

```Output
error C2065: 'm_bIsWindows9x': undeclared identifier
```

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(m_bIsWindows9x || hToolhelp32 != NULL);
}
```

Możemy zastąpić to wywołanie metody lub po prostu przekazać wartość TRUE i usunąć stary specjalny przypadek dla systemu Windows 9X.

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(TRUE /*!m_bIsWindows9x || hToolhelp32 != NULL*/);
}
```

Końcowe ostrzeżenie na poziomie domyślnym (3) musi mieć wartość pole bitowe.

```Output
treectl.cpp(1656): warning C4463: overflow; assigning 1 to bit-field that can only hold values from -1 to 0
```

Ten kod wyzwala następujące czynności.

```cpp
m_bStdMouse = TRUE;
```

Deklaracja `m_bStdMouse` wskazuje, że jest to element pole bitowe.

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

Ten kod został zapisany przed wbudowanym typem bool w wizualizacji C++. W takim kodzie BOOL był elementem **typedef** dla **int**. Typ **int** jest typem ze **znakiem** , a reprezentacja bitowa ze **znakiem int** ma używać pierwszego bitu jako bitu znaku, więc pole bitowe typu int można interpretować jako reprezentujący 0 lub-1, prawdopodobnie nie jest to oczekiwane.

Nie wiesz, patrząc na kod, dlaczego są one pola bitów. Czy zamiar zachować mały rozmiar obiektu lub czy tam, gdzie jest używany układ binarny obiektu? Zmieniono te wartości na zwykłe elementy logiczne, ponieważ nie wykryto żadnych przyczyn użycia pole bitowe. Użycie pola bitów do zachowania małego rozmiaru obiektu nie jest gwarantowane. Jest to zależne od tego, jak kompilator ustala typ.

Może się zdarzyć, że użycie typu standardowego **bool** w systemie byłoby przydatne. Wiele starych wzorców kodu, takich jak typ BOOL, zostały opracowane w celu rozwiązywania problemów, które zostały później rozwiązane w warstwie Standardowa C++, więc zmiana wartości logicznej na typ wbudowany typu **bool** to tylko jeden przykład takiej zmiany, którą należy wziąć pod uwagę po pierwszym uruchomieniu kodu w nowej wersji.

Po podaniu wszystkich ostrzeżeń, które są wyświetlane na poziomie domyślnym (poziom 3), został zmieniony na poziom 4, aby przechwycić kilka dodatkowych ostrzeżeń. Pierwszy z nich jest następujący:

```Output
warning C4100: 'nTab': unreferenced formal parameter
```

Kod, który wygenerował to ostrzeżenie, był następujący:

```cpp
virtual void OnSelectTab(int nTab) {};
```

Wydaje się to nieszkodliwe, ale ponieważ chcielibyśmy przeprowadzić czystą kompilację z `/W4` i `/WX` zestawem, po prostu komentarz do nazwy zmiennej, pozostawiając ją w celu czytelności.

```cpp
virtual void OnSelectTab(int /*nTab*/) {};
```

Inne otrzymane ostrzeżenia są przydatne podczas ogólnego czyszczenia kodu. Istnieje wiele niejawnych konwersji z **int** lub **unsigned int** do wyrazu (jest to element typedef dla **niepodpisanego Short**). Obejmują one ewentualną utratę danych. W tych przypadkach dodaliśmy rzutowanie do programu WORD.

Dla tego kodu jest wyświetlane ostrzeżenie innego poziomu 4:

```Output
warning C4211: nonstandard extension used: redefined extern to static
```

Ten problem występuje, gdy zmienna została najpierw zadeklarowana jako **extern**, a następnie później zadeklarowana jako **statyczna**. Znaczenie tych dwóch specyfikatorów klas magazynu wykluczają się wzajemnie, ale jest to dozwolone jako rozszerzenie firmy Microsoft. Jeśli chcesz, aby kod był przenośny do innych kompilatorów lub chcesz go skompilować przy użyciu `/Za` (zgodność ze standardem ANSI), należy zmienić deklaracje tak, aby miały pasujące specyfikatory klasy magazynu.

##  <a name="porting_to_unicode"></a>Krok 11. Przenoszenie z MBCS do Unicode

Należy pamiętać, że w świecie systemu Windows, gdy jesteśmy w formacie Unicode, zwykle jest to UTF-16. W przypadku innych systemów operacyjnych, takich jak Linux, są używane UTF-8, ale system Windows zazwyczaj nie. Wersja MBCS MFC była przestarzała w Visual Studio 2013 i 2015, ale nie jest już przestarzała w programie Visual Studio 2017. Jeśli jest używany Visual Studio 2013 lub 2015, przed przeprowadzeniem kroku do rzeczywistego portu MBCS kod w kodzie Unicode UTF-16, firma Microsoft może chcieć tymczasowo wyeliminować ostrzeżenia, które MBCS są przestarzałe, aby można było wykonać inne zadania lub odroczyć port do dogodnego czasu. Bieżący kod korzysta z MBCS i aby kontynuować, że musimy zainstalować wersję MFC/MBCS w wersji ANSI. Niewielka biblioteka MFC nie jest częścią domyślnego programowania programu Visual Studio **Desktop z C++**  instalacją, dlatego musi być wybrana z opcjonalnych składników w instalatorze. Zobacz [dodatek MFC MBCS dll](../mfc/mfc-mbcs-dll-add-on.md). Po pobraniu i ponownym uruchomieniu programu Visual Studio można kompilować i łączyć się z MBCS wersją MFC, ale aby usunąć ostrzeżenia o MBCS, jeśli używasz Visual Studio 2013 lub 2015, należy również dodać NO_WARN_MBCS_MFC_DEPRECATION do listy wstępnie zdefiniowanych makr w sekcji **preprocesora** we właściwościach projektu lub na początku pliku nagłówkowego *stdafx. h* lub innego wspólnego pliku nagłówkowego.

Mamy teraz kilka błędów konsolidatora.

```Output
fatal error LNK1181: cannot open input file 'mfc42d.lib'
```

LNK1181 występuje, ponieważ nieaktualna statyczna wersja biblioteki MFC jest uwzględniona w danych wejściowych konsolidatora. Nie jest to wymagane, ponieważ możemy dynamicznie łączyć MFC, dlatego wystarczy usunąć wszystkie biblioteki statyczne MFC z właściwości **Input** w sekcji **konsolidatora** właściwości projektu. Ten projekt używa również opcji `/NODEFAULTLIB`, a zamiast tego wyświetla wszystkie zależności biblioteki.

```
msvcrtd.lib;msvcirtd.lib;kernel32.lib;user32.lib;gdi32.lib;advapi32.lib;Debug\SpyHk55.lib;%(AdditionalDependencies)
```

Teraz daj nam zaktualizować stary kod wielobajtowego zestawu znaków (MBCS) do formatu Unicode. Ponieważ jest to aplikacja systemu Windows, dokładnie powiązane z platformą Windows Desktop, przeniesiemy ją do formatu UTF-16 Unicode używanego przez system Windows. W przypadku pisania kodu międzyplatformowego lub przenoszenia aplikacji systemu Windows na inną platformę warto rozważyć przenoszenie do formatu UTF-8, który jest powszechnie używany w innych systemach operacyjnych.

W przypadku przenoszenia do formatu UTF-16 Unicode należy zdecydować, czy nadal chcemy, aby opcja została skompilowana do MBCS, czy nie.  Jeśli chcemy mieć opcję obsługi MBCS, należy użyć makra używanie TCHAR jako typu znaku, który jest rozpoznawany jako **char** lub **wchar_t**, w zależności od tego, czy \_MBCS czy \_Unicode jest zdefiniowana podczas kompilacji. Przełączenie do używanie TCHAR i wersji używanie TCHAR różnych interfejsów API zamiast **wchar_t** i skojarzonych z nimi interfejsów API oznacza, że można wrócić do wersji MBCS kodu, wystarczy zdefiniować makro \_MBCS zamiast \_Unicode. Oprócz używanie TCHAR, istnieją różne wersje używanie TCHAR, takie jak powszechnie używane definicje typów, makra i funkcje. Na przykład LPCTSTR zamiast LPCSTR i tak dalej. W oknie dialogowym właściwości projektu, w obszarze **Właściwości konfiguracji**, w sekcji **Ogólne** Zmień właściwość **zestawu znaków** z zestawu znaków **MBCS** na użycie zestawu znaków **Unicode**. To ustawienie ma wpływ na to, jakie makro jest wstępnie zdefiniowane podczas kompilacji. Istnieje zarówno makro UNICODE, jak i \_makro UNICODE. Właściwość projektu wpływa spójnie. Nagłówki systemu Windows używają UNICODE, C++ gdzie nagłówki wizualne, takie jak MFC, używają \_Unicode, ale gdy jeden jest zdefiniowany, drugi jest zawsze zdefiniowany.

Dobry [Przewodnik](/previous-versions/cc194801(v=msdn.10)) dotyczący przenoszenia z MBCS do UTF-16 Unicode przy użyciu używanie TCHAR istnieje. Wybieramy tę trasę. Najpierw zmienimy Właściwość **zestawu znaków** , aby **używała zestawu znaków Unicode** i ponownie skompiluj projekt.

Niektóre miejsca w kodzie już korzystają z używanie TCHAR, prawdopodobnie w oczekiwanej obsłudze kodu Unicode. Niektóre z nich nie zostały. Przeszukano wystąpienia CHAR, które jest **elementem TypeDef** dla **char**, i zastąpione większością z używanie TCHAR. Szukamy również `sizeof(CHAR)`. Zawsze, gdy zmienimy się z CHAR na używanie TCHAR, zwykle musiałeś zmienić na `sizeof(TCHAR)`, ponieważ był on często używany do określenia liczby znaków w ciągu. Użycie nieprawidłowego typu w tym miejscu nie powoduje błędu kompilatora, dlatego warto zwrócić uwagę na ten przypadek.

Ten typ błędu jest bardzo powszechny po przełączeniu do formatu Unicode.

```Output
error C2664: 'int wsprintfW(LPWSTR,LPCWSTR,...)': cannot convert argument 1 from 'CHAR [16]' to 'LPWSTR'
```

Oto przykład kodu, który tworzy:

```cpp
wsprintf(szTmp, "%d.%2.2d.%4.4d", rmj, rmm, rup);
```

Wprowadzamy \_T wokół literału ciągu, aby usunąć błąd.

```cpp
wsprintf(szTmp, _T("%d.%2.2d.%4.4d"), rmj, rmm, rup);
```

Makro \_T ma wpływ na tworzenie literału ciągu jako ciągu **znaków** lub ciągu **wchar_t** , w zależności od ustawienia MBCS lub Unicode. Aby zastąpić wszystkie ciągi \_T w programie Visual Studio, najpierw Otwórz pole **szybkie zastąpienie** (klawiatura: **Ctrl**+**F**) lub **zamień w plikach** (klawiatura: **Ctrl**+**SHIFT**+**H**), a następnie wybierz pole wyboru **Użyj wyrażeń regularnych** . Wprowadź `((\".*?\")|('.+?'))` jako tekst do wyszukania i `_T($1)` jako tekst zastępujący. Jeśli masz już makro \_T wokół niektórych ciągów, ta procedura zostanie ponownie dodana i może również znajdować przypadki, w których nie chcesz \_T, na przykład gdy używasz `#include`, dlatego najlepiej użyć **Zastąp** , a nie **Zamień wszystkiego**.

Ta określona funkcja, [wsprintf](/windows/win32/api/winuser/nf-winuser-wsprintfw), jest zdefiniowana w nagłówkach systemu Windows, a dokumentacja nie zaleca się jej użycia z powodu przepełnienia buforu. Nie podano rozmiaru bufora `szTmp`, dlatego nie ma możliwości sprawdzenia, czy bufor może przechowywać wszystkie dane do zapisu. Zapoznaj się z następną sekcją przenoszenia do bezpiecznej CRT, w której Naprawiono inne podobne problemy. Zakończył zamianę na [_stprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md).

Inny typowy błąd widoczny w konwersji na Unicode to.

```Output
error C2440: '=': cannot convert from 'char *' to 'TCHAR *'
```

Tworzony jest następujący kod:

```cpp
pParentNode->m_szText = new char[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

Mimo że funkcja `_tcscpy` została użyta, która jest funkcją używanie TCHAR strcpy do kopiowania ciągu, przydzielony bufor był buforem **char** . Jest to łatwo zmienione na używanie TCHAR.

```cpp
pParentNode->m_szText = new TCHAR[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

Podobnie zmieniono LPSTR (długi wskaźnik na ciąg) i LPCSTR (długi wskaźnik na ciąg stały) na LPTSTR (długi wskaźnik do używanie TCHAR ciąg) i LPCTSTR (długi wskaźnik do stałego ciągu używanie TCHAR), gdy jest to uzasadnione przez błąd kompilatora. Nie wybraliśmy takich zamian przy użyciu wyszukiwania globalnego i zastępowania, ponieważ każda z nich musiała zostać zbadana pojedynczo. W niektórych przypadkach jest wymagana wersja **znaku** , na przykład podczas przetwarzania niektórych komunikatów systemu Windows korzystających ze struktur systemu Windows, które **mają sufiks.** W interfejsie API systemu Windows sufiks **a** oznacza ASCII lub ANSI (a także dotyczy MBCS), a sufiks **w** przypadku znaków dwubajtowych lub UTF-16 Unicode. Ten wzorzec nazewnictwa jest używany w nagłówkach systemu Windows, ale również został użyty w kodzie Spy + +, gdy musiałem zostać dodana wersja Unicode funkcji, która została już zdefiniowana w wersji MBCS.

W niektórych przypadkach wymagało zamiany typu w celu użycia wersji, która jest rozpoznawana poprawnie (WNDCLASS zamiast WNDCLASSA na przykład).

W wielu przypadkach musiała być używana ogólna wersja (makro) Win32 API jak `GetClassName` (zamiast `GetClassNameA`). W przypadku instrukcji switch programu obsługi komunikatów niektóre komunikaty są MBCS lub Unicode, w takich przypadkach musiałeś zmienić kod, aby jawnie wywołać wersję MBCS, ponieważ zastępujemy funkcje o nazwie i **w** określonych funkcjach i dodaliśmy makro dla nazwy ogólnej, która jest rozpoznawana jako poprawna nazwa **a** lub **w** na podstawie tego, czy Unicode jest zdefiniowany.  W wielu częściach kodu, gdy przełączymy się w celu zdefiniowania \_UNICODE, zostanie **wybrana wersja w**

Istnieje kilka miejsc, w których należy podjąć specjalne działania. Użycie `WideCharToMultiByte` lub `MultiByteToWideChar` może wymagać bliższego wyglądu. Oto przykład, w którym `WideCharToMultiByte` był używany.

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

Aby rozwiązać ten fakt, musiałmy zrozumieć, że przyczyną jest skopiowanie ciągu znaków dwubajtowych reprezentującego nazwę czcionki do wewnętrznego bufora `CString`, `strFace`. Jest to nieznacznie inny kod dla wielobajtowych ciągów `CString`, tak jak w przypadku ciągów szerokiej `CString`, więc dodaliśmy `#ifdef` w tym przypadku.

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

Oczywiście zamiast `wcscpy` należy używać `wcscpy_s`, bezpieczniejszej wersji. Następna sekcja dotyczy tego.

Jako sprawdzenie naszej pracy należy zresetować **zestaw znaków** , aby **używał zestawu znaków wielobajtowych** , i upewnić się, że kod nadal kompiluje się przy użyciu MBCS, a także kodu Unicode. Niezbędny do wypowiedzenia, w ponownie skompilowanej aplikacji należy wykonać pełne przebieg testowy po wszystkich tych zmianach.

W naszej pracy z tym rozwiązaniem Spy + + zajęło on około dwóch dni roboczych na średnią C++ aplikację, aby przekonwertować kod na Unicode. , Które nie obejmowały czasu przetestowania.

##  <a name="porting_to_secure_crt"></a>Krok 12. Przenoszenie do używania bezpiecznego CRT

Przenoszenie kodu w celu używania bezpiecznych wersji (wersje z sufiksem **_s** ) funkcji CRT jest dalej. W takim przypadku ogólna strategia polega na zastępowaniu funkcji z wersją **_s** , a następnie, zazwyczaj dodać wymagane dodatkowe parametry rozmiaru buforu. W wielu przypadkach jest to proste, ponieważ rozmiar jest znany. W innych przypadkach, w których rozmiar nie jest natychmiast dostępny, konieczne jest dodanie dodatkowych parametrów do funkcji, która używa funkcji CRT, lub może sprawdzić użycie buforu docelowego i zobaczyć, jakie są odpowiednie limity rozmiaru.

Wizualizacja C++ zawiera lewę, która ułatwia uzyskiwanie bezpiecznego kodu bez konieczności dodawania tylu parametrów rozmiaru i jest przy użyciu przeciążeń szablonu. Ponieważ te przeciążenia są szablonami, są dostępne tylko wtedy, gdy C++kompilacja jako, a nie jako c. Spyxxhk jest projektem c, więc lewę nie będzie można używać.  Jednak spyxx nie jest i będziemy mogli korzystać z lew. Lewę jest dodanie linii podobnej do tego w miejscu, w którym zostanie on skompilowany w każdym pliku projektu, na przykład w stdafx. h:

```cpp
#define _CRT_SECURE_TEMPLATE_OVERLOADS 1
```

Po zdefiniowaniu tego elementu, gdy bufor jest tablicą, a nie pierwotnym wskaźnikiem, jego rozmiar jest wywnioskowany z typu tablicy i używany jako parametr rozmiaru, bez konieczności podawania go. Pozwala to skrócić złożoność ponownego zapisywania kodu. W dalszym ciągu należy zamienić nazwę funkcji na wersję **_s** , ale często można wykonać operację wyszukiwania i zamieniania.

Wartości zwracane niektórych funkcji zostały zmienione. Na przykład `_itoa_s` (i `_itow_s` i makro `_itot_s`) zwraca kod błędu (`errno_t`), a nie ciąg. W takich przypadkach należy przenieść wywołanie do `_itoa_s` w osobnym wierszu i zastąpić je identyfikatorem buforu.

Niektóre typowe przypadki: dla `memcpy`, podczas przełączania do `memcpy_s`, często dodaliśmy rozmiar struktury kopiowanej do. Podobnie w przypadku większości ciągów i buforów rozmiar tablicy lub buforu można łatwo określić na podstawie deklaracji buforu lub przez znalezienie miejsca, w którym bufor został pierwotnie przydzielony. W niektórych sytuacjach należy określić, jak duże jest dostępność bufora, a jeśli te informacje nie są dostępne w zakresie modyfikowanej funkcji, należy dodać jako dodatkowy parametr, a kod wywołujący powinien zostać zmodyfikowany do Podaj informacje.

Przy użyciu tych technik trwało około pół dnia, aby przekonwertować kod w celu użycia funkcji Secure CRT. Jeśli wybierzesz pozycję nie do przeciążenia szablonu i dodasz parametry rozmiaru ręcznie, prawdopodobnie trwa dwa razy lub trzy razy więcej czasu.

##  <a name="deprecated_forscope"></a>Krok 13. /Zc: forScope — jest przestarzałe

Ponieważ Visual C++ 6,0, kompilator jest zgodny z bieżącym standardem, który ogranicza zakres zmiennych zadeklarowanych w pętli do zakresu pętli. Opcja kompilatora [/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) (**Wymuszaj zgodność z zakresem pętli** we właściwościach projektu) określa, czy jest to raportowany jako błąd. Należy zaktualizować nasz kod, aby był zgodny, i dodać deklaracje tylko poza pętlą. Aby uniknąć wprowadzania zmian w kodzie, można zmienić to ustawienie w sekcji **Język** właściwości C++ projektu na `No (/Zc:forScope-)`. Należy jednak pamiętać, że `/Zc:forScope-` mogą zostać usunięte w przyszłej wersji wizualizacji C++, a ostatecznie kod będzie musiał ulec zmianie, aby był zgodny ze standardem.

Te problemy są stosunkowo łatwe do naprawy, ale w zależności od kodu mogą mieć wpływ na wiele kodów. Poniżej przedstawiono typowy problem.

```cpp
int CPerfTextDataBase::NumStrings(LPCTSTR mszStrings) const
{
  for (int n = 0; mszStrings[0] != 0; n++)
  mszStrings = _tcschr(mszStrings, 0) + 1;
  return(n);
}
```

Powyższy kod powoduje błąd:

```Output
'n': undeclared identifier
```

Dzieje się tak, ponieważ kompilator zakończył opcję kompilatora, która zezwala na kod, który nie jest już C++ zgodny ze standardem. W standardzie deklarowanie zmiennej wewnątrz pętli ogranicza swój zakres do pętli, dlatego powszechną metodą używania licznika pętli poza pętlą jest, że deklaracja licznika również jest przenoszona poza pętlę, jak w poniższym zmienionym kodzie :

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

Przenoszenie programu Spy + + z oryginalnego kodu programu C++ Visual 6,0 do najnowszego kompilatora zajęło około 20 godzin czasu kodowania w ciągu tygodnia. Firma Microsoft została uaktualniona bezpośrednio przez osiem wydań produktu z programu Visual Studio 6,0 do programu Visual Studio 2015. Jest to teraz zalecane rozwiązanie dla wszystkich uaktualnień w projektach dużych i małych.

## <a name="see-also"></a>Zobacz też

[Przenoszenie i uaktualnianie: Przykłady i analizy przypadków](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Poprzednia analiza przypadku: COM Spy](../porting/porting-guide-com-spy.md)
