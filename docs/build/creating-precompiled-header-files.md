---
title: Pliki prekompilowanego nagłówka
ms.date: 10/24/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 158301ec3caacced1663892071b17ef2b8f8e741
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328670"
---
# <a name="precompiled-header-files"></a>Pliki prekompilowanego nagłówka

Podczas tworzenia nowego projektu w programie Visual Studio, *wstępnie skompilowany plik nagłówka* o nazwie *pch.h* jest dodawany do projektu. (W programie Visual Studio 2017 i wcześniejszych plik został nazwany *stdafx.h*.) Celem pliku jest przyspieszenie procesu kompilacji. W tym miejscu powinny znajdować się wszystkie `<vector>`stabilne pliki nagłówkowe, na przykład nagłówki biblioteki standardowej, takie jak , . Wstępnie skompilowany nagłówek jest kompilowany tylko wtedy, gdy lub wszystkie pliki, które zawiera, są modyfikowane. Jeśli tylko zmiany w kodzie źródłowym projektu, kompilacja pominie kompilacji dla wstępnie skompilowanego nagłówka.

Opcje kompilatora wstępnie skompilowanych nagłówków to [/Y](reference/y-precompiled-headers.md). Na stronach właściwości projektu opcje znajdują się w obszarze **Właściwości konfiguracji > C/C++ > Wstępnie skompilowane nagłówki**. Można wybrać opcję niekorzysconych nagłówków wstępnie skompilowanych i określić nazwę pliku nagłówka oraz nazwę i ścieżkę pliku wyjściowego.

## <a name="custom-precompiled-code"></a>Niestandardowy kod wstępnie skompilowany

W przypadku dużych projektów, które zajmują dużo czasu na tworzenie, warto rozważyć utworzenie niestandardowych wstępnie skompilowanych plików. Kompilatory Microsoft C i C++ udostępniają opcje wstępnego kompilowania dowolnego kodu C lub C++, w tym kodu wbudowanego. Za pomocą tej funkcji wydajności, można skompilować stabilną treść kodu, przechowywać skompilowany stan kodu w pliku i, podczas kolejnych kompilacji, połączyć wstępnie skompilowany kod z kodem, który jest nadal w fazie rozwoju. Każda kolejna kompilacja jest szybsza, ponieważ stabilny kod nie musi być ponownie skompilowany.

## <a name="when-to-precompile-source-code"></a>Kiedy przeprowadzać prekompilowanie kodu źródłowego

Wstępnie skompilowany kod jest przydatny podczas cyklu rozwoju, aby skrócić czas kompilacji, zwłaszcza jeśli:

- Zawsze używasz dużej treści kodu, który zmienia się rzadko.

- Program składa się z wielu modułów, z których wszystkie używają standardowego zestawu plików dołączanych i tych samych opcji kompilacji. W takim przypadku wszystkie pliki dołączane można wstępnie skompilować w jednym wstępnie skompilowanym nagłówku.

Pierwsza kompilacja — ta, która tworzy plik wstępnie skompilowanego nagłówka (PCH) — trwa nieco dłużej niż kolejne kompilacje. Kolejne kompilacje można kontynuować szybciej, dołączając wstępnie skompilowany kod.

Można wstępnie skompilować programy C i C++. W programowaniu języka C++ jest powszechną praktyką, aby oddzielić informacje o interfejsie klasy do plików nagłówkowych. Te pliki nagłówkowe mogą być później zawarte w programach, które używają klasy. Wstępnie kompilowanie tych nagłówków można skrócić czas kompilacji programu.

> [!NOTE]
> Chociaż można używać tylko jednego wstępnie skompilowanego pliku nagłówka (pch) na plik źródłowy, można użyć wielu plików pch w projekcie.

## <a name="two-choices-for-precompiling-code"></a>Dwa wybory dla wstępnej kompilacji kodu

