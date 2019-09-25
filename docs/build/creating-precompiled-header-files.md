---
title: Pliki prekompilowanego nagłówka
ms.date: 08/19/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 273d8cf996c2717339dd20dcbc7512f9c62afa8d
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "69630490"
---
# <a name="precompiled-header-files"></a>Pliki prekompilowanego nagłówka

Podczas tworzenia nowego projektu w programie Visual Studio do projektu zostanie dodany *prekompilowany plik nagłówkowy* o nazwie *PCH. h* . (W programie Visual Studio 2017 i starszych plik miał nazwę *stdafx. h*). Celem pliku jest przyspieszenie procesu kompilacji. Wszystkie stabilne pliki nagłówkowe, na przykład nagłówki biblioteki standardowej, `<vector>`takie jak, powinny być zawarte w tym miejscu. Prekompilowany nagłówek jest kompilowany tylko wtedy, gdy jest lub wszystkie pliki, które zawiera, są modyfikowane. Jeśli wprowadzasz tylko zmiany w kodzie źródłowym projektu, kompilacja pominie kompilację dla prekompilowanego nagłówka. 

Opcje kompilatora dla prekompilowanych nagłówków to [/y](reference/y-precompiled-headers.md). Na stronach właściwości projektu opcje znajdują się w obszarze **Właściwości konfiguracji > C/C++ > prekompilowane nagłówki**. Można zrezygnować z używania prekompilowanych nagłówków i określić nazwę pliku nagłówka oraz nazwę i ścieżkę pliku wyjściowego. 

## <a name="custom-precompiled-code"></a>Niestandardowy kod wstępnie skompilowany

W przypadku dużych projektów, które mają znaczny czas na kompilację, warto rozważyć utworzenie niestandardowych wstępnie skompilowanych plików. Język Microsoft C i C++ kompilatory udostępniają opcje wstępnego kompilowania dowolnych języków C lub C++ Code, w tym kodu wbudowanego. Korzystając z tej funkcji wydajności, można skompilować stabilną treść kodu, przechowywać skompilowany stan kodu w pliku i, podczas kolejnych kompilacji, połączyć wstępnie skompilowany kod z kodem, który jest nadal w fazie projektowania. Każda kolejna kompilacja jest szybsza, ponieważ stabilny kod nie musi być ponownie kompilowany.

## <a name="when-to-precompile-source-code"></a>Kiedy przeprowadzać prekompilowanie kodu źródłowego

Wstępnie skompilowany kod jest przydatny w cyklu programowania, aby skrócić czas kompilacji, zwłaszcza jeśli:

- Zawsze używasz dużej części kodu, która rzadko zmienia się.

- Program składa się z wielu modułów, z których wszystkie używają standardowego zestawu plików dołączanych i tych samych opcji kompilacji. W takim przypadku wszystkie pliki dołączane mogą być wstępnie skompilowane w jednym prekompilowanym nagłówku.

Pierwsza kompilacja — ta, która tworzy plik prekompilowanego nagłówka (PCH), zajmuje nieco więcej niż kolejne kompilacje. Kolejne kompilacje mogą szybciej przebiegać przez dołączenie wstępnie skompilowanego kodu.

Można wstępnie skompilować zarówno język C, C++ jak i programy. W C++ programowaniu typowym sposobem jest oddzielenie informacji o interfejsie klasy do plików nagłówkowych. Te pliki nagłówkowe można później dołączać do programów, które używają klasy. Wstępnie kompilując te nagłówki, można skrócić czas, jaki program zajmie kompilacją.

> [!NOTE]
> Chociaż można używać tylko jednego prekompilowanego pliku nagłówkowego (. pch) na plik źródłowy, można użyć wielu plików. PCH w projekcie.

## <a name="two-choices-for-precompiling-code"></a>Dwa wybory dla wstępnej kompilacji kodu

