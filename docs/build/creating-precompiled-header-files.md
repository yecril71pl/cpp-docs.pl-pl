---
title: Pliki prekompilowanego nagłówka
ms.date: 12/10/2018
f1_keywords:
- pch
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 5afda50c43f93baa2d73e6afb68f436560c3243e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823246"
---
# <a name="precompiled-header-files"></a>Pliki prekompilowanego nagłówka

Podczas tworzenia nowego projektu w programie Visual Studio, *prekompilowanego pliku nagłówkowego* o nazwie "pch.h" zostanie dodany do projektu. (We wcześniejszych wersjach programu Visual Studio, plik został nazywane "stdafx.h"). Plik ma na celu przyspieszenia procesu kompilacji. Wszelkie stabilne pliki nagłówkowe, na przykład nagłówki standardowej biblioteki takich jak `<vector>`, mają zostać uwzględnione w tym miejscu. Prekompilowany plik nagłówkowy jest kompilowana, tylko wtedy, gdy lub wszystkie pliki, które zawiera, są modyfikowane. Jeśli wprowadzisz zmiany tylko w kodzie źródłowym projektu, kompilacja zostanie pominięta kompilowania dla prekompilowanego nagłówka. 

Opcje kompilatora wstępnie skompilowanych nagłówków są [/Y](reference/y-precompiled-headers.md). Na stronach właściwości projektu, opcje znajdują się w obszarze **właściwości konfiguracji > C/C++ > prekompilowanych nagłówków**. Można wybrać opcję nie używał wstępnie skompilowanych nagłówków, ale można określić nagłówek pliku nazwę oraz nazwę i ścieżkę plików wyjściowych. 

## <a name="custom-precompiled-code"></a>Niestandardowe wstępnie skompilowany kod

Dla dużych projektów, które zająć dużo czasu na tworzenie warto rozważyć utworzenie niestandardowych wstępnie skompilowanych plików. Kompilatory Microsoft C i C++ zapewnia opcje dla wstępnej kompilacji kodu C lub C++, łącznie z kodem wbudowanego. Dzięki tej funkcji wydajności można skompilować stabilne treść kodu, zapisanie skompilowanej kodu w pliku i, podczas kolejnych kompilacjach łączyć wstępnie skompilowany kod z kodem, który jest nadal w fazie projektowania. Każda kolejne kompilacja jest szybsza, ponieważ stabilnym kodem nie musi być ponownie kompilowane.

## <a name="when-to-precompile-source-code"></a>Kiedy przeprowadzać prekompilowanie kodu źródłowego

Wstępnie skompilowany kod jest przydatne podczas cyklu rozwoju, aby skrócić czas kompilacji, zwłaszcza wtedy, gdy:

- Zawsze używaj dużej części kodu, który zmienia się rzadko.

- Program obejmuje wiele modułów, które używają standardowego zestawu dołączonych plików i tych samych opcji kompilacji. W takim przypadku wszystkie dołączane pliki być wstępnie skompilowany w jednym wstępnie skompilowanego nagłówka.

Pierwszy kompilacji — ten, który tworzy plik prekompilowanego nagłówka (PCH) — zajmuje to nieco dłużej niż kolejne kompilacje. Kolejne kompilacje można kontynuować szybciej, umieszczając wstępnie skompilowany kod.

Można prekompilowanie programów C i C++. W programowaniu C++ jest powszechną praktyką, aby oddzielić klasy interfejsu informacji w plikach nagłówkowych. Te pliki nagłówkowe objęte później programów, które używają tej klasy. Przez prekompilowanie tych nagłówków, można zmniejszyć czas program kompilacji.

> [!NOTE]
> Chociaż można używać tylko jednego pliku prekompilowanego pliku nagłówkowego (.pch) dla pliku źródłowego, można użyć wielu .pch — pliki w projekcie.

## <a name="two-choices-for-precompiling-code"></a>Dwa wybory dla wstępnej kompilacji kodu