Można wstępnie skompilować dowolny kod C lub C++; nie są ograniczone do wstępnego komppilowania tylko plików nagłówkowych.

Wstępne kompilowanie wymaga planowania, ale oferuje znacznie szybsze kompilacje, jeśli wstępnie skompilowany kod źródłowy inny niż proste pliki nagłówka.

Wstępnie skompilować kod, gdy wiadomo, że pliki źródłowe używają typowych zestawów plików nagłówkowych, ale nie zawierają ich w tej samej kolejności lub gdy chcesz dołączyć kod źródłowy do wstępnej kompilacji.

Wstępnie skompilowane opcje nagłówka to [/Yc (Tworzenie wstępnie skompilowanego pliku nagłówka)](reference/yc-create-precompiled-header-file.md) i [/Yu (Użyj wstępnie skompilowanego pliku nagłówka).](reference/yu-use-precompiled-header-file.md) Użyj **/Yc,** aby utworzyć wstępnie skompilowany nagłówek. W przypadku użycia z opcjonalnym [pragma hdrstop,](../preprocessor/hdrstop.md) **/Yc** umożliwia wstępnie skompilować zarówno pliki nagłówkowe, jak i kod źródłowy. Wybierz **/Yu,** aby użyć istniejącego wstępnie skompilowanego nagłówka w istniejącej kompilacji. Można również użyć **/Fp** z **/Yc** i **/Yu** opcji, aby podać alternatywną nazwę dla wstępnie skompilowany nagłówek.

Tematy referencyjne opcji kompilatora dla **/Yu** i **/Yc** omówienia sposobu dostępu do tej funkcji w środowisku programistycznym.

## <a name="precompiled-header-consistency-rules"></a>Zasady spójności prekompilowanego nagłówka

Ponieważ pliki PCH zawierają informacje o środowisku komputera, a także informacje o adresie pamięci programu, należy używać tylko pliku PCH na komputerze, na którym został utworzony.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Zasady spójności dla stosowanych dla prekompilowanych plików nagłówka

Opcja kompilatora [/Yu](reference/yu-use-precompiled-header-file.md) pozwala określić, który plik PCH ma być używany.

Podczas korzystania z pliku PCH kompilator przyjmuje to samo środowisko kompilacji — takie, które używa spójnych opcji kompilatora, pragmas i tak dalej — który obowiązywał podczas tworzenia pliku PCH, chyba że określono inaczej. Jeśli kompilator wykryje niespójność, generuje ostrzeżenie i identyfikuje niespójność, gdzie to możliwe. Takie ostrzeżenia nie muszą oznaczać problemu z plikiem PCH; po prostu ostrzegają przed możliwymi konfliktami. Wymagania dotyczące spójności plików PCH są opisane w poniższych sekcjach.

### <a name="compiler-option-consistency"></a>Spójność opcji kompilatora

Następujące opcje kompilatora mogą wyzwolić ostrzeżenie o niespójności podczas korzystania z pliku PCH:

- Makra utworzone przy użyciu opcji Preprocesor (/D) muszą być takie same między kompilacją, która utworzyła plik PCH, a bieżącą kompilacją. Stan zdefiniowanych stałych nie jest sprawdzany, ale mogą wystąpić nieprzewidywalne wyniki, jeśli te zmiany.

- Pliki PCH nie działają z opcjami /E i /EP.

- Pliki PCH muszą być tworzone przy użyciu opcji Generuj informacje o przeglądaniu (/FR) lub Opcji Wyklucz zmienne lokalne (/Fr), zanim kolejne kompilacje korzystające z pliku PCH będą mogły korzystać z tych opcji.

### <a name="c-70-compatible-z7"></a>Kompatybilny z C 7.0 (/Z7)

Jeśli ta opcja obowiązuje podczas tworzenia pliku PCH, kolejne kompilacje korzystające z pliku PCH mogą używać informacji debugowania.