Można wstępnie skompilować wszystkie C lub C++ kod; nie można prekompilować tylko plików nagłówkowych.

Prekompilowanie wymaga planowania, ale oferuje znacznie szybsze kompilacje, Jeśli kompilujesz kod źródłowy inny niż proste pliki nagłówkowe.

Kompiluj kod wstępnie, gdy wiesz, że pliki źródłowe używają wspólnych zestawów plików nagłówkowych, ale nie dodawaj ich w tej samej kolejności lub jeśli chcesz dołączyć kod źródłowy do wstępnej kompilacji.

Opcje prekompilowanego nagłówka to [/YC (Tworzenie prekompilowanego pliku nagłówkowego)](reference/yc-create-precompiled-header-file.md) i [/Yu (Użyj prekompilowanego pliku nagłówkowego)](reference/yu-use-precompiled-header-file.md). Użyj **/YC** , aby utworzyć prekompilowany nagłówek. Gdy jest używany z opcjonalnym pragmą [hdrstop](../preprocessor/hdrstop.md) , **/YC** umożliwia wstępne skompilowanie zarówno plików nagłówkowych, jak i kodu źródłowego. Wybierz pozycję **/Yu** , aby użyć istniejącego prekompilowanego nagłówka w istniejącej kompilacji. Możesz również użyć **/FP** z opcjami **/YC** i **/Yu** , aby podać alternatywną nazwę prekompilowanego nagłówka.

Tematy dotyczące opcji kompilatora dla **/Yu** i **/YC** omawiają sposób uzyskiwania dostępu do tej funkcji w środowisku programistycznym.

## <a name="precompiled-header-consistency-rules"></a>Zasady spójności prekompilowanego nagłówka

Ponieważ pliki PCH zawierają informacje o środowisku komputera, a także informacje o adresie pamięci dotyczące programu, należy użyć pliku PCH na komputerze, na którym został utworzony.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Zasady spójności dla stosowanych dla prekompilowanych plików nagłówka

Opcja kompilatora [/Yu](reference/yu-use-precompiled-header-file.md) umożliwia określenie, który plik PCH ma być używany.

W przypadku korzystania z pliku PCH kompilator zakłada to samo środowisko kompilacji — jeden, który używa spójnych opcji kompilatora, dyrektywy pragma i tak dalej — który obowiązywał podczas tworzenia pliku PCH, o ile nie określono inaczej. Jeśli kompilator wykryje niespójność, wygeneruje ostrzeżenie i zidentyfikuje niespójność tam, gdzie jest to możliwe. Takie ostrzeżenia nie zawsze wskazują na problem z plikiem PCH; po prostu ostrzega o możliwych konfliktach. Wymagania dotyczące spójności dla plików PCH są opisane w poniższych sekcjach.

### <a name="compiler-option-consistency"></a>Spójność opcji kompilatora

Następujące opcje kompilatora mogą wyzwalać ostrzeżenie niespójności podczas korzystania z pliku PCH:

- Makra utworzone przy użyciu opcji preprocesora (/D) muszą być takie same między kompilacją, która utworzyła plik PCH i bieżącą kompilację. Stan zdefiniowanych stałych nie jest zaznaczony, ale w przypadku tych zmian mogą wystąpić nieprzewidywalne wyniki.

- Pliki PCH nie działają z opcjami/E i/EP.

- Pliki PCH muszą zostać utworzone przy użyciu opcji Generuj informacje o przeglądaniu (/FR) lub wykluczanie zmiennych lokalnych (/fr) przed kolejnymi kompilacjami korzystającymi z pliku PCH.

### <a name="c-70-compatible-z7"></a>C 7,0 — zgodny (/Z7)

Jeśli ta opcja obowiązuje podczas tworzenia pliku PCH, kolejne kompilacje korzystające z pliku PCH mogą korzystać z informacji o debugowaniu.