Visual c++ można wstępnej kompilacji kodu języka C lub C++; nie są ograniczone do kompilacji wstępnej tylko pliki nagłówkowe.

Prekompilowanie wymaga planowania, ale oferuje znacznie szybsze kompilacje, jeśli prekompilowanie kodu źródłowego w innych niż pliki nagłówkowe proste.

Prekompilowanie kodu, gdy wiesz, użyć typowych zestawów plików nagłówkowych plików źródłowych, ale nie je uwzględnić w tej samej kolejności, lub gdy chcesz dołączyć kod źródłowy w swojej wstępnej kompilacji.

Dostępne są opcje prekompilowanego nagłówka [/Yc (Utwórz prekompilowany plik nagłówkowy)](reference/yc-create-precompiled-header-file.md) i [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](reference/yu-use-precompiled-header-file.md). Użyj **/Yc** do Utwórz prekompilowany nagłówek. Gdy jest używana z opcjonalnym [hdrstop](../preprocessor/hdrstop.md) pragma, **/Yc** umożliwia prekompilowanie oba pliki nagłówkowe i kod źródłowy. Wybierz **/Yu** do użycia istniejącego prekompilowanego pliku nagłówkowego w istniejącej kompilacji. Można również użyć **/FP** z **/Yc** i **/Yu** opcje zapewniają alternatywna nazwa podmiotu dla prekompilowanego nagłówka.

Tematy referencyjne — opcja kompilatora dla **/Yu** i **/Yc** omówiono, jak uzyskać dostęp do tej funkcji w środowisku programistycznym.

## <a name="precompiled-header-consistency-rules"></a>Zasady spójności prekompilowanego nagłówka

Ponieważ pliki PCH zawierają informacje o środowisku komputera, a także informacji na temat programu, informacje o adresie pamięci, należy używać tylko plik PCH na komputerze, w której został utworzony.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Zasady spójności dla stosowanych dla prekompilowanych plików nagłówka

[/Yu](reference/yu-use-precompiled-header-file.md) — opcja kompilatora pozwala określić plik PCH.

Korzystając z plików PCH, kompilator zakłada, w tym samym środowisku kompilacji — jedną, która używa opcji kompilatora spójne, pragm i tak dalej — było obowiązuje podczas tworzenia pliku PCH, chyba że określono inaczej. Jeśli kompilator wykryje niespójność, generuje ostrzeżenie i identyfikuje niespójności, jeśli jest to możliwe. Takie ostrzeżenia nie wskazują na problem z plików PCH; oni po prostu ostrzega o potencjalnych konfliktów. W poniższych sekcjach opisano wymagań spójności w przypadku plików PCH.

### <a name="compiler-option-consistency"></a>Spójność — opcja kompilatora

Następujące opcje kompilatora może wyzwalać ostrzeżenie niespójności, korzystając z plików PCH:

- Makra utworzone za pomocą preprocesora (/ D) opcja musi być taka sama, między kompilacji, która utworzyła plik PCH i bieżącej kompilacji. Stan zdefiniowanych stałych nie jest zaznaczone, ale nieprzewidywalne skutki może wystąpić, jeśli te zmiany.

- Pliki PCH nie działają z opcjami/e i /EP.

- Pliki PCH musi być utworzony przy użyciu albo wygenerować Przeglądaj informacje (/ FR) opcja lub wykluczania zmienne lokalne (/ Fr) opcja kolejne kompilacje, używające tego pliku PCH było korzystać z tych opcji.

### <a name="c-70-compatible-z7"></a>C 7.0 zgodne (/ Z7)

Jeśli ta opcja jest aktywna, po utworzeniu pliku PCH, kolejne kompilacje, używające tego pliku PCH użyć informacje debugowania.

Jeśli C 7.0 zgodne (/ Z7) opcja nie jest włączona podczas tworzenia pliku PCH, kolejne kompilacje, korzystających z plików PCH i/z7 wyzwolić ostrzeżenie. Informacje o debugowaniu znajduje się w bieżącym pliku .obj, a symbole lokalne zdefiniowane w pliku PCH nie są dostępne do debugera.

