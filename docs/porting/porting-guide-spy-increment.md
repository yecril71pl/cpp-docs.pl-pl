---
title: "Przewodnik przenoszenia: Narzędzie Spy ++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: e558f759-3017-48a7-95a9-b5b779d5e51d
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5043e77826e2210f45b70d564313ae6fd976d93a
ms.sourcegitcommit: 56f6fce7d80e4f61d45752f4c8512e4ef0453e58
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2018
---
# <a name="porting-guide-spy"></a>Przewodnik przenoszenia: Narzędzie Spy++
Przenoszenia w tej analizie przypadku zaprojektowano w celu daje wyobrażenie o jakie typowe projektu przenoszenia przypomina, jakiego rodzaju problemy mogą wystąpić i pewne ogólne porady i wskazówki dotyczące przenoszenia problemów. Nie ma mają być wyczerpujący do przenoszenia, ponieważ środowisko eksportowanie projekt zależy od znacznie szczegółowe informacje na temat kodu.  
  
## <a name="spy"></a>Spy++  
 Spy ++ jest powszechnie używane narzędzie diagnostyczne graficznego interfejsu użytkownika dla komputerów z systemem Windows, który zawiera wszystkie rodzaje informacji na temat elementów interfejsu użytkownika na pulpicie systemu Windows. Pokazuje pełną hierarchii systemu windows i udostępnia metadane dotyczące każdej okna i kontrolki. Ta aplikacja przydatne została wysłana z programu Visual Studio przez wiele lat. Znaleziono starą wersję jej ostatniej został skompilowany w programie Visual C++ 6.0 i przenieść go do programu Visual Studio 2015. Środowisko dla programu Visual Studio 2017 powinny być niemal identyczne.
  
 Firma Microsoft uznawane za przypadek być typowe przy eksportowaniu Windows aplikacji klasycznych, które Użyj MFC i interfejs API Win32, szczególnie w przypadku starych projektów, które nie zostały zaktualizowane w poszczególnych wersjach Visual C++ od czasu Visual C++ 6.0.  
  