Jeśli opcja zgodne z C 7,0 (/Z7) nie obowiązuje po utworzeniu pliku PCH, kolejne kompilacje używające pliku PCH i/Z7 wyzwalają ostrzeżenie. Informacje o debugowaniu są umieszczane w bieżącym pliku. obj, a symbole lokalne zdefiniowane w pliku PCH nie są dostępne dla debugera.

### <a name="include-path-consistency"></a>Uwzględnij spójność ścieżki

Plik PCH nie zawiera informacji o ścieżce include, która obowiązywała podczas tworzenia. W przypadku korzystania z pliku PCH kompilator zawsze używa ścieżki dołączania określonej w bieżącej kompilacji.

### <a name="source-file-consistency"></a>Spójność pliku źródłowego

W przypadku określenia opcji Użyj prekompilowanego pliku nagłówkowego (/Yu) kompilator ignoruje wszystkie dyrektywy preprocesora (w tym dyrektywy pragma), które są wyświetlane w kodzie źródłowym, który zostanie wstępnie skompilowany. Kompilacja określona przez takie dyrektywy preprocesora musi być taka sama jak kompilacja użyta dla opcji Utwórz prekompilowany plik nagłówkowy (/Yc).

### <a name="pragma-consistency"></a>Spójności dyrektywy pragma

Dyrektywy pragma przetwarzane podczas tworzenia pliku PCH zwykle wpływają na plik, z którego następnie jest używany plik PCH. Dyrektywy `comment` i`message` nie wpływają na resztę kompilacji.

Te dyrektywy pragma wpływają tylko na kod w pliku PCH; nie mają one wpływu na kod, który następnie używa pliku PCH:

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

Te dyrektywy pragma są zachowywane jako część prekompilowanego nagłówka i wpływają na resztę kompilacji, która używa prekompilowanego nagłówka:

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>Zasady spójności dla /Yc i /Yu

Jeśli używasz prekompilowanego nagłówka utworzonego za pomocą/YC lub/Yu, kompilator porównuje bieżące środowisko kompilacji z tym, który istniał podczas tworzenia pliku PCH. Należy pamiętać o określeniu środowiska spójnego z poprzednim (przy użyciu spójnych opcji kompilatora, pragm i tak dalej) dla bieżącej kompilacji. Jeśli kompilator wykryje niespójność, wygeneruje ostrzeżenie i zidentyfikuje niespójność tam, gdzie jest to możliwe. Takie ostrzeżenia nie zawsze wskazują na problem z plikiem PCH; po prostu ostrzega o możliwych konfliktach. W poniższych sekcjach wyjaśniono wymagania dotyczące spójności dla prekompilowanych nagłówków.

### <a name="compiler-option-consistency"></a>Spójność opcji kompilatora

Ta tabela zawiera listę opcji kompilatora, które mogą wyzwolić ostrzeżenie niespójności przy użyciu prekompilowanego nagłówka:

|Opcja|Nazwa|Reguła|
|------------|----------|----------|
|/D|Definiowanie stałych i makr|Musi być taka sama między kompilacją, która utworzyła prekompilowany nagłówek i bieżącą kompilację. Stan zdefiniowanych stałych nie jest zaznaczony, ale mogą wystąpić nieprzewidywalne wyniki, jeśli pliki są zależne od wartości zmienionych stałych.|
|/E lub/EP|Kopiuj dane wyjściowe preprocesora do wyjścia standardowego|Prekompilowane nagłówki nie działają z opcją/E lub/EP.|
|/Fr lub/FR|Generuj informacje o przeglądarce Microsoft Source|Aby opcje/fr i/FR były prawidłowe dla opcji/Yu, muszą one być stosowane podczas tworzenia prekompilowanego nagłówka. Kolejne kompilacje, które używają prekompilowanego nagłówka, również generują informacje o przeglądarce źródłowej. Informacje o przeglądarce są umieszczane w jednym pliku. sbr i są odwołujące się do innych plików w taki sam sposób, jak informacje CodeView. Nie można zastąpić umieszczania informacji w przeglądarce źródłowej.|
|/GA,/GD,/GE,/GW lub/GW|Opcje protokołu systemu Windows|Musi być taka sama między kompilacją, która utworzyła prekompilowany nagłówek i bieżącą kompilację. Jeśli te opcje różnią się, zostanie wyświetlony komunikat ostrzegawczy.|
|/Zi|Generuj pełne informacje o debugowaniu|Jeśli ta opcja obowiązuje po utworzeniu prekompilowanego nagłówka, kolejne kompilacje używające prekompilowania mogą korzystać z tych informacji debugowania. Jeśli/Zi nie obowiązuje po utworzeniu prekompilowanego nagłówka, kolejne kompilacje używające prekompilacji i opcji/Zi wyzwalają ostrzeżenie. Informacje o debugowaniu są umieszczane w bieżącym pliku obiektu, a symbole lokalne zdefiniowane w prekompilowanym nagłówku nie są dostępne dla debugera.|