### <a name="include-path-consistency"></a>Obejmują spójności ścieżki

Plik PCH nie zawiera informacji na temat ścieżki dołączania, które obowiązywały podczas jej tworzenia. Korzystając z plików PCH, kompilator zawsze używa ścieżki dołączania, określone w bieżącej kompilacji.

### <a name="source-file-consistency"></a>Zgodności plików źródłowych

Po określeniu opcji korzystaj Prekompilowanego pliku nagłówka (/Yu), kompilator ignoruje wszystkie dyrektywy preprocesora jest (w tym pragm), które pojawiają się w kodzie źródłowym, który zostanie wstępnie skompilowany. Kompilacja, określony przez dyrektywy preprocesora, takie musi być taka sama jak kompilacji używany dla opcji tworzenia Prekompilowanego pliku nagłówkowego (/Yc).

### <a name="pragma-consistency"></a>Pragma spójności

Dyrektywy pragma przetwarzania podczas tworzenia pliku PCH zwykle wpływa na plik, z którymi plików PCH są następnie używane. `comment` i `message` pragm nie ma wpływu na pozostałą część kompilacji.

Te dyrektywy pragma wpływa na tylko kod wewnątrz pliku PCH; nie wpływają na kod, który następnie używa pliku PCH:

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

Te dyrektywy pragma są przechowywane jako część prekompilowanego nagłówka i wpływać na pozostałą część kompilacji, który używa prekompilowanego nagłówka:

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>Zasady spójności dla /Yc i /Yu

Używając prekompilowanego nagłówka, utworzony za pomocą /Yc i /Yu, kompilator porównuje bieżącego środowiska kompilacji, który, które istniały podczas tworzenia pliku PCH. Pamiętaj określić środowisko, które są zgodne z poprzedniego (przy użyciu opcji kompilatora spójne, pragm i tak dalej) dla bieżącej kompilacji. Jeśli kompilator wykryje niespójność, generuje ostrzeżenie i identyfikuje niespójności, jeśli jest to możliwe. Takie ostrzeżenia nie musi oznaczać problem z plików PCH; oni po prostu ostrzega o potencjalnych konfliktów. W poniższych sekcjach opisano wymagania spójności wstępnie skompilowanych nagłówków.

### <a name="compiler-option-consistency"></a>Spójność — opcja kompilatora

Poniższa tabela zawiera listę opcji kompilatora, który może wyzwalać ostrzeżenie niespójności, po użyciu prekompilowanego nagłówka:

|Opcja|Nazwa|Reguła|
|------------|----------|----------|
|/D|Definiowanie stałych i makr|Musi być taka sama, między kompilacji, który utworzony prekompilowany plik nagłówkowy i bieżącej kompilacji. Stan zdefiniowanych stałych nie jest zaznaczone, ale nieprzewidywalne skutki może wystąpić, jeśli pliki są zależne od wartości stałe zmienione.|
|/E lub /EP|Kopiuj dane wyjściowe preprocesora do wyjścia standardowego|Nie działają z opcją/e lub /EP wstępnie skompilowanych nagłówków.|
|/FR lub /FR|Generuj informacje przeglądarka źródeł firmy Microsoft|Dla opcji /Fr i /FR ważność z opcją /Yu musi również zostały obowiązuje podczas tworzenia prekompilowanego pliku nagłówkowego. Kolejne kompilacje, korzystających z prekompilowanego pliku nagłówkowego również generuje informacje ze źródła przeglądarki. Informacje o przeglądarce zostanie umieszczony w pliku SBR pojedynczego i jest przywoływany przez inne pliki w taki sam sposób jak informacje CodeView. Nie można zastąpić położenie przeglądarka źródeł informacji.|
|/ GA, /GD, /GE, /Gw lub /GW|Opcje protokołu Windows|Musi być taka sama, między kompilacji, który utworzony prekompilowany plik nagłówkowy i bieżącej kompilacji. Jeśli te opcje są różne, wyniki komunikat ostrzegawczy.|
|/Zi|Generowanie kompletne informacje debugowania|Jeśli ta opcja jest aktywna, podczas tworzenia prekompilowanego pliku nagłówkowego, kolejne kompilacje, które używają wstępnej kompilacji można użyć tych informacji debugowania. Jeśli/zi nie jest włączona podczas tworzenia prekompilowanego pliku nagłówkowego, kolejne kompilacje, korzystających z opcji/zi i personalizacja wyzwalanie ostrzeżenie. Informacje o debugowaniu znajduje się w bieżącym pliku obiektu, a symbole lokalne zdefiniowane w prekompilowanego pliku nagłówkowego nie są dostępne do debugera.|