##  <a name="convert_project_file"></a>Krok 1. Konwertowanie pliku projektu.  
 Plik projektu, dwa stare pliki .dsw programu Visual C++ 6.0, łatwo przekonwertowany bez problemów wymagających dalszej uwagi. Jeden projekt jest aplikacją Spy ++. Druga to SpyHk napisane w języku C, pomocnicze biblioteki DLL. Bardziej złożone projektów nie może uaktualnić równie łatwo, zgodnie z opisem [tutaj](../porting/visual-cpp-porting-and-upgrading-guide.md).  
  
 Po uaktualnieniu dwa projekty Nasze rozwiązanie po zapoznaniu się następująco:  
  
 ![Spy &43; &#43; Rozwiązanie](../porting/media/spyxxsolution.PNG "SpyxxSolution")  
  
 Mamy dwa projekty, jeden z dużą liczbą plików C++, a drugi bibliotekę DLL, która została napisana C.  
  
##  <a name="header_file_problems"></a>Krok 2. Problemy z pliku nagłówka  
 Podczas kompilowania projektu nowo przekonwertowane, jest jedną z pierwszych rzeczy, które często okazuje się, nie znaleziono pliki nagłówkowe, które korzysta z projektu.  
  
 Jeden z plików, których nie można znaleźć w programie Spy ++ jest verstamp.h. Z wyszukiwaniem w Internecie Ustaliliśmy to pochodzeniu DAO SDK technologii przestarzałe dane. Możemy dowiedzieć się, jakie symbole były używane z tego pliku nagłówka, czy ten plik został naprawdę potrzebne lub jeśli te symbole zostały zdefiniowane w innym miejscu, możemy komentarzami deklaracji pliku nagłówka i ponownie kompilowana. Monitor przechodzi w stan tam jest tylko jeden symbol, który jest potrzebny w VER_FILEFLAGSMASK.  
  
```  
1>C:\Program Files (x86)\Windows Kits\8.1\Include\shared\common.ver(212): error RC2104: undefined keyword or key name: VER_FILEFLAGSMASK  
```  
  
 Najprostszym sposobem sprawdzenia symbolu w plikach dostępne include jest za pomocą narzędzia Znajdź w plikach (Ctrl + Shift + F) i określ **Visual C++ katalogi dołączenia**. Znaleziono go w ntverp.h. Możemy zastąpić verstamp.h dołączone ntverp.h i zniknęła tego błędu.  
  
##  <a name="linker_output_settings"></a>Krok 3. Ustawienie OutputFile konsolidatora  
 Starsze projekty mają czasami pliki umieszczone w niekonwencjonalnym lokalizacje, które mogą być przyczyną problemów po uaktualnieniu. W takim przypadku mamy do dodania do ścieżki dołączania we właściwościach projektu, aby upewnić się, że program Visual Studio można znaleźć niektóre pliki nagłówkowe, które są umieszczane w, a nie w jednym z folderów projektu $(SolutionDir).  
  
 MSBuild narzeka, że właściwość Link.OutputFile nie pasuje do wartości TargetPath i TargetName wystawiania MSB8012.  
  
```Output  
warning MSB8012: TargetPath(...\spyxx\spyxxhk\.\..\Debug\SpyxxHk.dll) does not match the Linker's OutputFile property value (...\spyxx\Debug\SpyHk55.dll). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).warning MSB8012: TargetName(SpyxxHk) does not match the Linker's OutputFile property value (SpyHk55). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).  
```  
  
 **Link.OutputFile** jest danych wyjściowych kompilacji (EXE, DLL, na przykład) i zazwyczaj jest tworzony z $(TargetDir)$(TargetName)$(TargetExt), podając ścieżkę, nazwa pliku i rozszerzenia. To jest typowym błędem podczas migrowania projektów ze starego Visual C++ kompilacji narzędzia (vcbuild.exe) nowego narzędzia kompilacji (MSBuild.exe). Ponieważ narzędzie kompilacji zmiana została wprowadzona w programie Visual Studio 2010, może wystąpić ten problem, gdy migracji projektu pre-2010 2010 lub nowszej wersji. Podstawowy problem jest, że Kreator migracji projektu nie powoduje aktualizacji **Link.OutputFile** wartości, ponieważ nie zawsze jest możliwe określenie, jakie wartości powinny być oparte na ustawieniach projektu. W związku z tym zazwyczaj należy ustawić ją ręcznie. Aby uzyskać więcej informacji, zobacz [post](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx) na blogu Visual C++.  
  
 W takim przypadku **Link.OutputFile** ustawiono właściwość w przekonwertowanego projektu.\Debug\Spyxx.exe i.\Release\Spyxx.exe dla Spy ++ projektu, w zależności od konfiguracji. Najlepiej po prostu zastąpić te wartości zapisane na stałe $(TargetDir)$(TargetName)$(TargetExt) dla wszystkich konfiguracji. Jeśli to nie zadziała, można dostosować z niej, lub zmienić właściwości w sekcji Ogólne, w którym te wartości są ustawiane (właściwości są **katalog wyjściowy**, **Nazwa docelowego**, i  **Celem rozszerzenia**. Należy pamiętać, że jeśli właściwość wyświetlasz używa makra, można **Edytuj** z listy rozwijanej, aby wyświetlić okno dialogowe zawiera ciąg końcowy z zastępczych makr wprowadzone. Można wyświetlić wszystkie dostępne makra i ich wartości, wybierając **makra** przycisku.  
  
##  <a name="updating_winver"></a>Krok 4. Aktualizowanie docelową wersję systemu Windows  
 Następny błąd wskazuje, że WINVER wersji nie jest już obsługiwana w MFC. Polecenie WINVER dla systemu Windows XP jest 0x0501.  
  
```Output  
C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxv_w32.h(40): fatal error C1189: #error:  MFC does not support WINVER less than 0x0501.  Please change the definition of WINVER in your project properties or precompiled header.  
```  
  
 Windows XP nie jest obsługiwany przez firmę Microsoft, nawet jeśli jego celem jest dozwolone w programie Visual Studio 2015, należy być wycofanie obsługę go w aplikacji i zachęcając użytkowników do przyjęcia nowych wersji systemu Windows.  
  
 Aby pozbyć się tego błędu, należy zdefiniować WINVER aktualizując **właściwości projektu** ustawienie Najniższa wersja systemu Windows, które obecnie ma być docelowa. Znajdź tabelę z wartościami w różnych wersjach systemu Windows [tutaj](http://msdn.microsoft.com/library/windows/desktop/aa383745.aspx).  
  
 Plik stdafx.h zawiera niektóre z tych definicji makra.  
  
```cpp  
#define WINVER       0x0500  // these defines are set so that we get the  
#define _WIN32_WINNT 0x0500  // maximum set of message/flag definitions,  
#define _WIN32_IE    0x0400  // from both winuser.h and commctrl.h.  
  
```  
  
 Polecenie WINVER możemy ustawi do systemu Windows 7. Jest to czytelność kodu później użycie makra w systemie Windows 7 (_WIN32_WINNT_WIN7), zamiast wartości sam (0x0601).  
  
```cpp  
#define WINVER _WINNT_WIN32_WIN7 // Minimum targeted Windows version is Windows 7  
```  
  
##  <a name="linker_errors"></a>Krok 5. Błędy konsolidatora  
 Wprowadzone zmiany kompilacje projektu SpyHk (DLL), ale powoduje błąd konsolidatora.  
  
```  
LINK : warning LNK4216: Exported entry point _DLLEntryPoint@12  
```  
  
 Punkt wejścia biblioteki DLL nie powinien wyeksportowane. Punkt wejścia jest przeznaczona tylko do wywołania przez moduł ładujący, gdy biblioteka DLL najpierw jest ładowany do pamięci, więc nie powinno być w tabeli eksportu jest przeznaczony dla innych klientów. Potrzebujemy upewnij się, że nie ma `__declspec(dllexport)` dyrektywy do niego dołączony. W spyxxhk.c musimy usunąć go z dwóch miejscach deklaracji i definicji DLLEntryPoint. Poprzednie wersje kompilatora i konsolidatora nie Flaga go jako problem, ale nigdy nie składane warto użyć tej dyrektywy. Nowsze wersje konsolidator ostrzeżenie.  
  
```cpp  
// deleted __declspec(dllexport)  
BOOL WINAPI DLLEntryPoint(HINSTANCE hinstDLL,DWORD fdwReason, LPVOID lpvReserved);  
  
```  
  
 Projekt C DLL, SpyHK.dll, teraz kompilacje i łączy bez błędów.  
  
##  <a name="outdated_header_files"></a>Krok 6. Więcej nieaktualne pliki nagłówka  
 W tym momencie Rozpoczniemy roboczych w projekcie głównym pliku wykonywalnego, Spyxx.  
  
 Nie można odnaleźć kilka innych plików dołączanych: ctl3d.h i penwin.h. Podczas może być przydatne do wyszukiwania w Internecie w celu zidentyfikowania co zawarte w nagłówku, czasami informacji nie jest to przydatne. Znaleziono ctl3d.h część zestaw deweloperski programu Exchange i zapewniono obsługę dla stylu kontrolki w systemie Windows 95 i penwin.h odnosi się do okna Pióro obliczeniowych, przestarzałe interfejsu API. W takim przypadku możemy po prostu komentarz #include i postępowania w przypadku Niezdefiniowany symbole, jak robiliśmy z verstamp.h. Wszystkie elementy, które odnoszą się do formantów 3D lub korzystania z pióra został usunięty z projektu.  
  
 Biorąc pod uwagę projekt o wiele błędów kompilacji, które są stopniowo wyeliminowanie, nie jest realistyczne, aby znaleźć wszystkie użycia interfejsu API nieaktualne od razu po usunięciu # dyrektywy include. Firma Microsoft nie wykryć natychmiast, ale raczej na kilka późniejszym dołączone do czy WM_DLGBORDER jest niezdefiniowany błąd. Jest to rzeczywiście tylko jeden wiele niezdefiniowanych symboli, które pochodzą od ctl3d.h. Gdy już Ustaliliśmy, że odnosi się do interfejsu API nieaktualne, usunęliśmy wszystkie odwołania w kodzie do niego.  
  
##  <a name="updating_iostreams_code"></a>Krok 7. Aktualizowanie poprzedni kod iostream  
 Błąd dalej jest często ze starego używa iostream kod w języku C++.  
  
 mstream.h(40): błąd krytyczny C1083: nie można dołączyć Otwórz plik: "iostream.h": Brak pliku lub katalogu  
  
 Problem polega na czy starego biblioteki iostream została usunięta i zastąpione. Mamy Zamień stary iostream nowszej standardów.  
  
```cpp  
#include <iostream.h>  
#include <strstrea.h>  
#include <iomanip.h>  
  
```  
  
 Są to zaktualizowanego obejmuje:  
  
```cpp  
#include <iostream>  
#include <sstream>  
#include <iomanip>  
  
```  
  
 Dzięki tej zmianie mamy problemy z ostrstream —, który nie jest już używana. Zastąpienie odpowiednie jest ostringstream. Spróbujemy Dodawanie typedef dla ostrstream — uniknąć modyfikacji kodu zbyt dużo przynajmniej rozpoczęcia.  
  
```cpp  
typedef std::basic_ostringstream<TCHAR> ostrstream;  
  
```  
  
 Obecnie projekt jest budowany przy użyciu MBCS (wielobajtowego zestawu znaków), więc `char` jest odpowiedni znaków typu danych. Jednak aby umożliwić łatwiejsze aktualizacji kodu Unicode UTF-16, modyfikacjom na `TCHAR`, który jest rozpoznawany jako `char` lub `wchar_t` w zależności od tego, czy **zestaw znaków** ma ustawioną wartość właściwości w ustawieniach projektu MBCS lub Unicode.  
  
 Kilka fragmentów kodu muszą zostać zaktualizowane.  Firma Microsoft zastąpione ios_base — klasa podstawowa dla systemu ios i możemy zastąpić ostream za basic_ostream —\<T >. Dodamy dwa dodatkowe definicje typów i kompiluje w tej sekcji.  
  
```cpp  
typedef std::basic_ostream<TCHAR> ostream;  
typedef ios_base ios;  
  
```  
  
 Używanie te definicje typów jest rozwiązanie tymczasowe. Bardziej trwałego rozwiązania firma Microsoft może zaktualizować każde odwołanie do API nieaktualne lub zmieniono jego nazwę.  
  
 Oto następnego błędu.  
  
```Output  
error C2039: 'freeze': is not a member of 'std::basic_stringbuf<char,std::char_traits<char>,std::allocator<char>>'  
```  
  
 Następny problem jest tym basic_stringbuf — nie ma metody zablokować. Metoda blokowanie służy do uniemożliwiają wyciek pamięci w starym ostream. Nie należy go teraz, firma Microsoft korzysta z nowych ostringstream. Można usunąć połączenia, aby zablokować.  
  
```cpp  
//rdbuf()->freeze(0);  
```  
  
 Następne dwa błędu w wierszach sąsiadujących ze sobą. Pierwszy narzeka o używaniu zakończenia, który jest manipulatora we/wy starego biblioteki iostream, który dodaje terminatorem null na ciąg.  Drugi z tych błędów wyjaśniono, że dane wyjściowe metody str nie można przypisać do wskaźnika z systemem innym niż stała.  
  
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
  
 Przy użyciu nowej biblioteki strumienia, zakończenia nie jest wymagana, ponieważ ciąg jest zawsze zerem, dzięki czemu można usunąć wiersza. Drugi problemu dotyczącego problemu jest to, że teraz str() nie zwraca wskaźnik do tablicy znaków ciągu; Zwraca typ std::string. Rozwiązanie do drugiej jest Zmień typ na LPCSTR i żądania wskaźnik przy użyciu metody c_str().  
  
```cpp  
//*this << ends;  
LPCTSTR psz = str().c_str();  
  
```  
  
 Błąd puzzled nam na chwilę na ten kod.  
  
```cpp  
MOUT << _T(" chUser:'") << chUser  
<< _T("' (") << (INT)(UCHAR)chUser << _T(')');  
  
```  
  
 Makro `MOUT` jest rozpoznawana jako * g_pmout, który jest obiektem typu `mstream`. Klasa mstream pochodzi od klasy ciągu wyjścia standardowego, `std::basic_ostream<TCHAR>.` jednak z _t — wokół literał, która testujemy w ramach przygotowania do konwersji na format Unicode, Rozpoznanie przeciążenia operatora << kończy się niepowodzeniem z powodu następującego błędu Komunikat:  
  
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
  
 Istnieje wiele operator << definicje, że taki błąd może mieć OPORY. Po dokładniejsze patrzeć dostępne przeciążenia, zobaczysz, że większość z nich są bez znaczenia i wyglądającej dokładniejsze na `mstream` klasy definicji, określiliśmy, że następująca funkcja, która naszym zdaniem powinien zostać wywołany w takim przypadku.  
  
```cpp  
mstream& operator<<(LPTSTR psz)  
{  
  return (mstream&)ostrstream::operator<<(psz);  
}  
  
```  
  
 Przyczyna nie jest ona wywoływana jest ponieważ literału ciągu ma typ `const wchar_t[10]` jak widać w ostatnim wierszu długi ekranie komunikatu o błędzie, więc konwersji do wskaźnik-const nie jest automatyczna. Jednak ten operator nie należy modyfikować parametru wejściowego, bardziej odpowiednie typ parametru jest LPCTSTR (`const char*` podczas kompilowania jako MBCS, i `const wchar_t*` jako Unicode), nie LPTSTR (`char*` podczas kompilowania jako MBCS, i `wchar_t*` jako Unicode). Wprowadzenie tej zmiany rozwiązuje ten błąd.  
  
 Ten typ konwersji jest dozwolone w obszarze kompilatora starszej, mniej rygorystyczne, ale nowsze zmiany zgodności wymaga więcej prawidłowego kodu.  
  
##  <a name="stricter_conversions"></a>Krok 8. Konwersje ściślejsze kompilatora  
 Możemy również uzyskać wiele błędów podobne do następujących:  
  
```  
error C2440: 'static_cast': cannot convert from 'UINT (__thiscall CHotLinkCtrl::* )(CPoint)' to 'LRESULT (__thiscall CWnd::* )(CPoint)'  
```  
  
 Błąd w mapie komunikat, który jest po prostu makra:  
  
```cpp  
BEGIN_MESSAGE_MAP(CFindToolIcon, CWnd)  
// other messages omitted...  
ON_WM_NCHITTEST() // Error occurs on this line.  
END_MESSAGE_MAP()  
```  
  
 Przechodzenie do definicji to makro, możemy znaleźć odwołuje się funkcja OnNcHitTest.  
  
```cpp  
#define ON_WM_NCHITTEST() \  
{ WM_NCHITTEST, 0, 0, 0, AfxSig_l_p, \  
(AFX_PMSG)(AFX_PMSGW) \  
(static_cast< LRESULT (AFX_MSG_CALL CWnd::*)(CPoint) > (&ThisClass :: OnNcHitTest)) },  
```  
  
 Problem jest związany z niezgodność wskaźnika do elementu członkowskiego typów funkcji. Problem nie jest konwersja z CHotLinkCtrl jako typ klasy CWnd jako typ klasy, ponieważ jest prawidłowa konwersja pochodnych do podstawowego. Problem jest typ zwracany: UINT vs. ELEMENTU LRESULT. Jest rozpoznawany jako elementu LRESULT LONG_PTR, który jest wskaźnik 64-bitowych lub wskaźnik 32-bitowy, w zależności od typu binarnego docelowej, UINT nie konwertuje do tego typu. To nie jest nietypowa sytuacja podczas uaktualniania kod napisany przed 2005, ponieważ zwracany typ metody mapy wiadomości wiele zmieniony z UINT na elementu LRESULT w programie Visual Studio 2005 jako część zmiany zgodności 64-bitowych. Możemy zmienić zwracany typ z UINT w poniższym kodzie elementu LRESULT:  
  
```cpp  
afx_msg UINT OnNcHitTest(CPoint point);  
```  
  
 Po zmianie mamy następujący kod:  
  
```cpp  
afx_msg LRESULT OnNcHitTest(CPoint point);  
```  
  
 Ponieważ około dziesięciu wystąpień tej funkcji w różnych klas pochodnych CWnd, warto użyć **przejdź do definicji** (klawiatury: F12) i **przejdź do deklaracji** (klawiatury: Ctrl + F12) po kursor jest w funkcji w edytorze, aby znaleźć te i przechodzić do nich z **Znajdź Symbol** okna narzędzia. **Przejdź do definicji** jest zazwyczaj bardziej użyteczna dwóch. **Przejdź do deklaracji** będzie deklaracji Znajdź niż definiowanie deklaracji, takich jak klasy deklaracje funkcji friend klasy lub przekazywania odwołań.  
  
##  <a name="mfc_changes"></a>Krok 9. Zmiany MFC  
 Następny błąd również odnosi się do typu deklaracji zmienione i występuje także w makrze.  
  
```Output  
error C2440: 'static_cast': cannot convert from 'void (__thiscall CFindWindowDlg::* )(BOOL,HTASK)' to 'void (__thiscall CWnd::* )(BOOL,DWORD)'  
```  
  
 Problem polega na tym, czy drugi parametr CWnd::OnActivateApp zmieniła się z HTASK do typu DWORD. Ta zmiana została wprowadzona w wersji 2002 programu Visual Studio, Visual Studio .NET.  
  
```cpp  
afx_msg void OnActivateApp(BOOL bActive, HTASK hTask);  
```  
  
 Konieczne jest uaktualnienie deklaracji OnActivateApp w klasach pochodnych odpowiednio w następujący sposób:  
  
```cpp  
afx_msg void OnActivateApp(BOOL bActive, DWORD dwThreadId);  
```  
  
 W tym momencie możemy skompilować projekt. Istnieje kilka ostrzeżeń do pracy, jednak i są opcjonalne części uaktualnienia, takie jak konwertowania MBCS na Unicode lub ulepszania zabezpieczeń przy użyciu funkcji CRT bezpieczny.  
  
##  <a name="compiler_warnings"></a>Krok 10. Adresowanie ostrzeżeń kompilatora  
 Aby uzyskać pełną listę ostrzeżeń, należy wykonać **rekompilacji wszystkiego** rozwiązania zamiast zwykłego kompilacji, tak, aby upewnić się, że wszystkie zasoby, które wcześniej skompilowany zostanie ponownie skompilowana, ponieważ tylko pobierają ostrzeżenie raporty z bieżącego kompilacji. Inne pytanie jest może akceptować bieżący poziom ostrzeżenia lub użyj wyższy poziom ostrzeżenia.  Eksportowanie dużej ilości kodu, szczególnie poprzedni kod przy użyciu wyższy poziom ostrzeżeń może być odpowiednie.  Można także uruchomić z domyślnym poziomem ostrzeżeń i dopiero potem zwiększyć poziom ostrzeżeń, aby wyświetlić wszystkie ostrzeżenia. Jeśli używasz/Wall, otrzymujesz ostrzeżenia w systemie pliki nagłówkowe, tak wielu użytkowników użyj/W4, aby uzyskać większości ostrzeżenia na kodzie bez uzyskiwania ostrzeżenia dla nagłówków systemu. Jeśli chcesz ostrzeżenia jako błędy wyświetlone dodać opcji wx. Te ustawienia są w sekcji C/C++ okna dialogowego właściwości projektu.  
  
 Jedną z metod w klasie CSpyApp generuje ostrzeżenie dotyczące funkcji, która nie jest już obsługiwana.  
  
```cpp  
void SetDialogBkColor() {CWinApp::SetDialogBkColor(::GetSysColor(COLOR_BTNFACE));}  
```  
  
 Ostrzeżenie ma następującą składnię.  
  
```Output  
warning C4996: 'CWinApp::SetDialogBkColor': CWinApp::SetDialogBkColor is no longer supported. Instead, handle WM_CTLCOLORDLG in your dialog  
```  
  
 Komunikat WM_CTLCOLORDLG już został obsłużony w kodzie Spy ++, tylko zmiany wymagane było usunąć wszystkie odwołania do SetDialogBkColor, które nie są już potrzebne.  
  
 Ostrzeżenie następnym został prostego rozwiązać komentowania limit nazwę zmiennej. Otrzymaliśmy następujące ostrzeżenie:  
  
```Output  
warning C4456: declaration of 'lpszBuffer' hides previous local declaration  
```  
  
 Kod, który daje to obejmuje makra.  
  
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
  
 Zwykle intensywnie korzysta z makra, tak jak ten kod być trudniejsze do obsługi kodu. W takim przypadku dostępne są następujące makra deklaracji zmiennych. Makro PARAMETR jest zdefiniowany w następujący sposób:  
  
```cpp  
#define PARM(var, type, src)type var = (type)src  
```  
  
 W związku z tym zmienna lpszBuffer pobiera zadeklarowana dwa razy w tej samej funkcji. Nie jest tym straightfoward, aby rozwiązać ten problem, tak jak Jeśli kod nie były używane makra (po prostu usuń drugi deklaracji typu). Jak mamy niefortunne wybór konieczności zdecyduj, czy ponownego pisania kodu makra jako kod zwykłej (zadanie żmudnego i prawdopodobnie podatnych) lub wyłącz ostrzeżenia.  
  
 W takim przypadku możemy zdecydować się na wyłączenie ostrzeżenia. Firma Microsoft można to zrobić, dodawanie pragma w następujący sposób:  
  
```cpp  
#pragma warning(disable : 4456)  
```  
  
 Po wyłączeniu ostrzeżenie, można ograniczyć wyłączenie efektu tylko kod możesz tworzącego ostrzeżenia, aby uniknąć pomijanie ostrzeżenia, gdy może udostępnić przydatne informacje. Nie możemy Dodaj kod, aby przywrócić ostrzeżenia zaraz po wierszu, który tworzy go lub jeszcze lepiej, ponieważ to ostrzeżenie występuje w makrze, użyć `__pragma` — słowo kluczowe, które działa w makrach (`#pragma` nie działa w makrach).  
  
```cpp  
#define PARM(var, type, src)__pragma(warning(disable : 4456))  \  
type var = (type)src \  
__pragma(warning(default : 4456))  
  
```  
  
 Ostrzeżenie następnym wymaga niektóre poprawki kodu. GetVersion interfejsu API systemu Win32 (i GetVersionEx) jest przestarzały.  
  
```Output  
warning C4996: 'GetVersion': was declared deprecated  
```  
  
 Poniższy kod przedstawia sposób uzyskiwania wersji.  
  
```cpp  
// check Windows version and set m_bIsWindows9x/m_bIsWindows4x/m_bIsWindows5x flags accordingly.  
DWORD dwWindowsVersion = GetVersion();  
  
```  
  
 To następuje wiele kodu, który sprawdza, czy wartość dwWindowsVersion, aby ustalić, czy Prowadzimy w systemie Windows 95 i wersji systemu Windows NT. Ponieważ jest to wszystko, przestarzałe, możemy usunąć kod i rozwiązać wszelkie odwołania do tych zmiennych.  
  
 Artykuł [zmiany wersji systemu operacyjnego Windows 8.1 i Windows Server 2012 R2](https://msdn.microsoft.com/library/windows/desktop/dn302074.aspx) wyjaśniono sytuacji.  
  
 Przy użyciu metod w klasie CSpyApp zapytania wersji systemu operacyjnego: IsWindows9x, IsWindows4x i IsWindows5x. Dobry punkt wyjścia dojść do wniosku, że wersje systemu Windows, które mają obsługuje (z systemem Windows 7 i nowsze) są wszystkie Zamknij, aby zainteresowanym systemu Windows NT 5 jako daleko technologie, które są używane w tym starszych aplikacji. Korzysta z tych metod zostały radzenia sobie z ograniczenia starszych systemów operacyjnych. Dlatego możemy zmienić tych metod, aby zwrócić wartość TRUE dla IsWindows5x i wartość FALSE dla pozostałych.  
  
```cpp  
BOOL IsWindows9x() {/*return(m_bIsWindows9x);*/ return FALSE;  }  
BOOL IsWindows4x() {/*return(m_bIsWindows4x);*/ return FALSE;  }  
BOOL IsWindows5x() {/*return(m_bIsWindows5x);*/ return TRUE;  }  
  
```  
  
 Który pozostanie tylko kilku miejscach, w którym wewnętrzne zmienne zostały użyte bezpośrednio. Ponieważ firma Microsoft usunęła tych zmiennych, uzyskujemy kilka błędów, które zajmują się jawnie.  
  
```Output  
error C2065: 'm_bIsWindows9x': undeclared identifier  
```  
  
```cpp  
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)  
{  
  pCmdUI->Enable(m_bIsWindows9x || hToolhelp32 != NULL);  
}  
  
```  
  
 Firma Microsoft może Zastąp to wywołanie metody lub po prostu Przekaż wartość PRAWDA i Usuń stare szczególnych przypadkach dla systemu Windows 9 x.  
  
```cpp  
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)  
{  
  pCmdUI->Enable(TRUE /*!m_bIsWindows9x || hToolhelp32 != NULL*/);  
}  
  
```  
  
 Końcowe ostrzeżenia na poziomie domyślnym (3) jest związany z bitfield.  
  
```Output  
treectl.cpp(1656): warning C4463: overflow; assigning 1 to bit-field that can only hold values from -1 to 0  
```  
  
 Kod, który wyzwala to wygląda następująco:  
  
```cpp  
m_bStdMouse = TRUE;  
```  
  
 Deklaracja m_bStdMouse oznacza, że jest bitfield.  
  
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
  
 Ten kod został zapisany zanim typu bool wbudowanych jest obsługiwana w programie Visual C++. W takich kodu BOOL została typedef dla int. Typ int jest poziomu typu ze znakiem i reprezentacja bitowej podpisanej int jest użycie pierwszy bit jako bitem, więc bitfield typu int można zinterpretować jako reprezentujący 0 albo -1, co prawdopodobnie nie jest przeznaczona.  
  
 Nie wiesz, sprawdzając kod dlaczego są pola bitów. Został zamiarem zachowywanie małych rozmiarów rozmiar obiektu lub istnieje już wszędzie gdzie są używane binarne układ obiektu? Zmieniony firma Microsoft, te zwykłej członkom BOOL od nie widzimy z jakiegokolwiek powodu bitfield do użytku. Użycie pola bitów, aby zapewnić mały rozmiar obiektu nie jest gwarantowana do pracy. To zależy od sposobu kompilator wychodzi poza typu.  
  
 Być może zastanawiasz się, jeśli przy użyciu bool standardowej w całym mogą być przydatne w. Wiele starego wzorce kodu podobne typu BOOL zostały utworzoną do rozwiązywania problemów, które później zostały rozwiązane w standard C++, więc zmiana z BOOL na typ wbudowany bool jest tylko jeden przykład takie zmiany, rozważ czynności po uzyskaniu początkowo uruchamiania kodu w nowej wersji.  
  
 Po możemy zostały omówione wszystkie ostrzeżenia, które pojawiają się na poziomie domyślnym (poziom 3), możemy zmienić poziom 4, aby przechwycić kilka dodatkowych ostrzeżeń. Pierwszy pojawią się to w następujący sposób:  
  
```Output  
warning C4100: 'nTab': unreferenced formal parameter  
```  
  
 Kod wytworzonego to ostrzeżenie jest w następujący sposób.  
  
```cpp  
virtual void OnSelectTab(int nTab) {};  
```  
  
 Prawdopodobnie dostatecznie bezpieczna, ale ponieważ możemy czystą kompilacji z zestawu/W4 i wx firma Microsoft po prostu oznaczone jako komentarz nazwę zmiennej, pozostawiając go dla czytelności.  
  
```cpp  
virtual void OnSelectTab(int /*nTab*/) {};  
```  
  
 Inne ostrzeżenia, które odebrano były przydatne oczyszczania ogólne kodu. Istnieje wiele niejawną konwersję z `int` lub `unsigned int` do `WORD` (czyli element typedef dla `unsigned short`). Jest to związane z utratą danych. Dodaliśmy Rzutowanie na `WORD` w tych przypadkach.  
  
 To ostrzeżenie inny poziom 4 dotarliśmy dla tego kodu:  
  
```Output  
warning C4211: nonstandard extension used: redefined extern to static  
```  
  
 Problem występuje, gdy najpierw została zadeklarowana zmienna `extern`, później zadeklarowany `static`. Znaczenie tych dwóch specyfikatory klas magazynu jest wykluczają się wzajemnie, ale jest to dozwolone jako rozszerzenie firmy Microsoft. Potrzebujesz przenośne do inne kompilatory kodu, czy chcesz go skompilować z /Za (zgodność ANSI), zmienią deklaracjach mieć pasujące specyfikatory klas magazynu.  
  
##  <a name="porting_to_unicode"></a>Krok 11. Eksportowanie z MBCS na Unicode

 Należy pamiętać, że w środowisku Windows podczas mówimy Unicode, możemy zazwyczaj oznacza UTF-16. Inne systemy operacyjne, takie jak Linux używać UTF-8, ale systemu Windows zazwyczaj nie. Wersja MFC MBCS została uznana za przestarzałą w programie Visual Studio 2013 i 2015, ale nie jest już przestarzały w programie Visual Studio 2017 r. Jeśli przy użyciu programu Visual Studio 2013 lub 2015, przed wykonaniem kroku do faktycznie portu kodu MBCS na Unicode UTF-16, firma Microsoft może być tymczasowo wyeliminować ostrzeżenia, że MBCS jest przestarzały, aby możliwe było wykonywanie innych zadań lub odłożyć eksportowanie czasu wygodny. Bieżący kod używa MBCS i aby kontynuować, musimy zainstalować wersję MFC ANSI/MBCS. Zamiast dużej bibliotece MFC nie jest częścią domyślnej programu Visual Studio **tworzenia klasycznych aplikacji w języku C++** instalacji, więc musi być zaznaczone z opcjonalne składniki w Instalatorze. Zobacz [MFC MBCS DLL dodatku](../mfc/mfc-mbcs-dll-add-on.md). Gdy to Pobierz i uruchom ponownie program Visual Studio, można skompilować i połączyć z wersją MFC MBCS, ale aby pozbyć się ostrzeżenia o MBCS — Jeśli używasz programu Visual Studio 2013 lub 2015, należy również dodać **NO_WARN_MBCS_MFC_DEPRECATION**do listy wstępnie zdefiniowanego makra w sekcji preprocesora właściwości projektu, lub na początku pliku nagłówka stdafx.h lub inne typowe pliku nagłówka.  
  
 Mamy teraz błędy konsolidatora.  
  
```Output  
fatal error LNK1181: cannot open input file 'mfc42d.lib'  
```  
  
 LNK1181 występuje, ponieważ wersja nieaktualne biblioteką statyczną mfc znajduje się na konsolidatora danych wejściowych. Nie jest to wymagane już, ponieważ firma Microsoft może połączyć MFC dynamicznie, więc musimy usunąć wszystkie biblioteki statycznej MFC z właściwości danych wejściowych w sekcji konsolidatora właściwości projektu. Ten projekt jest również przy użyciu opcji/nodefaultlib, a zamiast tego zawiera listę wszystkich zależności biblioteki.  
  
```  
msvcrtd.lib;msvcirtd.lib;kernel32.lib;user32.lib;gdi32.lib;advapi32.lib;Debug\SpyHk55.lib;%(AdditionalDependencies)  
```  
  
 Daj nam faktycznie aktualizowania poprzedni kod wielobajtowego ustawić znaków (MBCS) na ciąg Unicode. Ponieważ jest to aplikacji systemu Windows, ściśle powiązana z platformy pulpitu systemu Windows, firma Microsoft będzie portu na Unicode UTF-16, który korzysta z systemu Windows. Jeśli piszesz kod obsługujący wiele platform lub przenoszenie aplikacji systemu Windows do innej platformy, należy wziąć pod uwagę eksportowanie do UTF-8, który jest powszechnie używany w innych systemach operacyjnych.  
  
 Eksportowanie do Unicode UTF-16, możemy należy zdecydować, czy nadal chcemy opcję, aby skompilować do MBCS, czy nie.  Jeśli chcemy mieć możliwość obsługi MBCS powinniśmy skorzystać tchar — makro jako typ znak, który jest rozpoznawany jako albo `char` lub `wchar_t`, w zależności od tego, czy _MBCS lub _unicode — jest zdefiniowany podczas kompilowania. Przełączanie do tchar — i tchar — wersje różnych interfejsach API zamiast `wchar_t` i jego skojarzone interfejsy API oznacza, że możesz wrócić do wersji MBCS kodu za pomocą Definiowanie makro _MBCS zamiast _unicode —. Oprócz tchar — istnieje wiele wersji tchar — takie jak definicje typów powszechnie używane, makra i funkcje. Na przykład LPCTSTR zamiast LPCSTR i tak dalej. W oknie dialogowym właściwości projektu w obszarze **właściwości konfiguracji**w **ogólne** Zmień **zestaw znaków** właściwość z **Użyj MBCS Zestaw znaków** do **Użyj kodowania Unicode**. To ustawienie ma wpływ, które makro jest wstępnie zdefiniowane podczas kompilacji. Istnieje zarówno makro UNICODE i _unicode — makro. Właściwość projektu dotyczy zarówno spójnie. Nagłówki Windows używaj UNICODE w przypadku, gdy _unicode — Użyj nagłówków Visual C++, takie jak MFC, ale gdy jest ono zdefiniowane, drugi zawsze jest definiowany.  
  
 Jest dobrą [przewodnik](http://msdn.microsoft.com/library/cc194801.aspx) eksportowaniu z MBCS na Unicode UTF-16 przy użyciu tchar — istnieje. Wybrany tej trasy. Po pierwsze, zmieniamy **zestaw znaków** właściwości **zestaw znaków Unicode, użyj** i ponownie skompilować projekt.  
  
 Niektóre miejsca w kodzie zostały już używa `TCHAR`, prawdopodobnie w oczekiwaniu ostatecznie obsługi formatu Unicode. Niektóre nie były dostępne. Firma Microsoft wyszukiwane wystąpienia `CHAR`, który jest typem typedef char i zastąpionego większość z nich z tchar —. Ponadto analizujemy `sizeof (CHAR)`. Gdy firma Microsoft zmieniła się z `CHAR` do `TCHAR`, zwykle było można zmienić na `sizeof(TCHAR)` ponieważ było często używane w celu ustalenia liczby znaków w ciągu. W tym miejscu przy użyciu nieprawidłowego typu nie tworzy wystąpi błąd kompilatora, więc warto płatności nieco uwagi do tego przypadku.  
  
 Tego typu błędu jest często tylko po przełączeniu na Unicode.  
  
```Output  
error C2664: 'int wsprintfW(LPWSTR,LPCWSTR,...)': cannot convert argument 1 from 'CHAR [16]' to 'LPWSTR'  
```  
  
 Oto przykładowy kod, który spowoduje utworzenie to:  
  
```cpp  
wsprintf(szTmp, "%d.%2.2d.%4.4d", rmj, rmm, rup);  
```  
  
 _T — wokół ciąg testujemy literału, aby usunąć błąd.  
  
```cpp  
wsprintf(szTmp, _T("%d.%2.2d.%4.4d"), rmj, rmm, rup);  
```  
  
 _T — makro ma sprawia kompilacji literału ciągu, jako `char` ciąg lub `wchar_t` ciągu, w zależności od ustawienia MBCS lub UNICODE. Aby zastąpić wszystkie ciągi _t — w programie Visual Studio, należy najpierw otworzyć **szybkiego zastąpienia** (klawiatury: Ctrl + F) pole lub **zamienianie w plikach** (klawiatury: Ctrl + Shift + H), a następnie wybierz **Użyj regularnych Wyrażenia** wyboru. Wprowadź `((\".*?\")|('.+?'))` jako szukany tekst i `_T($1)` jako tekst zastępczy. Jeśli masz już _t — makro wokół niektórych ciągów, w tej procedurze zostanie dodane ponownie i może także przypadki, w których nie chcesz _t — na przykład przy użyciu `#include`, dlatego najlepiej użyć **Zastąp dalej** zamiast  **Zamień wszystkie**.  
  
 Tej określonej funkcji [wsprintf](https://msdn.microsoft.com/library/windows/desktop/ms647550.aspx), faktycznie jest zdefiniowany w nagłówków systemu Windows i dokumentację dla sugeruje, że ona nie być używane, z powodu przepełnienia buforu możliwe. Rozmiar nie jest określony dla `szTmp` buforu, dlatego nie ma możliwości dla tej funkcji sprawdzić, czy bufor może przechowywać wszystkie dane do zapisania go. Zobacz następną sekcję o eksportowaniu na CRT bezpieczny, w którym firma Microsoft rozwiązać inne problemy podobne. Firma Microsoft ostatecznie otrzymano zamienienie go z [_stprintf_s —](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md).  
  
 Inny błąd wspólnego zobaczysz konwersji na format Unicode jest to.  
  
```Output  
error C2440: '=': cannot convert from 'char *' to 'TCHAR *'  
```  
  
 Kod, który tworzy go następująco:  
  
```cpp  
pParentNode->m_szText = new char[strTitle.GetLength() + 1];  
_tcscpy(pParentNode->m_szText, strTitle);  
  
```  
  
 Mimo że _tcscpy — funkcja została użyta, ponieważ jest to funkcja strcpy tchar — kopiowania ciąg, buforu, który został przydzielony został `char` buforu. Jest to łatwo zmienić na tchar —.  
  
```cpp  
pParentNode->m_szText = new TCHAR[strTitle.GetLength() + 1];  
_tcscpy(pParentNode->m_szText, strTitle);  
  
```  
  
 Podobnie, możemy zmienić `LPSTR` (wskaźnik długi ciąg) i `LPCSTR` (długa wskaźnik ze stałym ciągiem) do `LPTSTR` (wskaźnik długi ciąg tchar —) i `LPCTSTR` (długa wskaźnik ze stałym ciągiem tchar —) odpowiednio w błąd kompilatora. Wybraliśmy nie dokonywać takiego zastąpienia za pomocą wyszukiwania globalnego i Zamień, ponieważ każdej sytuacji musiały rozpatrywane pojedynczo. W niektórych przypadkach `char` wyznaczony wersji, np. podczas przetwarzania niektórych Windows komunikaty używających struktury systemu Windows, które mają sufiks A. W interfejsie API systemu Windows A sufiksem oznacza ASCII lub ANSI (i mają zastosowanie również do MBCS), a sufiks W oznacza znaki dwubajtowe lub Unicode UTF-16. Ten wzorzec nazewnictwa jest używane w nagłówkach systemu Windows, ale także była ona w kodzie Spy ++ podczas było dodać wersję Unicode, funkcji, która została już zdefiniowana w wersji MBCS.  
  
 W niektórych przypadkach było zamienić typu do korzystania z wersji, która rozpoznaje poprawnie (WNDCLASS zamiast WNDCLASSA, na przykład).  
  
 W wielu przypadkach było używana wersja ogólny interfejs API Win32, takich jak GetClassName (zamiast GetClassNameA) (makro). W instrukcji switch obsługi wiadomości, niektóre komunikaty są właściwe MBCS lub Unicode, w tych przypadkach, było zmienić kod, aby jawnie wywołać MBCS wersji, ponieważ firma Microsoft objęty nazwanego funkcje za pomocą A oraz W określonych funkcji i dodać makro nazwy ogólnej, który jest rozpoznawany jako poprawne A lub nazwa W oparciu czy UNICODE jest zdefiniowane.  W wielu części kodu gdy wprowadziliśmy do definiowania _unicode —, W wersji teraz wybierany jest nawet jeśli wersja A jest wyznaczony co.  
  
 Istnieje kilka miejsc, gdy miały specjalne akcje do wykonania. Stosowania Procedura WideCharToMultiByte lub MultiByteToWideChar może wymagać bliższe spojrzenie. Oto przykład jeżeli Procedura WideCharToMultiByte jest używany.  
  
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
  
 Aby rozwiązać ten problem, było zrozumienie, że przyczyny, dla której zostało to było do skopiowania ciąg znaków typu wide reprezentujący nazwę czcionki do wewnętrznego buforu cstring —, strFace. Nieco inny kod to wymagane dla wielobajtowe ciągów cstring — podobnie jak w przypadku znaków typu wide cstring — ciągi, więc w takim przypadku dodaliśmy #ifdef.  
  
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
  
 Oczywiście zamiast wcscpy — naprawdę powinien używamy wcscpy_s —, wersja bardziej bezpieczne. Następna sekcja rozwiązuje ten problem.  
  
 W celu sprawdzenia naszej pracy możemy zresetować zestawu znaków do zestawu znaków wielobajtowych użycia i upewnij się, że kod kompiluje nadal przy użyciu MBCS, jak również Unicode. Needless, że przebiegu testowego pełną powinien być wykonywany na ponownej kompilacji aplikacji po tych zmian.  
  
 W naszym korzystają z tego rozwiązania Spy ++ zajęło około dwóch dni roboczych dla programisty C++ średni przekonwertować kod Unicode. Który nie zawiera retesting czasu.  
  
##  <a name="porting_to_secure_crt"></a>Krok 12. Eksportowanie do użycia bezpiecznego CRT  
 Eksportowanie kodu w celu użycia wersji bezpiecznego (wersje wraz z sufiksem _s) funkcje CRT jest dalej. W takim przypadku ogólne strategii ma zastąpić funkcję wersji _s, a następnie, zwykle, Dodaj parametry rozmiar wymagany dodatkowy bufor. W wielu przypadkach jest to prosta ponieważ rozmiar jest znany. W innych przypadkach, gdy rozmiar nie jest dostępna natychmiast, konieczne jest dodanie dodatkowych parametrów do funkcji, która używa funkcji CRT ani prawdopodobnie zużycie bufor docelowy i zobacz jakie odpowiedniego rozmiaru są limity.  
  
 Visual C++ zapewnia lewy, aby ułatwić otrzymać kod bezpiecznego bez dodawania jako wiele parametrów rozmiar i to przy użyciu szablonu przeciążenia. Ponieważ przeciążenia te szablony, ich są dostępne tylko podczas kompilowania jako C++, nie jako C. Spyxxhk jest to projekt C, dlatego lewy nie będą działać w tym.  Jednak nie jest Spyxx i możemy użyć lewy. Lewy jest dodany wiersz podobny do tego w miejscu, gdzie ona zostanie skompilowany w każdym pliku projektu, takie jak w pliku stdafx.h:  
  
```cpp  
#define _CRT_SECURE_TEMPLATE_OVERLOADS 1  
```  
  
 Po zdefiniowaniu, gdy bufor jest tablicą, zamiast wskaźnik raw, jego rozmiar jest wywnioskowany na podstawie typu tablicy i który jest używany jako parametr rozmiaru bez konieczności dostarczenia go. Który pozwala zmniejszyć złożoność poprawiania kodu. Nadal trzeba zastąpić wersją _s nazwę funkcji, ale często może odbywać się za pomocą wyszukiwania i Zakończono operację zamiany.  
  
 Wartości zwrócone przez niektóre funkcje zmienić. Na przykład _itoa_s — (i _itow_s — i _itot_s — makro) zwraca kod błędu (errno_t), zamiast ciągu. W takich przypadkach należy więc Przenieś wywołanie _itoa_s — na osobnym wierszu i zastąp go identyfikator buforu.  
  
 Niektóre typowe przypadki: dla funkcji memcpy, podczas przełączania do memcpy_s —, często dodaliśmy rozmiar kopiowane do struktury. Podobnie dla większości ciągów i buforów rozmiaru tablicy lub buforu łatwo zależy od deklaracji buforu lub znajdowania, gdzie pierwotnie został przydzielony rozmiar buforu. W niektórych sytuacjach należy ustalić, jak duży buforu jest aktualnie dostępna oraz że informacje nie są dostępne w zakresie funkcji, która jest modyfikacja, powinny zostać dodane jako dodatkowy parametr oraz kod wywołujący powinien zostać zmodyfikowane w celu Podaj informacje.  
  
 Te techniki zajęło około połowy przekonwertować kod, aby użyć funkcji CRT bezpieczne. Jeśli wybierzesz nie przeciążeń szablonu i ręcznie Dodaj parametry rozmiar, prawdopodobnie zajmie się dwukrotnie lub trzy razy więcej czasu.  
  
##  <a name="deprecated_forscope"></a>Krok 13. /Zc:forScope-jest przestarzały.  
 Od czasu Visual C++ 6.0 kompilator jest zgodna z bieżącym standard, co ogranicza zakres zmiennych zadeklarowanych w pętli do zakresu pętli. Opcja kompilatora [/Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) (**Wymuszaj zgodność w zakresie pętli for** we właściwościach projektu) określa, czy jest to raportowane jako błąd. Firma Microsoft należy zaktualizować naszego kodu zgodność, a następnie dodaj deklaracje tylko poza pętli. Aby uniknąć zmian w kodzie, można zmienić tego ustawienia w sekcji języka C++ właściwości projektu, aby **(/Zc:forScope-)**. Jednak należy pamiętać, że **/Zc:forScope-** mogą zostać usunięte w przyszłej wersji programu Visual C++, więc po pewnym czasie kodu należy zmienić zgodności ze standardem.  
  
 Są stosunkowo łatwa do rozwiązać te problemy, ale w zależności od kodu, to może wpłynąć na dużej ilości kodu. Oto typowy problem.  
  
```cpp  
int CPerfTextDataBase::NumStrings(LPCTSTR mszStrings) const  
{  
  for (int n = 0; mszStrings[0] != 0; n++)  
  mszStrings = _tcschr(mszStrings, 0) + 1;  
  return(n);  
}  
  
```  
  
 Powyższy kod tworzy kod błędu:  
  
```Output  
'n': undeclared identifier  
```  
  
 Dzieje się tak, ponieważ kompilatora jest przestarzałe opcję kompilatora, która może kod, który nie spełnia już C++ standard. Standard deklarowanie zmiennej wewnątrz pętli ogranicza zakres do pętli, więc popularną praktyką użycia licznika pętli poza pętlą wymagają, że deklaracja licznika również zostać przeniesiona poza pętli, jak w poniższym kodzie poprawione :  
  
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
 Eksportowanie Spy ++ z oryginalnego kodu Visual C++ 6.0 do najnowszej kompilatora zajęło około 20 godzin kodowania czasu w trakcie o tydzień. Możemy uaktualnić bezpośrednio do ośmiu wersje produktu programu Visual Studio 6.0 do programu Visual Studio 2015. Teraz jest zalecane podejście do uaktualnienia wszystkich projektów, duże i małe.  
  
## <a name="see-also"></a>Zobacz też  
 [Przenoszenie i uaktualnianie: przykłady i analizy przypadków:](../porting/porting-and-upgrading-examples-and-case-studies.md)   
 [Analiza przypadku poprzednich: narzędzie Spy modelu COM](../porting/porting-guide-com-spy.md)