> [!NOTE]
>  Wstępnie skompilowany obiekt nagłówkowy jest przeznaczony do użytku tylko w języku C C++ i plikach źródłowych.

## <a name="using-precompiled-headers-in-a-project"></a>Stosowanie w projekcie prekompilowanych nagłówków

Poprzednie sekcje zawierają przegląd prekompilowanych nagłówków:/YC i/Yu, opcję/FP oraz [hdrstop](../preprocessor/hdrstop.md) pragma. W tej sekcji opisano metodę używania ręcznie wstępnie skompilowanych opcji nagłówka w projekcie; jest ona zakończona przykładowym plikem reguł programu make i zarządzanym kodem.

Inne podejście do używania opcji ręcznego prekompilowanego nagłówka w projekcie przeanalizuje jeden z plików reguł programu make znajdujących się w katalogu MFC\SRC, który jest tworzony podczas konfiguracji domyślnej programu Visual Studio. Te pliki reguł programu make są zgodne z podejściem przedstawionym w tej sekcji, ale nie pozwalają na lepsze korzystanie z makr narzędzia do konserwacji programów firmy Microsoft (NMAKE) i oferują większą kontrolę nad procesem kompilacji.

## <a name="pch-files-in-the-build-process"></a>Pliki PCH w procesie kompilacji