> [!NOTE]
>  Funkcji prekompilowanego pliku nagłówkowego jest przeznaczony do użytku tylko w plikach źródłowych C i C++.

## <a name="using-precompiled-headers-in-a-project"></a>Stosowanie w projekcie prekompilowanych nagłówków

Poprzednie sekcje zawierają omówienie wstępnie skompilowanych nagłówków: /Yc i /Yu z opcją/FP i [hdrstop](../preprocessor/hdrstop.md) pragmy. W tej sekcji opisano metody przy użyciu ręcznych opcji wstępnie skompilowanego nagłówka w projekcie; kończy się ona przykład pliku reguł programu make i kod, który zarządza.

Dla innego podejścia do przy użyciu ręcznych opcji wstępnie skompilowanego nagłówka w projekcie badanie jeden z plików reguł programu make znajduje się w katalogu MFC\SRC, który jest tworzony podczas instalacji domyślnej w Visual c++. Te pliki reguł programu make zastosować podejście podobne do przedstawionego znajdujące się w tej sekcji, ale większe wykorzystanie makr firmy Microsoft Program obsługi narzędzia (NMAKE) i oferują większą kontrolę nad procesem kompilacji.

## <a name="pch-files-in-the-build-process"></a>Pliki PCH w procesie kompilacji