Jeśli opcja C 7.0-Compatible (/Z7) nie obowiązuje podczas tworzenia pliku PCH, kolejne kompilacje korzystające z pliku PCH i /Z7 wyzwalają ostrzeżenie. Informacje debugowania są umieszczane w bieżącym pliku obj, a symbole lokalne zdefiniowane w pliku PCH nie są dostępne dla debugera.

### <a name="include-path-consistency"></a>Uwzględnij spójność ścieżki

Plik PCH nie zawiera informacji o ścieżce dołączania, która obowiązywała podczas jej tworzenia. Podczas korzystania z pliku PCH kompilator zawsze używa ścieżki dołączania określonej w bieżącej kompilacji.

### <a name="source-file-consistency"></a>Spójność pliku źródłowego

Po określeniu opcji Użyj wstępnie skompilowanego pliku nagłówka (/Yu), kompilator ignoruje wszystkie dyrektywy preprocesora (w tym pragmy), które pojawiają się w kodzie źródłowym, który będzie wstępnie skompilowany. Kompilacja określona przez takie dyrektywy preprocesora musi być taka sama jak kompilacja używana dla opcji Utwórz wstępnie skompilowany plik nagłówka (/Yc).

### <a name="pragma-consistency"></a>Spójność Pragma

Pragmas przetwarzane podczas tworzenia pliku PCH zwykle wpływają na plik, z którym plik PCH jest następnie używany. I `comment` `message` pragmy nie wpływają na pozostałą część kompilacji.

Te pragmy wpływają tylko na kod w pliku PCH; nie mają one wpływu na kod, który następnie używa pliku PCH:

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

Te pragmy są zachowywane jako część wstępnie skompilowanego nagłówka i wpływają na pozostałą część kompilacji, która używa wstępnie skompilowanego nagłówka:

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>Zasady spójności dla /Yc i /Yu

Korzystając z wstępnie skompilowanego nagłówka utworzonego przy użyciu /Yc lub /Yu, kompilator porównuje bieżące środowisko kompilacji z tym, które istniało podczas tworzenia pliku PCH. Pamiętaj, aby określić środowisko zgodne z poprzednim (przy użyciu spójnych opcji kompilatora, pragmas i tak dalej) dla bieżącej kompilacji. Jeśli kompilator wykryje niespójność, generuje ostrzeżenie i identyfikuje niespójność, gdzie to możliwe. Takie ostrzeżenia nie muszą oznaczać problemu z plikiem PCH; po prostu ostrzegają przed możliwymi konfliktami. W poniższych sekcjach wyjaśniono wymagania dotyczące spójności dla wstępnie skompilowanych nagłówków.

### <a name="compiler-option-consistency"></a>Spójność opcji kompilatora

W tej tabeli wymieniono opcje kompilatora, które mogą wyzwolić ostrzeżenie o niespójności podczas korzystania z wstępnie skompilowanego nagłówka:

|Opcja|Nazwa|Reguła|
|------------|----------|----------|
|/D|Definiowanie stałych i makr|Musi być taka sama między kompilacji, która utworzyła wstępnie skompilowany nagłówek i bieżącej kompilacji. Stan zdefiniowanych stałych nie jest sprawdzany, ale nieprzewidywalne wyniki mogą wystąpić, jeśli pliki zależą od wartości zmienionych stałych.|
|/E lub /EP|Kopiowanie wyjścia preprocesora na wyjście standardowe|Wstępnie skompilowane nagłówki nie działają z opcją /E lub /EP.|
|/Fr lub /FR|Generowanie informacji o przeglądarce źródłowego firmy Microsoft|Aby opcje /Fr i /FR były prawidłowe z opcją /Yu, muszą one również obowiązywać podczas tworzenia wstępnie skompilowanego nagłówka. Kolejne kompilacje, które używają wstępnie skompilowanego nagłówka, również generują informacje o przeglądarce źródłowej. Informacje o przeglądarce są umieszczane w jednym pliku .sbr i są odwoływane przez inne pliki w taki sam sposób, jak informacje CodeView. Nie można zastąpić umieszczania informacji o przeglądarce źródłowej.|
|/GA, /GD, /GE, /Gw lub /GW|Opcje protokołu systemu Windows|Musi być taka sama między kompilacji, która utworzyła wstępnie skompilowany nagłówek i bieżącej kompilacji. Jeśli te opcje różnią się, zostanie wyświetlony komunikat ostrzegawczy.|
|/zi|Generowanie pełnych informacji debugowania|Jeśli ta opcja obowiązuje podczas tworzenia wstępnie skompilowanego nagłówka, kolejne kompilacje korzystające z wstępnej kompilacji mogą używać tych informacji debugowania. Jeśli /Zi nie obowiązuje podczas tworzenia wstępnie skompilowanego nagłówka, kolejne kompilacje, które używają wstępnej kompilacji i opcji /Zi, wyzwalają ostrzeżenie. Informacje debugowania są umieszczane w bieżącym pliku obiektu, a symbole lokalne zdefiniowane w wstępnie skompilowanym nagłówku nie są dostępne dla debugera.|

> [!NOTE]
> Wstępnie skompilowany przycisk nagłówka jest przeznaczony do użytku tylko w plikach źródłowych języka C i C++.

## <a name="using-precompiled-headers-in-a-project"></a>Stosowanie w projekcie prekompilowanych nagłówków

Poprzednie sekcje przedstawiają przegląd wstępnie skompilowanych nagłówków: /Yc i /Yu, /Fp i [hdrstop](../preprocessor/hdrstop.md) pragma. W tej sekcji opisano metodę korzystania z ręcznych opcji wstępnie skompilowanego nagłówka w projekcie; kończy się przykładem makefile i kodem, który zarządza.

Aby uzyskać inne podejście do korzystania z ręcznych opcji wstępnie skompilowanego nagłówka w projekcie, przestudiuj jeden z plików makefiles znajdujących się w katalogu MFC\SRC, który jest tworzony podczas domyślnej konfiguracji programu Visual Studio. Te makefiles podjąć podobne podejście do przedstawionego w tej sekcji, ale w większym stopniu korzystać z microsoft program konserwacji narzędzia (NMAKE) makra i oferują większą kontrolę nad procesem kompilacji.

## <a name="pch-files-in-the-build-process"></a>Pliki PCH w procesie kompilacji

