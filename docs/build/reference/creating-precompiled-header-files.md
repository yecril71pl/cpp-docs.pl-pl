---
title: Tworzenie prekompilowanych plików nagłówka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- pch
dev_langs:
- C++
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 09c436d55ad7087d407ba580be0b63286b056898
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-precompiled-header-files"></a>Tworzenie prekompilowanych plików nagłówka
  
Kompilatory języka Microsoft C i C++ opcje dla wstępnej kompilacji dowolnego kodu języka C lub C++, w tym kodu wbudowanego. Tej funkcji wydajności można skompilować stabilna treści kodu, przechowywać skompilowanej kodu w pliku i, podczas kolejnych kompilacjach połączyć prekompilowany kod z kodem, który jest nadal w fazie projektowania. Każda kolejne Kompilacja trwa krócej, ponieważ stabilna kodu nie muszą być ponownie kompilowane.  
  
W tym temacie omówiono następujące zagadnienia prekompilowanego nagłówka:  
  
-   [Kiedy przeprowadzać Prekompilowanie kodu źródłowego](#when-to-precompile-source-code)  
  
-   [Dwa wybory dla wstępnej kompilacji kodu](#two-choices-for-precompiling-code)  
  
-   [Zasady spójności prekompilowanego nagłówka](#precompiled-header-consistency-rules)  
  
-   [Zasady spójności dla stosowanych do użycia dla plików nagłówków prekompilowanych](#consistency-rules-for-per-file-use-of-precompiled-headers)  
  
-   [Zasady spójności dla /Yc i /Yu](#consistency-rules-for-yc-and-yu)  
  
-   [Stosowanie w projekcie prekompilowanych nagłówków](#using-precompiled-headers-in-a-project)  
  
-   [Pliki PCH w procesie kompilacji](#pch-files-in-the-build-process)  
  
-   [Przykład pliku reguł programu make dla PCH](#sample-makefile-for-pch)  
  
-   [Przykład kodu dla PCH](#example-code-for-pch)  
  
Aby uzyskać informacje na temat opcji kompilatora związane z prekompilowanych nagłówków, zobacz [/Y (prekompilowane nagłówki)](../../build/reference/y-precompiled-headers.md).  
  
<a name="when-to-precompile-source-code"></a>  
  
## <a name="when-to-precompile-source-code"></a>Kiedy przeprowadzać prekompilowanie kodu źródłowego  
  
Prekompilowany kod jest przydatne podczas cyklu rozwoju, aby skrócić czas kompilacji, zwłaszcza, jeśli:  
  
-   Zawsze używaj dużą porcję kodu, który zmienia się rzadko.  
  
-   Program obejmuje wiele modułów, które używają standardowego zestawu plików dołączanych i te same opcje kompilacji. W takim przypadku Dołącz wszystkie pliki mogą być wstępnie skompilowany do jednego prekompilowanego nagłówka.  
  
Pierwszy kompilacji — jedną, która tworzy plik prekompilowanego nagłówka (PCH) — nieco dłużej, niż kolejne kompilacje. Kolejne kompilacje szybciej przejść przez dołączenie prekompilowany kodu.  
  
Można prekompilowanie programy zarówno C i C++. W języku C++ programowania jest powszechną praktyką było oddzielne informacje o interfejsie klasa plikami nagłówka. Te pliki nagłówkowe później mogą zostać włączone w programach korzystających z tej klasy. Przez prekompilowanie tych nagłówków, można zmniejszyć czas programu kompilacji.  
  
> [!NOTE]
>  Chociaż można używać tylko jednego pliku prekompilowanego nagłówka (.pch) dla pliku źródłowego, można użyć wielu .pch — pliki w projekcie.  
  
<a name="two-choices-for-precompiling-code"></a>  
  
# <a name="two-choices-for-precompiling-code"></a>Dwa wybory dla wstępnej kompilacji kodu  
  
Z programem Visual C++ można wstępnej kompilacji C lub C++ kod; nie są ograniczone do prekompilowanie tylko pliki nagłówków.  
  
Prekompilowanie wymaga zaplanowania, ale zapewnia znacznie szybsze kompilacji w przypadku prekompilowanie kodu źródłowego innych niż pliki nagłówkowe proste.  
  
Prekompilowanie kodu, gdy wiesz, że plików źródłowych użyj zestawy wspólne pliki nagłówkowe, ale nie je uwzględnić w tej samej kolejności, lub gdy chcesz uwzględnić w Twojej wstępnej kompilacji kodu źródłowego.  
  
Dostępne są następujące opcje prekompilowanego nagłówka [/Yc (Utwórz prekompilowany plik nagłówka)](../../build/reference/yc-create-precompiled-header-file.md) i [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](../../build/reference/yu-use-precompiled-header-file.md). Użyj **/Yc** do utworzenia prekompilowanego nagłówka. Gdy jest używany z opcjonalnym [hdrstop](../../preprocessor/hdrstop.md) pragma, **/Yc** umożliwia prekompilowanie oba pliki nagłówka i kod źródłowy. Wybierz **/Yu** do używania istniejącego prekompilowanego nagłówka w istniejących kompilacji. Można również użyć **/FP** z **/Yc** i **/Yu** opcje w celu zapewnienia alternatywnej nazwy dla prekompilowanego nagłówka.  
  
Tematy odwołań — opcja kompilatora dla **/Yu** i **/Yc** omówiono sposób korzystania z tej funkcji w środowisku programistycznym.  
  
<a name="precompiled-header-consistency-rules"></a>  
  
## <a name="precompiled-header-consistency-rules"></a>Zasady spójności prekompilowanego nagłówka  
  
Ponieważ PCH, pliki zawierają informacje o środowisku maszyny, a także informacje dotyczące adresów pamięci o programie, należy używać tylko plik PCH na komputerze, w której został utworzony.  
  
<a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>  
  
## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Zasady spójności dla stosowanych dla prekompilowanych plików nagłówka

[/Yu](../../build/reference/yu-use-precompiled-header-file.md) — opcja kompilatora pozwala określić plik PCH.  
  
Korzystając z plików PCH, kompilator przyjęto założenie, w tym samym środowisku kompilacji — korzystającą — opcje kompilatora spójne, pragm i tak dalej, które obowiązywały podczas tworzenia pliku PCH, chyba że określono inaczej. W przypadku wykrycia niespójności przez kompilator, ostrzeżenie i identyfikuje niespójności, jeśli jest to możliwe. Takie ostrzeżenia nie wskazują na problem z plików PCH; ich po prostu ostrzegać o potencjalnych konfliktów. W poniższych sekcjach opisano wymagania spójności dla PCH, pliki.  
  
### <a name="compiler-option-consistency"></a>Spójność — opcja kompilatora  
  
Następujące opcje kompilatora wyzwolić ostrzeżenie niespójność podczas korzystania z pliku PCH:  
  
-   Makra utworzone za pomocą preprocesora (/ D) opcja muszą być takie same, między kompilacji, która utworzyła plik PCH i bieżącej kompilacji. Stan zdefiniowanych stałych nie jest zaznaczone, ale może wystąpić nieprzewidywalne skutki, jeśli te zmiany.  
  
-   PCH, pliki nie działają z opcjami/e i /EP.  
  
-   PCH, pliki muszą być utworzone przy użyciu albo Generowanie przeglądać informacje (/ FR) opcja lub wykluczyć zmienne lokalne (/ Fr) opcja przed kolejne kompilacje, korzystających z plików PCH mogą korzystać z tych opcji.  
  
### <a name="c-70-compatible-z7"></a>C zgodnego 7.0 (/ Z7)  
  
Jeśli ta opcja jest włączona, podczas tworzenia pliku PCH, kolejne kompilacje, korzystających z plików PCH można użyć informacji o debugowaniu.  
  
Jeśli C zgodnego 7.0 (/ Z7) opcja nie jest włączona podczas tworzenia pliku PCH, kolejne kompilacje, które korzystają z plików PCH oraz/z7 wyzwolenia ostrzeżenie. Informacje o debugowaniu znajduje się w bieżącym pliku .obj i lokalne symbole zdefiniowane w pliku PCH nie są dostępne do debugera.  
  
### <a name="include-path-consistency"></a>Obejmować spójność ścieżki  
  
Plik PCH nie zawiera informacji o ścieżki dołączenia, które obowiązywały podczas jej tworzenia. Korzystając z plików PCH, kompilator zawsze używa ścieżki dołączenia określony w bieżącej kompilacji.  
  
### <a name="source-file-consistency"></a>Spójność pliku źródłowego  
  
Po określeniu opcji Użyj Prekompilowanego nagłówka pliku (/Yu) Kompilator ignoruje wszystkie dyrektywy preprocesora (w tym pragm), które pojawiają się w kodzie źródłowym, który zostanie wstępnie skompilowana. Kompilacja określony przez takie dyrektywy preprocesora musi być taka sama jak kompilacji używany dla opcji tworzenia Prekompilowanego pliku nagłówkowego (/Yc).  
  
### <a name="pragma-consistency"></a>Pragma spójności    
  
Pragma przetworzone podczas tworzenia pliku PCH zwykle mają wpływ na plik, z którym plik PCH są następnie używane. `comment` i `message` pragm nie ma wpływu na pozostałą część kompilacji.  
  
Pragma te mają wpływ na kod w pliku PCH; nie ma wpływu na kod, który następnie używa pliku PCH:  
  
||||  
|-|-|-|  
|`comment`|`page`|`subtitle`|  
|`linesize`|`pagesize`|`title`|  
|`message`|`skip`||  
  
Pragma te są przechowywane jako część prekompilowanego nagłówka i mają wpływ na pozostałą część kompilacji, która używa prekompilowanego nagłówka:  
  
||||  
|-|-|-|  
|`alloc_text`|`include_alias`|`pack`|  
|`auto_inline`|`init_seg`|`pointers_to_members`|  
|`check_stack`|`inline_depth`|`setlocale`|  
|`code_seg`|`inline_recursion`|`vtordisp`|  
|`data_seg`|`intrinsic`|`warning`|  
|`function`|`optimize`||  
  
<a name="consistency-rules-for-yc-and-yu"></a>  
  
## <a name="consistency-rules-for-yc-and-yu"></a>Zasady spójności dla /Yc i /Yu  
  
Użycie prekompilowanego nagłówka, utworzone za pomocą /Yc i /Yu, kompilator porównuje w bieżącym środowisku kompilacji do tego, które istniały podczas tworzenia pliku PCH. Należy określić środowisko zgodne z poprzedniego (przy użyciu opcji kompilatora spójne, pragm i tak dalej) dla bieżącej kompilacji. W przypadku wykrycia niespójności przez kompilator, ostrzeżenie i identyfikuje niespójności, jeśli jest to możliwe. Takie ostrzeżenia nie musi oznaczać problem z plików PCH; ich po prostu ostrzegać o potencjalnych konfliktów. W poniższych sekcjach opisano wymagania spójności prekompilowanych nagłówków.  
  
### <a name="compiler-option-consistency"></a>Spójność — opcja kompilatora  
  
Poniższa tabela zawiera opcje kompilatora, które mogą wyzwalać ostrzeżenie niespójności po użyciu prekompilowanego nagłówka:  
  
|Opcja|Nazwa|Reguła|  
|------------|----------|----------|  
|/D|Definiowanie stałych i makra|Musi być taka sama między kompilacji, która utworzona prekompilowany nagłówek i bieżącej kompilacji. Stan zdefiniowanych stałych nie jest zaznaczone, ale nieprzewidywalne skutki może wystąpić, jeśli pliki są zależne od wartości stałe zmienione.|  
|/E lub /EP|Kopiuj dane wyjściowe preprocesora do wyjścia standardowego|Prekompilowane nagłówki nie działają z opcją/e lub /EP.|  
|/FR lub /FR|Generowanie informacji firmy Microsoft przeglądarki źródła|Dla opcji /Fr i /FR ważność z opcją /Yu musi również zostały skutkuje podczas tworzenia prekompilowanego nagłówka. Kolejne kompilacje, które używają prekompilowanego nagłówka również generować informacji przeglądarki źródła. Informacje o przeglądarce znajduje się w pliku SBR pojedynczego i odwołuje się do niego inne pliki w taki sam sposób jak informacje CodeView. Nie można zastąpić umieszczania przeglądarki źródła informacji.|  
|/ GA /GD, /GE, /Gw albo /GW|Opcje protokołu systemu Windows|Musi być taka sama między kompilacji, która utworzona prekompilowany nagłówek i bieżącej kompilacji. Jeśli te opcje są różne, powoduje komunikat ostrzegawczy.|  
|/ Zi|Generowanie pełne informacje debugowania|Jeśli ta opcja jest włączona, podczas tworzenia prekompilowanego nagłówka, kolejne kompilacje, które używają wstępnej kompilacji można użyć tych informacji debugowania. Jeśli/zi jest obowiązująca podczas tworzenia prekompilowanego nagłówka, kolejne kompilacje, które używają wstępnej kompilacji i/zi, opcja wyzwolenia ostrzeżenie. Informacje o debugowaniu znajduje się w bieżącym pliku obiektu, a lokalny symboli zdefiniowanych we prekompilowanym nagłówku nie są dostępne do debugera.|  
  
> [!NOTE]
>  Funkcji prekompilowany nagłówek jest przeznaczony do użycia tylko w plikach źródłowych C i C++.  
  
<a name="using-precompiled-headers-in-a-project"></a>  
  
## <a name="using-precompiled-headers-in-a-project"></a>Stosowanie w projekcie prekompilowanych nagłówków  
  
Przedstawione w poprzednich sekcjach dostępne prekompilowanych nagłówków: /Yc i /Yu, opcja/FP i [hdrstop](../../preprocessor/hdrstop.md) pragma. W tej sekcji opisano metody przy użyciu opcji ręcznego prekompilowanego nagłówka w projekcie; kończy się przykład pliku reguł programu make i kod, który zarządza.  
  
Innego podejścia do przy użyciu opcji ręcznego prekompilowanego nagłówka w projekcie badanie co pliki reguł programu make znajduje się w katalogu MFC\SRC, która jest tworzona podczas instalacji domyślnej programu Visual C++. Te pliki reguł programu make zastosować podejście podobne do przedstawionego przedstawionych w tej sekcji, ale w większym stopniu wykorzystują makr Microsoft Program obsługi narzędzia (NMAKE), a także oferują większą kontrolę nad procesu kompilacji.  
  
<a name="pch-files-in-the-build-process"></a>  
  
## <a name="pch-files-in-the-build-process"></a>Pliki PCH w procesie kompilacji  
  
Ścieżki bazowej kodu projektu oprogramowania zwykle znajduje się w wielu C lub C++ pliki źródłowe, pliki obiektów biblioteki i pliki nagłówkowe. Zazwyczaj pliku reguł programu make koordynuje kombinacji tych elementów do pliku wykonywalnego. Na poniższej ilustracji przedstawiono struktury pliku reguł programu make, która używa prekompilowanego pliku nagłówkowego. Nazwy makr NMAKE i nazwy plików na tym diagramie są spójne z identyfikatorami w przykładowym kodzie w [próbki pliku reguł programu make dla PCH](#sample-makefile-for-pch) i [przykład kodu dla PCH](#example-code-for-pch).  
  
Rysunek używa trzech podającą urządzeń, aby pokazać przepływ procesu kompilacji. O nazwie reprezentują prostokąty każdego pliku lub makro; trzy makra reprezentuje jeden lub więcej plików. Obszary przyciemnione reprezentują każdej kompilacji lub łącza akcji. Strzałki oznaczają, które pliki i makra są łączone podczas kompilacji lub proces łączenia.  
  
![Pliku reguł programu make, która używa prekompilowanego pliku nagłówkowego](../../build/reference/media/vc30ow1.gif "struktura pliku reguł programu make, który używa Prekompilowanego pliku nagłówka")  
##### <a name="structure-of-a-makefile-that-uses-a-precompiled-header-file"></a>Struktura pliku reguł programu make, która używa Prekompilowanego pliku nagłówkowego  
  
Począwszy od góry diagramu zarówno STABLEHDRS, jak i GRANICZNY są makra NMAKE, w których można wyświetlić listę plików nie mogą wymagać ponownej kompilacji. Te pliki są kompilowane przez ciąg polecenia  
  
`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`  
  
tylko wtedy, gdy prekompilowanego pliku nagłówkowego (STABLE.pch) nie istnieje lub wprowadzić zmiany do plików wymienionych w dwóch makr. W obu przypadkach prekompilowanego pliku nagłówkowego będzie zawierać kod tylko z plików wymienionych w makrze STABLEHDRS. Wyświetl listę ostatni plik, który ma wstępnie skompilowana w makrze GRANICZNY.  
  
Pliki, lista w makrach można pliki nagłówkowe lub pliki źródłowe C lub C++. (Nie można używać w jednym pliku PCH z modułami zarówno C i C++.) Należy pamiętać, że można użyć **hdrstop** makra, aby zatrzymać wstępnej kompilacji w pewnym momencie w pliku GRANICZNY. Zobacz [hdrstop](../../preprocessor/hdrstop.md) Aby uzyskać więcej informacji.  
  
Kontynuowanie w dół na diagramie, APPLIB.obj reprezentuje kod obsługi używany w końcowym aplikacji. Jest tworzona na podstawie APPLIB.cpp, plików wymienionych w makrze UNSTABLEHDRS i wstępnie skompilowana kod z prekompilowanego nagłówka.  
  
MYAPP.obj reprezentuje ostatecznego aplikacji. Jest tworzona na podstawie MYAPP.cpp, plików wymienionych w makrze UNSTABLEHDRS i wstępnie skompilowana kod z prekompilowanego nagłówka.  
  
Na koniec pliku wykonywalnego (MOJA_APLIKACJA. Wywołanie pliku EXE) jest tworzony przez łączenie plików wymienionych w makrze OBJS (APPLIB.obj i MYAPP.obj).  
  
<a name="sample-makefile-for-pch"></a>  
  
## <a name="sample-makefile-for-pch"></a>Przykładowy plik pliku reguł programu Make dla PCH  
  
Makra korzysta z następującego pliku reguł programu make a! JEŚLI! #ELSE! Struktura polecenia sterowania przepływem ENDIF uprościć jego dostosowania do projektu.  
  
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
  
Jako uzupełnienie makra STABLEHDRS GRANICZNY i UNSTABLEHDRS pokazano na rysunku "Struktura z pliku reguł programu make czy używa Prekompilowanego pliku nagłówka" [pliki PCH w procesie kompilacji](#pch-files-in-the-build-process), tego pliku reguł programu make zapewnia makro CLFLAGS i LINKFLAGS makra. Aby wyświetlić listę kompilatora i opcje konsolidatora, które mają zastosowanie zarówno kompilacji debugowania i ostateczną wersją plik wykonywalny aplikacji, należy użyć tych makr. Istnieje również makro biblioteki gdzie listy bibliotek wymaga projektu.  
  
Używa również pliku reguł programu make! JEŚLI! #ELSE! ENDIF do wykrywania, czy zdefiniować symbolu debugowania w wierszu polecenia NMAKE:  
  
```NMAKE  
NMAKE DEBUG=[1|0]  
```  
  
Ta funkcja umożliwia można użyć tego samego pliku reguł programu make podczas tworzenia i ostateczne wersje programu — użyj debugowania = 0 w przypadku ostateczne wersje. Następujące wiersze polecenia są równoważne:  
  
```NMAKE  
NMAKE   
NMAKE DEBUG=0  
```  
  
Aby uzyskać więcej informacji dotyczących pliki reguł programu make, zobacz [odwołanie NMAKE](../../build/nmake-reference.md). Zobacz też [— opcje kompilatora](../../build/reference/compiler-options.md) i [opcje konsolidatora](../../build/reference/linker-options.md).  
  
<a name="example-code-for-pch"></a>  
  
## <a name="example-code-for-pch"></a>Przykład kodu dla PCH  
  
Następujące pliki źródłowe są używane w pliku reguł programu make opisanego w [pliki PCH w procesie kompilacji](#pch-files-in-the-build-process) i [próbki pliku reguł programu make dla PCH](#sample-makefile-for-pch). Należy pamiętać, że komentarze zawiera ważne informacje.  
  
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
    
## <a name="see-also"></a>Zobacz też  
[Odwołanie kompilacji C/C++](../../build/reference/c-cpp-building-reference.md)   
[Opcje kompilatora](../../build/reference/compiler-options.md)