Podstawa kodu z projektem oprogramowania jest zwykle zawarty w wielu C lub C++ plików źródłowych, plikach obiektowych, biblioteki i pliki nagłówkowe. Zazwyczaj pliku reguł programu make koordynuje kombinacji tych elementów do pliku wykonywalnego. Poniższa ilustracja przedstawia strukturę pliku reguł programu make, która korzysta z prekompilowanego pliku nagłówka. Nazwy makr NMAKE i nazwy plików, w tym diagramie są spójne z identyfikatorami w przykładowym kodzie w [przykładowy plik reguł programu make dla PCH](#sample-makefile-for-pch) i [przykład kodu dla PCH](#example-code-for-pch).

Rysunek używa trzech urządzeń diagramu, aby pokazać przepływ procesu kompilacji. O nazwie prostokąty reprezentują każdego pliku lub makro; trzy makra reprezentuje jeden lub więcej plików. Zacieniony obszary reprezentują każde działanie kompilacji lub łącza. Strzałki oznaczają, które pliki i makra są łączone podczas kompilacji lub proces łączenia.

![Struktura pliku reguł programu make, która korzysta z prekompilowanego pliku nagłówka](media/vc30ow1.gif "strukturę pliku reguł programu make, która korzysta z prekompilowanego pliku nagłówka") <br/>
Struktura pliku reguł programu make, która korzysta z Prekompilowanego pliku nagłówka

Począwszy od góry diagramu STABLEHDRS i GRANICZNY są makra NMAKE, w których możesz wyświetlić listę plików, prawdopodobnie nie będzie ponownej kompilacji. Te pliki są kompilowane przez ciąg polecenia

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

tylko wtedy, gdy prekompilowanego pliku nagłówkowego (STABLE.pch) nie istnieje, lub wprowadzić zmiany do plików wymienionych w dwa makra. W obu przypadkach prekompilowanego pliku nagłówkowego będzie zawierać kod tylko z plików wymienionych w makrze STABLEHDRS. Wyświetl listę ostatni plik, który ma wstępnie skompilowanych w makrze GRANICZNY.

Pliki listy w tych makr można pliki nagłówkowe i pliki źródłowe C lub C++. (Pojedynczy plik PCH nie można używać z modułami C i C++.) Należy zauważyć, że można użyć **hdrstop** makra, aby zatrzymać wstępnej kompilacji w pewnym momencie w pliku GRANICZNY. Zobacz [hdrstop](../preprocessor/hdrstop.md) Aby uzyskać więcej informacji.

Trwając w dół na diagramie, APPLIB.obj reprezentuje kod pomocy technicznej, używany w ostatnim aplikacji. Jest tworzona na podstawie APPLIB.cpp, plików wymienionych w makrze UNSTABLEHDRS i wstępnie skompilowany kod z prekompilowanego pliku nagłówkowego.

MYAPP.obj reprezentuje końcowego aplikacji. Jest tworzona na podstawie MYAPP.cpp, plików wymienionych w makrze UNSTABLEHDRS i wstępnie skompilowany kod z prekompilowanego pliku nagłówkowego.

Na koniec pliku wykonywalnego (MYAPP. Z rozszerzeniem EXE) jest tworzony przez łączenie plików wymienionych w makrze OBJS (APPLIB.obj i MYAPP.obj).

## <a name="sample-makefile-for-pch"></a>Przykładowy plik pliku reguł programu Make dla PCH

Następujący plik makefile korzysta z makr i! JEŚLI! ELSE! Struktura polecenia sterowania przepływem ENDIF można uproszczenie dostosowania ich do projektu.

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
LINKFLAGS = /NOD /ONERROR:NOEXE
!IF "$(DEBUG)" == "1"
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi /f
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

Oprócz makra STABLEHDRS GRANICZNY i UNSTABLEHDRS pokazano na rysunku "Struktura z pliku reguł programu make, używa Prekompilowanego nagłówka pliku" w [pliki PCH w procesie kompilacji](#pch-files-in-the-build-process), ten plik reguł programu make zawiera makra CLFLAGS i LINKFLAGS makra. Aby wyświetlić listę kompilatora i opcje konsolidatora, które odnoszą się do zarówno kompilacji debugowania lub ostateczna wersja pliku wykonywalnego aplikacji, należy użyć tych makr. Istnieje również makro LIBS gdzie listy bibliotek Twój projekt wymaga.

Używa również pliku reguł programu make! JEŚLI! ELSE! ENDIF do wykrywania, czy w wierszu polecenia NMAKE zdefiniować symbol debugowania:

```NMAKE
NMAKE DEBUG=[1|0]
```

Ta funkcja umożliwia możesz użyć tego samego pliku reguł programu make podczas tworzenia i ostateczna wersja programu — użyj debugowania = 0 dla wersji końcowej. Następujące wiersze polecenia są równoważne:

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Aby uzyskać więcej informacji na temat plików reguł programu make, zobacz [odwołanie NMAKE](reference/nmake-reference.md). Zobacz też [opcje kompilatora MSVC](reference/compiler-options.md) i [opcje konsolidatora MSVC](reference/linker-options.md).

## <a name="example-code-for-pch"></a>Przykład kodu dla PCH

Następujące pliki źródłowe są używane w pliku reguł programu make opisanego w [pliki PCH w procesie kompilacji](#pch-files-in-the-build-process) i [przykładowy plik reguł programu make dla PCH](#sample-makefile-for-pch). Należy pamiętać, że komentarze zawierają ważne informacje.

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
#include<iostream.h>
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

## <a name="see-also"></a>Zobacz także

[Dokumentacja kompilacji w języku C/C++](reference/c-cpp-building-reference.md)<br/>
[MSVC Compiler Options](reference/compiler-options.md)