Baza kodu projektu oprogramowania jest zwykle zawarta w wielu plikach źródłowych języka C lub C++, plikach obiektów, bibliotekach i plikach nagłówkowych. Zazwyczaj plik makefile koordynuje kombinację tych elementów w pliku wykonywalnym. Na poniższej ilustracji przedstawiono strukturę pliku makefile, który używa wstępnie skompilowanego pliku nagłówka. Nazwy makr NMAKE i nazwy plików na tym diagramie są zgodne z nazwami w przykładowym kodzie znalezionym w [przykładowym pliku Makefile dla PCH](#sample-makefile-for-pch) i [przykładowym kodzie dla PCH](#example-code-for-pch).

Rysunek używa trzech urządzeń diagramowych, aby pokazać przepływ procesu kompilacji. Nazwane prostokąty reprezentują każdy plik lub makro; trzy makra reprezentują jeden lub więcej plików. Cieniowane obszary reprezentują każdą akcję kompilacji lub łącza. Strzałki pokazują, które pliki i makra są łączone podczas procesu kompilacji lub łączenia.

![Struktura pliku makefile, który używa wstępnie skompilowanego pliku nagłówka](media/vc30ow1.gif "Struktura pliku makefile, który używa wstępnie skompilowanego pliku nagłówka") <br/>
Struktura pliku Makefile, który używa wstępnie skompilowanego pliku nagłówka

Począwszy od góry diagramu, zarówno STABLEHDRS i BOUNDRY są NMAKE makr, w których lista plików nie może wymagać ponownej kompilacji. Pliki te są kompilowane przez ciąg poleceń

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

tylko wtedy, gdy wstępnie skompilowany plik nagłówka (STABLE.pch) nie istnieje lub jeśli wprowadzone zostaną zmiany w plikach wymienionych w dwóch makrach. W obu przypadkach wstępnie skompilowany plik nagłówka będzie zawierał kod tylko z plików wymienionych w makrze STABLEHDRS. Wyświetl ostatni plik, który ma być wstępnie skompilowany w makrze BOUNDRY.

Pliki wywieszane w tych makrach mogą być plikami nagłówkowymi lub plikami źródłowymi języka C lub C++. (Pojedynczego pliku PCH nie można używać zarówno z modułami C, jak i C++). Należy zauważyć, że można użyć makra **hdrstop,** aby zatrzymać wstępną kompilację w pewnym momencie w pliku BOUNDRY. Zobacz [hdrstop aby](../preprocessor/hdrstop.md) uzyskać więcej informacji.

Kontynuując w dół diagramu APPLIB.obj reprezentuje kod pomocy technicznej używany w aplikacji końcowej. Jest on tworzony z APPLIB.cpp, pliki wymienione w makra UNSTABLEHDRS i wstępnie skompilowany kod z wstępnie skompilowanego nagłówka.

MYAPP.obj reprezentuje ostateczną aplikację. Jest on tworzony z MYAPP.cpp, pliki wymienione w makra UNSTABLEHDRS i wstępnie skompilowany kod z wstępnie skompilowanego nagłówka.

Na koniec plik wykonywalny (MYAPP. EXE) jest tworzony przez połączenie plików wymienionych w makra OBJS (APPLIB.obj i MYAPP.obj).

## <a name="sample-makefile-for-pch"></a>Przykładowy plik pliku reguł programu Make dla PCH

Następujący plik makefile używa makr i ! Jeśli! Innego! ENDIF flow-of-control struktury poleceń, aby uprościć jego adaptacji do projektu.

```NMAKE
# Makefile : Illustrates the effective use of precompiled
#            headers in a project
# Usage:     NMAKE option
# option:    DEBUG=[0|1]
#            (DEBUG not defined is equivalent to DEBUG=0)
#
OBJS = myapp.obj applib.obj
# List all stable header files in the STABLEHDRS macro.
STABLEHDRS = stable.h another.h
# List the final header file to be precompiled here:
BOUNDRY = stable.h
# List header files under development here:
UNSTABLEHDRS = unstable.h
# List all compiler options common to both debug and final
# versions of your code here:
CLFLAGS = /c /W3
# List all linker options common to both debug and final
# versions of your code here:
LINKFLAGS = /nologo
!IF "$(DEBUG)" == "1"
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi
LINKFLAGS = $(LINKFLAGS) /COD
LIBS      = slibce
!ELSE
CLFLAGS   = $(CLFLAGS) /Oselg /Gs
LINKFLAGS = $(LINKFLAGS)
LIBS      = slibce
!ENDIF
myapp.exe: $(OBJS)
    link $(LINKFLAGS) @<<
$(OBJS), myapp, NUL, $(LIBS), NUL;
<<
# Compile myapp
myapp.obj  : myapp.cpp $(UNSTABLEHDRS)  stable.pch
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    myapp.cpp
# Compile applib
applib.obj : applib.cpp $(UNSTABLEHDRS) stable.pch
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    applib.cpp
# Compile headers
stable.pch : $(STABLEHDRS)
    $(CPP) $(CLFLAGS) /Yc$(BOUNDRY)    applib.cpp myapp.cpp
```

Oprócz makr STABLEHDRS, BOUNDRY i UNSTABLEHDRS pokazanych na rysunku "Struktura pliku Makefile, który używa wstępnie skompilowanego pliku nagłówka" w [plikach PCH w procesie kompilacji,](#pch-files-in-the-build-process)plik ten zapewnia makro CLFLAGS i makro LINKFLAGS. Te makra należy używać do listy opcji kompilatora i konsolidatora, które mają zastosowanie, niezależnie od tego, czy tworzysz debugowanie, czy ostateczną wersję pliku wykonywalnego aplikacji. Istnieje również makro LIBS, w którym można wyświetlić listę bibliotek, których wymaga projekt.

Makefile również używa! Jeśli! Innego! ENDIF do wykrywania, czy symbol DEBUG w wierszu polecenia NMAKE:

```NMAKE
NMAKE DEBUG=[1|0]
```

Ta funkcja umożliwia używanie tego samego pliku makefile podczas tworzenia i dla ostatecznych wersji programu — użyj DEBUG=0 dla ostatecznych wersji. Następujące wiersze polecenia są równoważne:

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Aby uzyskać więcej informacji na temat plików makefiles, zobacz [NMAKE Reference](reference/nmake-reference.md). Zobacz też [Opcje kompilatora MSVC](reference/compiler-options.md) i [Opcje konsolidatora MSVC](reference/linker-options.md).

## <a name="example-code-for-pch"></a>Przykład kodu dla PCH

Następujące pliki źródłowe są używane w pliku plików plików opisanych w [pliku PCH w procesie kompilacji](#pch-files-in-the-build-process) i [przykładowym pliku makefile dla PCH](#sample-makefile-for-pch). Należy pamiętać, że komentarze zawierają ważne informacje.

```cpp
// ANOTHER.H : Contains the interface to code that is not
//             likely to change.
//
#ifndef __ANOTHER_H
#define __ANOTHER_H
#include<iostream>
void savemoretime( void );
#endif // __ANOTHER_H
```

```cpp
// STABLE.H : Contains the interface to code that is not likely
//            to change. List code that is likely to change
//            in the makefile's STABLEHDRS macro.
//
#ifndef __STABLE_H
#define __STABLE_H
#include<iostream>
void savetime( void );
#endif // __STABLE_H
```

```cpp
// UNSTABLE.H : Contains the interface to code that is
//              likely to change. As the code in a header
//              file becomes stable, remove the header file
//              from the makefile's UNSTABLEHDR macro and list
//              it in the STABLEHDRS macro.
//
#ifndef __UNSTABLE_H
#define __UNSTABLE_H
#include<iostream>
void notstable( void );
#endif // __UNSTABLE_H
```

```cpp
// APPLIB.CPP : This file contains the code that implements
//              the interface code declared in the header
//              files STABLE.H, ANOTHER.H, and UNSTABLE.H.
//
#include"another.h"
#include"stable.h"
#include"unstable.h"
using namespace std;
// The following code represents code that is deemed stable and
// not likely to change. The associated interface code is
// precompiled. In this example, the header files STABLE.H and
// ANOTHER.H are precompiled.
void savetime( void )
    { cout << "Why recompile stable code?\n"; }
void savemoretime( void )
    { cout << "Why, indeed?\n\n"; }
// The following code represents code that is still under
// development. The associated header file is not precompiled.
void notstable( void )
    { cout << "Unstable code requires"
            << " frequent recompilation.\n";
    }
```

```cpp
// MYAPP.CPP : Sample application
//             All precompiled code other than the file listed
//             in the makefile's BOUNDRY macro (stable.h in
//             this example) must be included before the file
//             listed in the BOUNDRY macro. Unstable code must
//             be included after the precompiled code.
//
#include"another.h"
#include"stable.h"
#include"unstable.h"
int main( void )
{
    savetime();
    savemoretime();
    notstable();
}
```

## <a name="see-also"></a>Zobacz też

[Odwołanie kompilacji C/C++](reference/c-cpp-building-reference.md)<br/>
[Opcje kompilatora MSVC](reference/compiler-options.md)