Baza kodu projektu oprogramowania zwykle znajduje się w wielu plikach C lub C++ źródłowych, plikach obiektów, bibliotekach i plikach nagłówkowych. Zwykle plik reguł programu make koordynuje kombinację tych elementów w pliku wykonywalnym. Na poniższej ilustracji przedstawiono strukturę pliku reguł programu make, który używa prekompilowanych plików nagłówkowych. Nazwy makr NMAKE i nazwy plików na tym diagramie są spójne z tymi w przykładowym kodzie znalezionym w [przykładowym pliku reguł programu make dla PCH](#sample-makefile-for-pch) i [przykładowego kodu dla PCH](#example-code-for-pch).

Rysunek używa trzech urządzeń diagramowy do wyświetlania przepływu procesu kompilacji. Nazwane prostokąty reprezentują każdy plik lub makro; trzy makra reprezentują jeden lub więcej plików. Zacienione obszary reprezentują każdą akcję kompilacji lub łącza. Strzałki pokazują, które pliki i makra są łączone podczas kompilacji lub procesu łączenia.

![Struktura pliku reguł programu make korzystającego z prekompilowanych plików nagłówkowych](media/vc30ow1.gif "Struktura pliku reguł programu make korzystającego z prekompilowanych plików nagłówkowych") <br/>
Struktura pliku reguł programu make korzystającego z prekompilowanych plików nagłówkowych

Począwszy od górnej części diagramu, zarówno STABLEHDRS, jak i powiązane są makrami NMAKE, w których można wyświetlić listę plików, które nie wymagają ponownej kompilacji. Te pliki są kompilowane przez ciąg polecenia

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

tylko wtedy, gdy prekompilowany plik nagłówkowy (stabilny. pch) nie istnieje lub wprowadzasz zmiany w plikach wymienionych w dwóch makrach. W obu przypadkach prekompilowany plik nagłówkowy będzie zawierał kod tylko z plików wymienionych w makrze STABLEHDRS. Utwórz listę ostatnio zakompilowanego pliku w powiązanym makrze.

Pliki znajdujące się w tych makrach mogą być plikami nagłówkowe lub C lub C++ plikami źródłowymi. (Pojedynczy plik PCH nie może być używany zarówno w języku C C++ , jak i w modułach.) Należy pamiętać, że można użyć makra **hdrstop** , aby zatrzymać prekompilowanie w pewnym momencie w pliku Bound. Aby uzyskać więcej informacji, zobacz [hdrstop](../preprocessor/hdrstop.md) .

Kontynuowanie diagramu APPLIB. obj reprezentuje kod pomocy technicznej używany w aplikacji końcowej. Jest tworzony z APPLIB. cpp, plików wymienionych w makrze UNSTABLEHDRS i prekompilowanego kodu z prekompilowanego nagłówka.

MOJAAPL. obj reprezentuje ostateczną aplikację. Jest tworzony na podstawie pliku MOJAAPL. cpp, plików wymienionych w makrze UNSTABLEHDRS i prekompilowanego kodu z prekompilowanego nagłówka.

Na koniec plik wykonywalny (MOJAAPL. EXE) jest tworzony przez połączenie plików wymienionych w makrze przywołujące obj zawierały (APPLIB. obj i MOJAAPL. obj).

## <a name="sample-makefile-for-pch"></a>Przykładowy plik pliku reguł programu Make dla PCH

Poniższy plik reguł programu make używa makr i! IF,! W przeciwnym razie! Struktura poleceń sterujących przepływem (ENDIF) do uproszczenia adaptacji do projektu.

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

Poza makrami STABLEHDRS, BOUNDs i UNSTABLEHDRS przedstawionymi w strukturze "Struktura pliku reguł programu make, który używa prekompilowanych plików nagłówkowych" w [plikach PCH w procesie kompilacji](#pch-files-in-the-build-process), ten plik reguł programu make zawiera makro CLFLAGS i makro LINKFLAGS. Należy użyć tych makr, aby wyświetlić listę opcji kompilatora i konsolidatora, które mają zastosowanie do tworzenia debugowania lub końcowej wersji pliku wykonywalnego aplikacji. Istnieje również makro LIBS, w którym można wyświetlić listę bibliotek wymaganych przez ten projekt.

Plik reguł programu make używa również! IF,! W przeciwnym razie! ENDIF, aby wykryć, czy zdefiniujesz symbol debugowania w wierszu polecenia NMAKE:

```NMAKE
NMAKE DEBUG=[1|0]
```

Ta funkcja umożliwia korzystanie z tego samego pliku reguł programu make podczas tworzenia i dla końcowych wersji programu — dla końcowych wersji należy używać debugowania = 0. Następujące wiersze polecenia są równoważne:

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Aby uzyskać więcej informacji na temat plików reguł programu make, zobacz [NMAKE Reference](reference/nmake-reference.md). Zobacz również opcje [kompilatora MSVC](reference/compiler-options.md) i [MSVC opcji konsolidatora](reference/linker-options.md).

## <a name="example-code-for-pch"></a>Przykład kodu dla PCH

Następujące pliki źródłowe są używane w pliku reguł programu make opisanym w [plikach PCH w procesie kompilacji](#pch-files-in-the-build-process) i [przykładowy plik reguł programu make dla PCH](#sample-makefile-for-pch). Zwróć uwagę, że komentarze zawierają ważne informacje.

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
[Opcje kompilatora MSVC](reference/compiler-options.md)
