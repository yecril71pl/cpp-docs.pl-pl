---
title: 'Przewodnik przenoszenia: Narzędzie Spy++'
ms.date: 10/23/2019
ms.assetid: e558f759-3017-48a7-95a9-b5b779d5e51d
ms.openlocfilehash: edccf18c3fbc4d6eeec2ed0aa59df0e7d1f85335
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353379"
---
# <a name="porting-guide-spy"></a>Przewodnik przenoszenia: Narzędzie Spy++

To studium przypadku przenoszenia ma na celu dać wyobrażenie o tym, jak wygląda typowy projekt przenoszenia, rodzaje problemów, które mogą wystąpić, oraz kilka ogólnych wskazówek i wskazówek dotyczących rozwiązywania problemów z przenoszeniem. To nie ma być ostateczny przewodnik do przenoszenia, ponieważ doświadczenie przenoszenia projektu zależy w dużej mierze od specyfiki kodu.

## <a name="spy"></a>Spy++

Spy ++ jest powszechnie używane narzędzie diagnostyczne GUI dla pulpitu systemu Windows, który zapewnia wszelkiego rodzaju informacje na temat elementów interfejsu użytkownika na pulpicie systemu Windows. Pokazuje pełną hierarchię okien i zapewnia dostęp do metadanych o każdym oknie i kontroli. Ta przydatna aplikacja jest dostarczany z visual studio przez wiele lat. Znaleźliśmy starą wersję, która została ostatnio skompilowana w języku Visual C++ 6.0 i przeniesiona do programu Visual Studio 2015. Środowisko dla programu Visual Studio 2017 lub Visual Studio 2019 powinno być prawie identyczne.

Uznaliśmy, że ten przypadek jest typowy dla przenoszenia aplikacji klasycznych systemu Windows, które używają MFC i Win32 API, szczególnie dla starych projektów, które nie zostały zaktualizowane przy każdej wersji programu Visual C++ od visual C++ 6.0.

## <a name="step-1-converting-the-project-file"></a><a name="convert_project_file"></a>Krok 1. Konwertowanie pliku projektu.

Plik projektu, dwa stare pliki .dsw z programu Visual C++ 6.0, można łatwo przekonwertować bez problemów, które wymagają dalszej uwagi. Jednym z projektów jest aplikacja Spy++. Drugi to SpyHk, napisany w C, obsługującej bibliotekę DLL. Bardziej złożone projekty mogą nie zostać uaktualnione tak łatwo, jak omówiono [tutaj.](../porting/visual-cpp-porting-and-upgrading-guide.md)

Po modernizacji dwóch projektów nasze rozwiązanie wyglądało następująco:

![Rozwiązanie&#43;&#43; szpiegowskie](../porting/media/spyxxsolution.PNG "Rozwiązanie&#43;&#43; szpiegowskie")

Mamy dwa projekty, jeden z dużą liczbą plików C++, a drugi DLL, który jest napisany w języku C.

## <a name="step-2-header-file-problems"></a><a name="header_file_problems"></a>Krok 2. Problemy z plikiem nagłówka

Po zbudowaniu nowo przekonwertowanego projektu jedną z pierwszych rzeczy, które często można znaleźć, jest to, że pliki nagłówkowe używane przez projekt nie zostaną znalezione.

Jednym z plików, których nie można znaleźć w Spy++ był verstamp.h. Z wyszukiwania w Internecie ustaliliśmy, że pochodzi to z SDK DAO, przestarzałej technologii danych. Chcieliśmy dowiedzieć się, jakie symbole były używane z tego pliku nagłówka, aby sprawdzić, czy ten plik był naprawdę potrzebny lub czy te symbole zostały zdefiniowane gdzie indziej, więc skomentowaliśmy deklarację pliku nagłówka i ponownie skompilowaliśmy. Okazuje się, że jest tylko jeden symbol, który jest potrzebny, VER_FILEFLAGSMASK.

```Output
1>C:\Program Files (x86)\Windows Kits\8.1\Include\shared\common.ver(212): error RC2104: undefined keyword or key name: VER_FILEFLAGSMASK
```

Najprostszym sposobem znalezienia symbolu w dostępnych plikach dołączanych jest użycie **funkcji Znajdź w plikach** **(Ctrl**+**Shift**+**F)** i określenie **visual c++ include Directories**. Znaleźliśmy go w ntverp.h. Wymieniliśmy verstamp.h to ntverp.h i ten błąd zniknął.

## <a name="step-3-linker-outputfile-setting"></a><a name="linker_output_settings"></a>Krok 3. Ustawienie pliku wyjściowego konsolidatora

Starsze projekty czasami mają pliki umieszczone w niekonwencjonalnych lokalizacjach, które mogą powodować problemy po uaktualnieniu. W takim przypadku musimy `$(SolutionDir)` dodać do **Include** path we właściwościach projektu, aby upewnić się, że visual studio można znaleźć niektóre pliki nagłówka, które są tam umieszczone, a nie w jednym z folderów projektu.

MSBuild skarży się, że **Właściwość Link.OutputFile** nie jest zgodna z wartościami **TargetPath** i **TargetName,** wystawiając msb8012.

```Output
warning MSB8012: TargetPath(...\spyxx\spyxxhk\.\..\Debug\SpyxxHk.dll) does not match the Linker's OutputFile property value (...\spyxx\Debug\SpyHk55.dll). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).warning MSB8012: TargetName(SpyxxHk) does not match the Linker's OutputFile property value (SpyHk55). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).
```

**Link.OutputFile** jest wyjściem kompilacji (EXE, DLL, na przykład), `$(TargetDir)$(TargetName)$(TargetExt)`i jest zwykle konstruowany z , podając ścieżkę, nazwę pliku i rozszerzenie. Jest to typowy błąd podczas migracji projektów ze starego narzędzia kompilacji języka Visual C++ (vcbuild.exe) do nowego narzędzia kompilacji (MSBuild.exe). Ponieważ zmiana narzędzia kompilacji wystąpił w programie Visual Studio 2010, może wystąpić ten problem przy każdym migracji projektu sprzed 2010 r. do wersji 2010 lub nowszej. Podstawowym problemem jest to, że kreator migracji projektu nie **aktualizuje Wartość Link.OutputFile,** ponieważ nie zawsze jest możliwe określenie, jaka jest jego wartość na podstawie innych ustawień projektu. W związku z tym zwykle trzeba ustawić go ręcznie. Aby uzyskać więcej informacji, zobacz ten [post](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/) na blogu języka Visual C++.

W takim przypadku właściwość **Link.OutputFile** w przekonwertowanym projekcie została ustawiona na .\Debug\Spyxx.exe i .\Release\Spyxx.exe dla projektu Spy++, w zależności od konfiguracji. Najlepiej jest po prostu zastąpić te wartości `$(TargetDir)$(TargetName)$(TargetExt)` zakodowane na wszystkie **konfiguracje.** Jeśli to nie zadziała, można dostosować stamtąd lub zmienić właściwości w sekcji **Ogólne,** w której są ustawione te wartości (właściwości to **Katalog wyjściowy,** **Nazwa docelowa**i **Rozszerzenie docelowe**. Pamiętaj, że jeśli wyświetlana właściwość używa makr, możesz wybrać **opcję Edytuj** na liście rozwijanej, aby wyświetlić okno dialogowe z ostatnim ciągiem z wykonanymi podstawkami makr. Wszystkie dostępne makra i ich bieżące wartości można wyświetlić, wybierając przycisk **Makra.**

## <a name="step-4-updating-the-target-windows-version"></a><a name="updating_winver"></a>Krok 4. Aktualizowanie docelowej wersji systemu Windows

Następny błąd wskazuje, że wersja programu WINVER nie jest już obsługiwana w MFC. Winver dla systemu Windows XP jest 0x0501.

```Output
C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxv_w32.h(40): fatal error C1189: #error:  MFC does not support WINVER less than 0x0501.  Please change the definition of WINVER in your project properties or precompiled header.
```

System Windows XP nie jest już obsługiwany przez firmę Microsoft, więc mimo że kierowanie jest dozwolone w programie Visual Studio, należy stopniowo wycofywać obsługę tego w aplikacjach i zachęcać użytkowników do przyjmowania nowych wersji systemu Windows.

Aby pozbyć się błędu, zdefiniuj program WINVER, aktualizując ustawienie **Właściwości projektu** do najniższej wersji systemu Windows, którą obecnie chcesz kierować. Tutaj znajdziesz tabelę wartości dla różnych [wersji](/windows/win32/WinProg/using-the-windows-headers)systemu Windows .

Plik *stdafx.h* zawierał niektóre z tych definicji makr.

```cpp
#define WINVER       0x0500  // these defines are set so that we get the
#define _WIN32_WINNT 0x0500  // maximum set of message/flag definitions,
#define _WIN32_IE    0x0400  // from both winuser.h and commctrl.h.
```

WINVER ustawimy na Windows 7. Łatwiej jest odczytać kod później, jeśli używasz makra dla systemu Windows 7 (_WIN32_WINNT_WIN7), a nie samej wartości (0x0601).

```cpp
#define WINVER _WINNT_WIN32_WIN7 // Minimum targeted Windows version is Windows 7
```

## <a name="step-5-linker-errors"></a><a name="linker_errors"></a>Krok 5. Błędy konsolidatora

Dzięki tym zmianom projekt SpyHk (DLL) tworzy, ale generuje błąd konsolidatora.

```Output
LINK : warning LNK4216: Exported entry point _DLLEntryPoint@12
```

Nie należy eksportować punktu wejścia dla biblioteki DLL. Punkt wejścia jest przeznaczony do wywoływania tylko przez moduł ładujący, gdy biblioteka DLL jest najpierw ładowana do pamięci, więc nie powinna znajdować się w tabeli eksportu, która jest przeznaczona dla innych wywołań. Musimy tylko upewnić się, że nie ma **__declspec (dllexport)** dyrektywy dołączone do niego. W spyxxhk.c, musimy usunąć go z dwóch miejsc, `DLLEntryPoint`deklaracji i definicji . Nigdy nie ma sensu używać tej dyrektywy, ale poprzednie wersje konsolidatora i kompilatora nie oflagować go jako problem. Nowsze wersje konsolidatora ostrzegają.

```cpp
// deleted __declspec(dllexport)
BOOL WINAPI DLLEntryPoint(HINSTANCE hinstDLL,DWORD fdwReason, LPVOID lpvReserved);
```

Projekt DLL C, SpyHK.dll, teraz buduje i łączy bez błędu.

## <a name="step-6-more-outdated-header-files"></a><a name="outdated_header_files"></a>Krok 6. Więcej nieaktualnych plików nagłówkowych

W tym momencie rozpoczynamy pracę nad głównym projektem wykonywalnym, Spyxx.

Nie można znaleźć kilku innych plików dołączanych: ctl3d.h i penwin.h. Chociaż wyszukiwanie w Internecie w celu zidentyfikowania tego, co zawierał nagłówek, może być przydatne, czasami informacje nie są tak pomocne. Dowiedzieliśmy się, że ctl3d.h był częścią Exchange Development Kit i pod warunkiem wsparcia dla pewnego stylu kontroli w systemie Windows 95, a penwin.h odnosi się do Window Pen Computing, przestarzałe API. W tym przypadku po prostu `#include` komentujemy linię i zajmujemy się nieokreślonymi symbolami, tak jak zrobiliśmy to w przypadku verstamp.h. Wszystko, co odnosi się do kontroli 3D lub Pen Computing został usunięty z projektu.

Biorąc pod uwagę projekt z wielu błędów kompilacji, które są stopniowo eliminowania, nie jest realistyczne, `#include` aby znaleźć wszystkie zastosowania przestarzałego interfejsu API od razu po usunięciu dyrektywy. Nie wykryliśmy go natychmiast, ale w pewnym momencie doszło do błędu, który WM_DLGBORDER był nieokreślony. W rzeczywistości jest to tylko jeden z wielu nieokreślonych symboli, które pochodzą z ctl3d.h. Po ustaleniu, że odnosi się do przestarzałego interfejsu API, usunęliśmy wszystkie odwołania w kodzie do niego.

## <a name="step-7-updating-old-iostreams-code"></a><a name="updating_iostreams_code"></a>Krok 7. Aktualizowanie starego kodu iostreams

Następny błąd jest wspólny ze starym kodem Języka C++, który używa iostreams.

```Output
mstream.h(40): fatal error C1083: Cannot open include file: 'iostream.h': No such file or directory
```

Problem polega na tym, że stara biblioteka iostreams została usunięta i zastąpiona. Musimy zastąpić stare iostreams z nowszych standardów.

```cpp
#include <iostream.h>
#include <strstrea.h>
#include <iomanip.h>
```

Są to zaktualizowane obejmuje:

```cpp
#include <iostream>
#include <sstream>
#include <iomanip>
```

Z tą zmianą mamy `ostrstream`problemy z , który nie jest już używany. Właściwą wymianą jest ostringstream. Spróbujmy dodać **typedef** dla, `ostrstream` aby uniknąć modyfikowania kodu zbyt wiele, przynajmniej jako początek.

```cpp
typedef std::basic_ostringstream<TCHAR> ostrstream;
```

Obecnie projekt jest zbudowany przy użyciu MBCS (Wielo bajtowy zestaw znaków), więc **char** jest odpowiedni typ danych znaków. Jednak aby umożliwić łatwiejszą aktualizację kodu do UTF-16 `TCHAR`Unicode, możemy zaktualizować to do , który rozwiązuje **char** lub **wchar_t** w zależności od tego, czy **właściwość Zestaw znaków** w ustawieniach projektu jest ustawiona na MBCS lub Unicode.

Kilka innych elementów kodu należy zaktualizować.  Zastąpiliśmy klasę `ios` podstawową `ios_base`, a my wymieniliśmy ostream jest basic_ostream\<T>. Dodajemy dwa dodatkowe typedefs, a ta sekcja kompiluje.

```cpp
typedef std::basic_ostream<TCHAR> ostream;
typedef ios_base ios;
```

Korzystanie z tych typedefs jest tylko rozwiązaniem tymczasowym. Aby uzyskać bardziej trwałe rozwiązanie, możemy zaktualizować każde odwołanie do zmienionego nazwy lub przestarzałego interfejsu API.

Oto następny błąd.

```Output
error C2039: 'freeze': is not a member of 'std::basic_stringbuf<char,std::char_traits<char>,std::allocator<char>>'
```

Następnym problemem jest `basic_stringbuf` to, że `freeze` nie ma metody. Metoda `freeze` ta jest stosowana w celu `ostream`zapobieżenia wyciekowi pamięci w starym . Nie potrzebujemy go teraz, że używamy nowego `ostringstream`. Możemy usunąć połączenie `freeze`do .

```cpp
//rdbuf()->freeze(0);
```

Kolejne dwa błędy wystąpiły w sąsiednich liniach. Pierwszy narzeka na `ends`użycie , który `iostream` jest stary biblioteki IO manipulator, który dodaje null terminator do ciągu. Drugi z tych błędów wyjaśnia, `str` że dane wyjściowe metody nie można przypisać do wskaźnika non-const.

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

Przy użyciu nowej `ends` biblioteki strumienia, nie jest potrzebne, ponieważ ciąg jest zawsze zakończone z wartością null, dzięki czemu wiersz można usunąć. W przypadku drugiego problemu problem `str()` polega na tym, że teraz nie zwraca wskaźnika do tablicy znaków dla ciągu; zwraca `std::string` typ. Rozwiązaniem drugiego jest zmiana typu i `LPCSTR` użyć `c_str()` metody, aby zażądać wskaźnika.

```cpp
//*this << ends;
LPCTSTR psz = str().c_str();
```

Błąd, który zaskoczył nas na chwilę wystąpił w tym kodzie.

```cpp
MOUT << _T(" chUser:'") << chUser
<< _T("' (") << (INT)(UCHAR)chUser << _T(')');
```

Makro MOUT rozpoznaje, do `*g_pmout` którego `mstream`jest obiekt typu . Klasa `mstream` jest pochodną standardowej klasy `std::basic_ostream<TCHAR>`ciągu wyjściowego. Jednak \_z T wokół ciągu literał, który umieszczamy w ramach przygotowań do konwersji do Unicode, rozdzielczość przeciążenia dla **operatora <<** nie powiedzie się z następującym komunikatem o błędzie:

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

Istnieje tak wiele **operator <<** definicje, że tego rodzaju błąd może być zastraszające. Po przyjrzeniu się bliżej dostępnych przeciążenia, widzimy, że większość z nich są `mstream` nieistotne, i patrząc bliżej na definicji klasy, zidentyfikowaliśmy następującą funkcję, które uważamy, że należy wywołać w tym przypadku.

```cpp
mstream& operator<<(LPTSTR psz)
{
  return (mstream&)ostrstream::operator<<(psz);
}
```

Powodem, dla którego nie jest wywoływana jest `const wchar_t[10]` ponieważ literał ciągu ma typ, jak widać z ostatniego wiersza tego długiego komunikatu o błędzie, więc konwersja do wskaźnika non-const nie jest automatyczna. Jednak ten operator nie powinien modyfikować parametru wejściowego, więc `LPCTSTR` bardziej odpowiedni jest typ parametru (podczas`const char*` kompilowania jako MBCS i `const wchar_t*` jako Unicode), `LPTSTR` nie (podczas`char*` kompilowania jako MBCS i `wchar_t*` jako Unicode). Wprowadzenie tej zmiany rozwiązuje ten błąd.

Ten typ konwersji był dozwolony w starszych, mniej rygorystyczne kompilatora, ale nowsze zmiany zgodności wymagają bardziej poprawnego kodu.

## <a name="step-8-the-compilers-more-strict-conversions"></a><a name="stricter_conversions"></a>Krok 8. Bardziej rygorystyczne konwersje kompilatora

Otrzymujemy również wiele błędów, takich jak następujące:

```Output
error C2440: 'static_cast': cannot convert from 'UINT (__thiscall CHotLinkCtrl::* )(CPoint)' to 'LRESULT (__thiscall CWnd::* )(CPoint)'
```

Błąd występuje na mapie wiadomości, która jest po prostu makro:

```cpp
BEGIN_MESSAGE_MAP(CFindToolIcon, CWnd)
// other messages omitted...
ON_WM_NCHITTEST() // Error occurs on this line.
END_MESSAGE_MAP()
```

Przechodząc do definicji tego makra, widzimy, że odwołuje się do funkcji `OnNcHitTest`.

```cpp
#define ON_WM_NCHITTEST() \
{ WM_NCHITTEST, 0, 0, 0, AfxSig_l_p, \
(AFX_PMSG)(AFX_PMSGW) \
(static_cast< LRESULT (AFX_MSG_CALL CWnd::*)(CPoint) > (&ThisClass :: OnNcHitTest)) },
```

Problem ma do czynienia z niezgodności w wskaźniku do typów funkcji elementu członkowskiego. Problem nie jest konwersja `CHotLinkCtrl` z jako `CWnd` typ klasy jako typ klasy, ponieważ jest to prawidłowa konwersja pochodna do podstawy. Problem polega na typie zwracany: UINT vs. LRESULT. LRESULT rozwiązuje LONG_PTR który jest wskaźnikiem 64-bitowym lub 32-bitowym, w zależności od docelowego typu binarnego, więc UINT nie konwertuje do tego typu. Nie jest to rzadkością podczas uaktualniania kodu napisanego przed 2005 r., ponieważ typ zwracania wielu metod mapy wiadomości zmieniono z UINT na LRESULT w programie Visual Studio 2005 w ramach zmian zgodności 64-bitowej. Zmieniamy typ zwracany z UINT w następującym kodzie na LRESULT:

```cpp
afx_msg UINT OnNcHitTest(CPoint point);
```

Po zmianie mamy następujący kod:

```cpp
afx_msg LRESULT OnNcHitTest(CPoint point);
```

Ponieważ istnieje około dziesięciu wystąpień tej funkcji w różnych klasach pochodzących z CWnd, warto użyć **Przejdź do definicji** (Keyboard: **F12**) i **Przejdź do deklaracji** (Keyboard: **Ctrl**+**F12),** gdy kursor jest na funkcji w edytorze, aby zlokalizować te i przejść do nich z okna narzędzia **Znajdź symbol.** **Przejdź do definicji** jest zwykle bardziej przydatne z dwóch. **Przejdź do Deklaracji** znajdzie deklaracje inne niż deklaracje klasy definiowania, takie jak deklaracje klasy przyjaciela lub odwołania do przodu.

## <a name="step-9-mfc-changes"></a><a name="mfc_changes"></a>Krok 9. Zmiany W MFC

Następny błąd odnosi się również do zmienionego typu deklaracji, a także występuje w makrze.

```Output
error C2440: 'static_cast': cannot convert from 'void (__thiscall CFindWindowDlg::* )(BOOL,HTASK)' to 'void (__thiscall CWnd::* )(BOOL,DWORD)'
```

Problem polega na tym, `CWnd::OnActivateApp` że drugi parametr zmieniono z HTASK na DWORD. Ta zmiana nastąpiła w 2002 wydanie programu Visual Studio, Visual Studio .NET.

```cpp
afx_msg void OnActivateApp(BOOL bActive, HTASK hTask);
```

Musimy odpowiednio zaktualizować deklaracje OnActivateApp w klasach pochodnych w następujący sposób:

```cpp
afx_msg void OnActivateApp(BOOL bActive, DWORD dwThreadId);
```

W tym momencie jesteśmy w stanie skompilować projekt. Istnieje jednak kilka ostrzeżeń do wykonania, a istnieją opcjonalne części uaktualnienia, takie jak konwersja z MBCS na Unicode lub poprawa zabezpieczeń przy użyciu funkcji Secure CRT.

## <a name="step-10-addressing-compiler-warnings"></a><a name="compiler_warnings"></a>Krok 10. Adresowanie ostrzeżeń kompilatora

Aby uzyskać pełną listę ostrzeżeń, należy wykonać **Rebuild All** na rozwiązanie, a nie zwykłej kompilacji, tylko upewnić się, że wszystko, co wcześniej skompilowane zostaną ponownie skompilowane, ponieważ otrzymasz tylko raporty ostrzegawcze z bieżącej kompilacji. Inne pytanie brzmi, czy zaakceptować bieżący poziom ostrzeżenia lub użyć wyższego poziomu ostrzeżenia.  Podczas przenoszenia dużo kodu, zwłaszcza starego kodu, przy użyciu wyższego poziomu ostrzeżenia może być właściwe.  Można również rozpocząć od domyślnego poziomu ostrzeżenia, a następnie zwiększyć poziom ostrzeżenia, aby uzyskać wszystkie ostrzeżenia. Jeśli używasz `/Wall`, masz kilka ostrzeżeń w systemowych `/W4` plikach nagłówkowych, tak wiele osób używa, aby uzyskać jak najwięcej ostrzeżeń na ich kod bez uzyskiwania ostrzeżeń dla nagłówków systemowych. Jeśli chcesz, aby ostrzeżenia były wyświetlane `/WX` jako błędy, dodaj tę opcję. Te ustawienia znajdują się w sekcji **C/C++** w oknie dialogowym **Właściwości projektu.**

Jedna z metod `CSpyApp` w klasie generuje ostrzeżenie o funkcji, która nie jest już obsługiwana.

```cpp
void SetDialogBkColor() {CWinApp::SetDialogBkColor(::GetSysColor(COLOR_BTNFACE));}
```

Ostrzeżenie jest następujące.

```Output
warning C4996: 'CWinApp::SetDialogBkColor': CWinApp::SetDialogBkColor is no longer supported. Instead, handle WM_CTLCOLORDLG in your dialog
```

Wiadomość WM_CTLCOLORDLG była już obsługiwana w kodzie Spy++, więc jedyną wymaganą `SetDialogBkColor`zmianą było usunięcie wszelkich odniesień do , które nie są już potrzebne.

Następne ostrzeżenie było proste do naprawienia, komentując nazwę zmiennej. Otrzymaliśmy następujące ostrzeżenie:

```Output
warning C4456: declaration of 'lpszBuffer' hides previous local declaration
```

Kod, który to tworzy, obejmuje makro.

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

Intensywne użycie makr, jak w tym kodzie ma tendencję do kodu trudniejsze do utrzymania. W takim przypadku makra zawierają deklaracje zmiennych. Makro PARM jest zdefiniowane w następujący sposób:

```cpp
#define PARM(var, type, src)type var = (type)src
```

W związku `lpszBuffer` z tym zmienna zostanie zadeklarowana dwa razy w tej samej funkcji. Nie jest to takie proste, aby to naprawić, jak byłoby, gdyby kod nie używał makr (po prostu usuń deklarację drugiego typu). Ponieważ jest, mamy niefortunny wybór konieczności podjęcia decyzji, czy przepisać kod makra jako zwykły kod (żmudne i ewentualnie podatne na błędy zadanie) lub wyłączyć ostrzeżenie.

W takim przypadku zdecydujemy się wyłączyć ostrzeżenie. Możemy to zrobić, dodając pragmę w następujący sposób:

```cpp
#pragma warning(disable : 4456)
```

Podczas wyłączania ostrzeżenia, można ograniczyć efekt wyłączenia tylko do kodu, który generuje ostrzeżenie, aby uniknąć pomijania ostrzeżenia, gdy może dostarczyć przydatnych informacji. Dodajemy kod, aby przywrócić ostrzeżenie tuż po wierszu, który go tworzy, lub jeszcze lepiej, ponieważ to ostrzeżenie występuje`#pragma` w makrze, użyj słowa kluczowego **__pragma,** które działa w makrach ( nie działa w makrach).

```cpp
#define PARM(var, type, src)__pragma(warning(disable : 4456))  \
type var = (type)src \
__pragma(warning(default : 4456))
```

Następne ostrzeżenie wymaga pewnych poprawek kodu. Interfejs API `GetVersion` systemu Win32 (i) `GetVersionEx`jest przestarzały.

```Output
warning C4996: 'GetVersion': was declared deprecated
```

Poniższy kod pokazuje, jak wersja jest uzyskiwana.

```cpp
// check Windows version and set m_bIsWindows9x/m_bIsWindows4x/m_bIsWindows5x flags accordingly.
DWORD dwWindowsVersion = GetVersion();
```

Po tym następuje wiele kodu, który sprawdza dwWindowsVersion wartość, aby ustalić, czy jesteśmy uruchomione w systemie Windows 95 i która wersja systemu Windows NT. Ponieważ to wszystko jest nieaktualne, usuwamy kod i zajmujemy się wszelkimi odwołaniami do tych zmiennych.

Artykuł [Zmiany wersji systemu operacyjnego w systemach Windows 8.1 i Windows Server 2012 R2](/windows/win32/w8cookbook/operating-system-version-changes-in-windows-8-1) wyjaśnia sytuację.

Istnieją metody w `CSpyApp` klasie, które kwerendy `IsWindows9x` `IsWindows4x`wersji `IsWindows5x`systemu operacyjnego: , , i . Dobrym punktem wyjścia jest założenie, że wersje systemu Windows, które zamierzamy obsługiwać (Windows 7 i nowsze) są zbliżone do Systemu Windows NT 5, jeśli chodzi o technologie stosowane przez tę starszą aplikację. Zastosowania tych metod miały dotyczyć ograniczeń starszych systemów operacyjnych. Więc zmieniliśmy te metody, `IsWindows5x` aby zwrócić TRUE dla i FALSE dla innych.

```cpp
BOOL IsWindows9x() {/*return(m_bIsWindows9x);*/ return FALSE;  }
BOOL IsWindows4x() {/*return(m_bIsWindows4x);*/ return FALSE;  }
BOOL IsWindows5x() {/*return(m_bIsWindows5x);*/ return TRUE;  }
```

Pozostawiło to tylko kilka miejsc, w których zmienne wewnętrzne były używane bezpośrednio. Ponieważ usunęliśmy te zmienne, otrzymujemy kilka błędów, które mają do czynienia z jawnie.

```Output
error C2065: 'm_bIsWindows9x': undeclared identifier
```

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(m_bIsWindows9x || hToolhelp32 != NULL);
}
```

Możemy zastąpić to wywołaniem metody lub po prostu przekazać TRUE i usunąć stary specjalny przypadek dla Windows 9x.

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(TRUE /*!m_bIsWindows9x || hToolhelp32 != NULL*/);
}
```

Ostateczne ostrzeżenie na poziomie domyślnym (3) ma do czynienia z polem bitowym.

```Output
treectl.cpp(1656): warning C4463: overflow; assigning 1 to bit-field that can only hold values from -1 to 0
```

Kod, który wyzwala to jest w następujący sposób.

```cpp
m_bStdMouse = TRUE;
```

Deklaracja `m_bStdMouse` wskazuje, że jest to pole bitowe.

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

Ten kod został napisany przed wbudowany typ bool był obsługiwany w języku Visual C++. W takim kodzie BOOL był **typedef** dla **int.** Typ **int** jest typem **podpisanym,** a reprezentacja bitowa **podpisanego int** polega na użyciu pierwszego bitu jako bitu znaku, więc pole bitowe typu int może być interpretowane jako reprezentujące 0 lub -1, prawdopodobnie nie to, co było zamierzone.

Nie wiesz, patrząc na kod, dlaczego są to pola bitowe. Czy zamiar, aby zachować rozmiar obiektu małe, czy jest w dowolnym miejscu, gdzie używany jest układ binarny obiektu? Zmieniliśmy je na zwykłych członków BOOL, ponieważ nie widzieliśmy żadnego powodu do korzystania z pola bitowego. Używanie pól bitowych do utrzymywania małego rozmiaru obiektu nie gwarantuje pracy. To zależy od tego, jak kompilator określa typ.

Można się zastanawiać, czy przy użyciu standardowego typu **bool** całej byłoby pomocne. Wiele starych wzorców kodu, takich jak typ BOOL zostały wynalezione w celu rozwiązania problemów, które zostały później rozwiązane w standardzie C ++, więc zmiana z BOOL do **bool** wbudowany typ jest tylko jednym z przykładów takiej zmiany, które należy rozważyć robi po uzyskanie kodu początkowo uruchomiony w nowej wersji.

Po omówieniu wszystkich ostrzeżeń, które pojawiają się na poziomie domyślnym (poziom 3), zmieniliśmy się na poziom 4, aby wyłapać kilka dodatkowych ostrzeżeń. Pierwsze, które się pojawiły, było następujące:

```Output
warning C4100: 'nTab': unreferenced formal parameter
```

Kod, który wyprodukował to ostrzeżenie, był następujący.

```cpp
virtual void OnSelectTab(int nTab) {};
```

Wydaje się to dość nieszkodliwe, ale ponieważ `/W4` `/WX` chcieliśmy czystej kompilacji z i ustawić, po prostu skomentował nazwę zmiennej, pozostawiając go ze względu na czytelność.

```cpp
virtual void OnSelectTab(int /*nTab*/) {};
```

Inne ostrzeżenia, które otrzymaliśmy były przydatne do ogólnego oczyszczania kodu. Istnieje wiele niejawnych konwersji z **int** lub **unsigned int** do WORD (który jest typedef dla **niepodpisanego krótkiego**). Wiąże się to z możliwą utratą danych. Dodaliśmy obsadę do WORD w tych przypadkach.

Innym poziomem 4 ostrzeżenie mamy dla tego kodu było:

```Output
warning C4211: nonstandard extension used: redefined extern to static
```

Problem występuje, gdy zmienna została po raz pierwszy zadeklarowana **extern**, a następnie zadeklarowane **statyczne**. Znaczenie tych specyfikatorów klasy magazynu dwóch jest wzajemnie wykluczają się, ale jest to dozwolone jako rozszerzenie firmy Microsoft. Jeśli chcesz, aby kod był przenośny do innych kompilatorów lub chcesz skompilować go z `/Za` (zgodność ANSI), należy zmienić deklaracje, aby mieć pasujące specyfikatory klasy magazynu.

## <a name="step-11-porting-from-mbcs-to-unicode"></a><a name="porting_to_unicode"></a>Krok 11. Przenoszenie z MBCS do Unicode

Należy pamiętać, że w świecie systemu Windows, kiedy mówimy Unicode, zwykle mamy na myśli UTF-16. Inne systemy operacyjne, takie jak Linux używać UTF-8, ale Windows na ogół nie. Wersja MBCS MFC została przestarzała w programie Visual Studio 2013 i 2015, ale nie jest już przestarzała w programie Visual Studio 2017. Jeśli przy użyciu programu Visual Studio 2013 lub 2015, przed wykonaniem kroku do faktycznie port mbcs kodu do UTF-16 Unicode, możemy chcieć tymczasowo wyeliminować ostrzeżenia, że MBCS jest przestarzały, aby wykonać inną pracę lub odroczyć przenoszenie do dogodnego czasu. Bieżący kod używa MBCS i kontynuować, że musimy zainstalować wersję ANSI/MBCS MFC. Dość duża biblioteka MFC nie jest częścią domyślnego programu Visual Studio Desktop development z instalacją **języka C++,** więc musi być wybrana z opcjonalnych składników w instalatorze. Zobacz [dodatek MFC MBCS DLL](../mfc/mfc-mbcs-dll-add-on.md). Po pobraniu tego i ponownym uruchomieniu programu Visual Studio można skompilować i połączyć się z wersją MBCS MFC, ale aby pozbyć się ostrzeżeń dotyczących MBCS, jeśli używasz programu Visual Studio 2013 lub 2015, należy również dodać NO_WARN_MBCS_MFC_DEPRECATION do listy wstępnie zdefiniowanych makr w sekcji **Preprocessor** właściwości projektu lub na początku pliku nagłówka *stdafx.h* lub innego wspólnego pliku nagłówka.

Mamy teraz kilka błędów konsolidatora.

```Output
fatal error LNK1181: cannot open input file 'mfc42d.lib'
```

LNK1181 występuje, ponieważ przestarzała statyczna wersja biblioteki mfc jest zawarta na wejściu konsolidatora. Nie jest to już wymagane, ponieważ możemy połączyć MFC dynamicznie, więc musimy po prostu usunąć wszystkie biblioteki statyczne MFC z **Input** właściwości w **sekcji Konsolidator** właściwości projektu. Ten projekt jest `/NODEFAULTLIB` również przy użyciu opcji, a zamiast tego wyświetla listę wszystkich zależności biblioteki.

```
msvcrtd.lib;msvcirtd.lib;kernel32.lib;user32.lib;gdi32.lib;advapi32.lib;Debug\SpyHk55.lib;%(AdditionalDependencies)
```

Teraz pozwól nam rzeczywiście zaktualizować stary kod wielo bajtowy zestaw znaków (MBCS) do Unicode. Ponieważ jest to aplikacja systemu Windows, ściśle związana z platformą pulpitu systemu Windows, przemykiemy ją na UTF-16 Unicode, którego używa system Windows. Jeśli piszesz kod międzyplatformowy lub przenosisz aplikację systemu Windows na inną platformę, warto rozważyć przeniesienie do UTF-8, który jest szeroko stosowany w innych systemach operacyjnych.

Przenoszenie do UTF-16 Unicode, musimy zdecydować, czy nadal chcemy opcję kompilacji do MBCS, czy nie.  Jeśli chcemy mieć możliwość obsługi MBCS, powinniśmy użyć makra TCHAR jako typu znaku, **wchar_t**który jest rozpoznawany \_jako **char** lub wchar_t , w zależności od tego, czy MBCS lub \_UNICODE jest zdefiniowany podczas kompilacji. Przełączenie na wersje TCHAR i TCHAR różnych interfejsów API zamiast **wchar_t** i skojarzonych z nimi interfejsów API oznacza, że możesz \_wrócić do wersji \_MBCS kodu, po prostu definiując makro MBCS zamiast UNICODE. Oprócz TCHAR istnieje wiele wersji TCHAR, takich jak powszechnie używane typedefs, makra i funkcje. Na przykład LPCTSTR zamiast LPCSTR i tak dalej. W oknie dialogowym właściwości projektu w obszarze **Właściwości konfiguracji**w sekcji **Ogólne** zmień właściwość **Zestaw znaków** z Użyj zestawu **znaków MBCS,** aby użyć zestawu znaków **Unicode**. To ustawienie ma wpływ na to, które makro jest wstępnie zdefiniowane podczas kompilacji. Istnieje zarówno makro UNICODE, \_jak i makro UNICODE. Właściwość projektu wpływa zarówno konsekwentnie. Nagłówki systemu Windows używają UNICODE, gdzie nagłówki języka \_Visual C++, takie jak MFC, używają UNICODE, ale gdy jeden jest zdefiniowany, drugi jest zawsze zdefiniowany.

Istnieje dobry [przewodnik po](/previous-versions/cc194801(v=msdn.10)) przenoszeniu z MBCS do UTF-16 Unicode za pomocą TCHAR. Wybieramy tę trasę. Najpierw zmieniamy właściwość **Zestaw znaków** na Użycie zestawu **znaków Unicode** i przebudowujemy projekt.

Niektóre miejsca w kodzie były już przy użyciu TCHAR, najwyraźniej w oczekiwaniu na ostatecznie wspieranie Unicode. Niektóre nie były. Szukaliśmy instancji CHAR, który jest **typedef** dla **char**, i zastąpił większość z nich z TCHAR. Również szukaliśmy `sizeof(CHAR)`. Za każdym razem, gdy zmienialiśmy się z CHAR `sizeof(TCHAR)` na TCHAR, zwykle musieliśmy się na niego zmieniać, ponieważ było to często używane do określania liczby znaków w ciągu. Przy użyciu niewłaściwego typu w tym miejscu nie powoduje błąd kompilatora, więc warto zwrócić trochę uwagi na ten przypadek.

Ten typ błędu jest bardzo często po przełączeniu na Unicode.

```Output
error C2664: 'int wsprintfW(LPWSTR,LPCWSTR,...)': cannot convert argument 1 from 'CHAR [16]' to 'LPWSTR'
```

Oto przykład kodu, który to tworzy:

```cpp
wsprintf(szTmp, "%d.%2.2d.%4.4d", rmj, rmm, rup);
```

Umieszczamy \_T wokół literał ciągu, aby usunąć błąd.

```cpp
wsprintf(szTmp, _T("%d.%2.2d.%4.4d"), rmj, rmm, rup);
```

Makro \_T ma wpływ na wykonanie doskomplkowania literału ciągu jako ciągu **char** lub **ciągu wchar_t,** w zależności od ustawienia MBCS lub UNICODE. Aby zastąpić wszystkie \_ciągi T w programie Visual Studio, najpierw otwórz pole **Szybkie zastępowanie** (klawiatura: **Ctrl**+**F)** lub **Zamień w plikach** (klawiatura: **Ctrl**+**Shift**+**H),** a następnie wybierz pole wyboru Użyj **wyrażeń regularnych.** Wprowadź `((\".*?\")|('.+?'))` jako tekst `_T($1)` wyszukiwania i jako tekst zastępczy. Jeśli masz już \_makro T wokół niektórych ciągów, ta procedura doda go ponownie, a \_także może znaleźć `#include`przypadki, w których nie chcesz T, na przykład podczas korzystania , więc najlepiej jest użyć **Zamień następny,** a nie **Zastąp wszystko**.

Ta szczególna funkcja, [wsprintf](/windows/win32/api/winuser/nf-winuser-wsprintfw), jest faktycznie zdefiniowana w nagłówkach systemu Windows, a dokumentacja dla niej zaleca, aby nie była używana ze względu na możliwe przepełnienie buforu. Nie podano rozmiaru `szTmp` dla buforu, więc nie ma możliwości, aby funkcja sprawdzała, czy bufor może przechowywać wszystkie dane, które mają zostać zapisane. Zobacz następną sekcję dotyczącą przenoszenia do bezpiecznego crt, w którym możemy rozwiązać inne podobne problemy. Skończyło się na zastąpieniu go [_stprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md).

Innym częstym błędem, który zobaczysz podczas konwersji na Unicode, jest to.

```Output
error C2440: '=': cannot convert from 'char *' to 'TCHAR *'
```

Kod, który produkuje jest następujący:

```cpp
pParentNode->m_szText = new char[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

Mimo że `_tcscpy` funkcja została użyta, która jest TCHAR strcpy funkcji kopiowania ciągu, bufor, który został przydzielony był bufor **char.** Można to łatwo zmienić na TCHAR.

```cpp
pParentNode->m_szText = new TCHAR[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

Podobnie zmieniliśmy LPSTR (Long Pointer do STRing) i LPCSTR (Long Pointer do Constant STRing) odpowiednio na LPTSTR (Long Pointer to TCHAR STRing) i LPCTSTR (Long Pointer to Constant TCHAR STRing), gdy jest to uzasadnione błędem kompilatora. Zdecydowaliśmy się nie dokonywać takich zamienników za pomocą globalnego wyszukiwania i zastępowania, ponieważ każda sytuacja musiała być badana indywidualnie. W niektórych przypadkach wersja **char** jest pożądana, na przykład podczas przetwarzania niektórych komunikatów systemu Windows, które używają struktur systemu Windows, które mają sufiks **A.** W interfejsie API systemu Windows sufiks **A** oznacza ASCII lub ANSI (a także dotyczy MBCS), a przyrostek **W** oznacza szerokie znaki lub UTF-16 Unicode. Ten wzorzec nazewnictwa jest używany w nagłówkach systemu Windows, ale śledziliśmy go również w kodzie Spy++, gdy musieliśmy dodać wersję Unicode funkcji, która została już zdefiniowana tylko w wersji MBCS.

W niektórych przypadkach musieliśmy zastąpić typ, aby użyć wersji, która jest rozpoznawana poprawnie (WNDCLASS zamiast WNDCLASSA na przykład).

W wielu przypadkach musieliśmy użyć ogólnej wersji (makro) interfejsu `GetClassName` API Win32, takiej jak (zamiast `GetClassNameA`). W instrukcji przełącznika obsługi komunikatów niektóre komunikaty są specyficzne dla MBCS lub Unicode, w tych przypadkach musieliśmy zmienić kod, aby jawnie wywołać wersję MBCS, ponieważ zastąpiliśmy ogólnie nazwane funkcje określonymi funkcjami **A** i **W** i dodaliśmy makro dla nazwy ogólnej, która rozwiązuje poprawną nazwę **A** lub **W** na podstawie tego, czy unicode jest zdefiniowany.  W wielu częściach kodu, gdy przełączyliśmy \_się do definiowania UNICODE, wersja W jest teraz wybierana nawet wtedy, gdy wersja **A** jest tym, czego jest pożądane.

Jest kilka miejsc, w których trzeba było podjąć specjalne działania. Jakiekolwiek użycie `WideCharToMultiByte` `MultiByteToWideChar` lub wykorzystanie lub może wymagać bliższego przyjrzenia się. Oto jeden z `WideCharToMultiByte` przykładów, gdzie był używany.

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

Aby rozwiązać ten problem, musieliśmy zrozumieć, że powodem tego było skopiowanie szerokiego ciągu znaków reprezentującego nazwę czcionki do wewnętrznego buforu `CString`. `strFace` Wymagało to nieco inny kod `CString` dla ciągów `CString` wielobajtowych, `#ifdef` jak dla ciągów znaków szerokich, więc dodaliśmy w tym przypadku.

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

Oczywiście, zamiast naprawdę `wcscpy` powinniśmy `wcscpy_s`używać , bardziej bezpieczna wersja. Następna sekcja dotyczy tego problemu.

W celu sprawdzenia naszej pracy, powinniśmy zresetować **zestaw znaków** do korzystania z zestawu **znaków multibajtów** i upewnij się, że kod nadal kompiluje przy użyciu MBCS, a także Unicode. Nie trzeba dodawać, że pełne wykonanie testu powinno być wykonane w ponownej kompilacji aplikacji po tych wszystkich zmianach.

W naszej pracy z tym rozwiązaniem Spy++ zajęło około dwóch dni roboczych dla przeciętnego dewelopera Języka C++, aby przekonwertować kod na Unicode. Nie obejmowało to czasu ponownego testowania.

## <a name="step-12-porting-to-use-the-secure-crt"></a><a name="porting_to_secure_crt"></a>Krok 12. Przenoszenie w celu korzystania z bezpiecznego CRT

Następnie jest kolejnym przeniesieniem kodu w celu użycia bezpiecznych wersji (wersji z **_s** sufiksem) funkcji CRT. W takim przypadku ogólną strategią jest zastąpienie funkcji **wersją _s,** a następnie zwykle dodawanie wymaganych dodatkowych parametrów rozmiaru buforu. W wielu przypadkach jest to proste, ponieważ rozmiar jest znany. W innych przypadkach, gdy rozmiar nie jest natychmiast dostępny, konieczne jest dodanie dodatkowych parametrów do funkcji, która używa funkcji CRT lub może zbadać użycie buforu docelowego i zobaczyć, jakie są odpowiednie limity rozmiaru.

Visual C++ zapewnia sztuczkę, aby ułatwić uzyskanie kodu bezpieczne bez dodawania jak najwięcej parametrów rozmiaru, i to za pomocą przeciążenia szablonu. Ponieważ te przeciążenia są szablonami, są one dostępne tylko podczas kompilowania jako C++, a nie jako C. Spyxxhk jest projektem C, więc sztuczka nie będzie działać.  Jednak Spyxx nie jest i możemy użyć sztuczki. Sztuką jest dodanie takiej linii w miejscu, w którym zostanie ona skompilowana w każdym pliku projektu, takim jak w stdafx.h:

```cpp
#define _CRT_SECURE_TEMPLATE_OVERLOADS 1
```

Podczas definiowania, że zawsze, gdy bufor jest tablicą, a nie nieprzetworzony wskaźnik, jego rozmiar jest wywnioskowany z typu tablicy i który jest używany jako parametr size, bez konieczności podaniu go. To pomaga zmniejszyć złożoność przepisywania kodu. Nadal musisz zastąpić nazwę funkcji **wersją _s,** ale często można to zrobić za pomocą operacji wyszukiwania i zastępowania.

Wartości zwracane niektórych funkcji uległy zmianie. Na przykład `_itoa_s` (i `_itow_s` makro `_itot_s`) zwraca kod`errno_t`błędu ( ), a nie ciąg. W takich przypadkach należy przenieść wywołanie `_itoa_s` do oddzielnego wiersza i zastąpić je identyfikatorem buforu.

Niektóre z typowych `memcpy`przypadków: w `memcpy_s`przypadku , podczas przełączania się do , często dodaliśmy rozmiar kopiowanej struktury. Podobnie dla większości ciągów i buforów rozmiar tablicy lub buforu można łatwo określić na podstawie deklaracji buforu lub przez znalezienie, gdzie bufor został pierwotnie przydzielony. W niektórych sytuacjach należy określić, jak duży bufor jest rzeczywiście dostępny, a jeśli te informacje nie są dostępne w zakresie funkcji, która modyfikujesz, należy dodać jako dodatkowy parametr i kod wywołujący powinny być modyfikowane w celu dostarczenia informacji.

Dzięki tym technikom konwersja kodu do korzystania z bezpiecznych funkcji CRT zajęła około pół dnia. Jeśli nie zdecydujesz się na przeciążenia szablonu i ręcznie dodać parametry rozmiaru, prawdopodobnie zajmie to dwa lub trzy razy więcej czasu.

## <a name="step-13-zcforscope--is-deprecated"></a><a name="deprecated_forscope"></a>Krok 13. /Zc:forScope- jest przestarzały

Ponieważ Visual C++ 6.0 kompilator jest zgodny z bieżącą normą, która ogranicza zakres zmiennych zadeklarowanych w pętli do zakresu pętli. Opcja kompilatora [/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) (**Wymuś zgodność dla zakresu pętli** we właściwościach projektu) określa, czy jest to zgłaszane jako błąd. Powinniśmy zaktualizować nasz kod, aby być zgodny i dodać deklaracje tuż poza pętlą. Aby uniknąć wprowadzania zmian w kodzie, **Language** można zmienić to ustawienie w `No (/Zc:forScope-)`sekcji Język właściwości projektu C++ na . Należy jednak pamiętać, `/Zc:forScope-` że może zostać usunięty w przyszłej wersji języka Visual C++, więc ostatecznie kod będzie musiał zmienić, aby były zgodne ze standardem.

Te problemy są stosunkowo łatwe do naprawienia, ale w zależności od kodu może mieć wpływ na wiele kodu. Oto typowy problem.

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

Dzieje się tak, ponieważ kompilator ma przestarzałe opcji kompilatora, który pozwolił na kod, który nie jest już zgodny ze standardem C++. W standardzie deklarowanie zmiennej wewnątrz pętli ogranicza jej zakres tylko do pętli, więc powszechną praktyką używania licznika pętli poza pętlą wymaga, aby deklaracja licznika również została przeniesiona poza pętlę, jak w poniższym zmienionym kodzie:

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

Przenoszenie Spy++ z oryginalnego kodu Visual C++ 6.0 do najnowszego kompilatora zajęło około 20 godzin czasu kodowania w ciągu około tygodnia. Uaktualniliśmy bezpośrednio przez osiem wersji produktu z programu Visual Studio 6.0 do programu Visual Studio 2015. Jest to obecnie zalecane podejście dla wszystkich uaktualnień w projektach dużych i małych.

## <a name="see-also"></a>Zobacz też

[Przenoszenie i uaktualnianie: Przykłady i analizy przypadków](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Poprzednie studium przypadku: COM Spy](../porting/porting-guide-com-spy.md)
