---
title: Funkcje bibliotek CRT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/13/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- MSVCR71.dll
- libraries [C++], multithreaded
- library files, run-time
- LIBCMT.lib
- LIBCP.lib
- LIBCPMT.lib
- run-time libraries, C
- CRT, release versions
- MSVCP71.dll
- LIBC.lib
- libraries [C++]
- libraries [C++], run-time
- linking [C++], libraries
ms.assetid: a889fd39-807d-48f2-807f-81492612463f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b0ccedc3a1794b34fce3ad773e44155f7602d3b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704727"
---
# <a name="crt-library-features"></a>Biblioteka CRT — Funkcje

W tym temacie omówiono różne pliki .lib wchodzące w skład biblioteki wykonawcze języka C, a także ich — opcje kompilatora skojarzone i dyrektywy preprocesora.

## <a name="c-run-time-libraries-crt"></a>Biblioteki C-Run-Time (CRT)

Biblioteki wykonawcze języka C (CRT) jest częścią standardowa biblioteka C++, która będzie zawierała ISO C99 standardowa biblioteka. Bibliotek języka Visual C++, które implementują CRT obsługuje programowanie kodu natywnego, a jednocześnie mieszanym kodu natywnego i zarządzanego. Wszystkie wersje CRT obsługuje programowanie wielowątkowych. Większość bibliotek obsługuje zarówno statyczne połączenie, aby połączyć biblioteki bezpośrednio w kodzie, lub Konsolidacja dynamiczna, aby umożliwić plików kodu użycie wspólnej biblioteki DLL.

Począwszy od programu Visual Studio 2015 CRT ma został zrefaktoryzowany do nowych danych binarnych. Universal CRT (Biblioteka UCRT) zawiera funkcje i zmienne globalne wyeksportowane przez standardowa biblioteka C99 CRT. Biblioteka UCRT jest teraz składnik systemu Windows i jest dostarczana jako część systemu Windows 10. Biblioteka statyczna, biblioteki importowanej biblioteki DLL i pliki nagłówkowe dla Biblioteka UCRT znajdują się teraz w zestawie SDK systemu Windows 10. Po zainstalowaniu programu Visual C++, Visual Studio instalacja podzbiór musieli używać Biblioteka UCRT zestawu Windows 10 SDK. Biblioteka UCRT można użyć w dowolnej wersji systemu Windows obsługiwane przez Visual Studio 2015 i nowszych wersjach. Można rozpowszechniać za pomocą programu vcredist obsługiwane wersje systemu Windows, innym niż Windows 10. Aby uzyskać więcej informacji, zobacz [redystrybuowanie pliki Visual C++](../ide/redistributing-visual-cpp-files.md).

W poniższej tabeli wymieniono bibliotek, które implementują Biblioteka UCRT.

|Biblioteka|Skojarzone biblioteki DLL|Właściwości|Opcja|Dyrektywy preprocesora|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libucrt.lib|Brak|Statycznie łącza Biblioteka UCRT w kodzie.|**/MT**|_MT|
|libucrtd.lib|Brak|Debugować wersję Biblioteka UCRT statycznego łączenia. Nie do dystrybucji.|**/ MTd**|_DEBUG, _MT|
|ucrt.lib|ucrtbase.dll|Importuj biblioteki DLL Biblioteka UCRT.|**/MD**|_MT, _DLL|
|ucrtd.lib|ucrtbased.dll|Biblioteki DLL Importuj biblioteki dla wersji debugowania Biblioteka UCRT. Nie do dystrybucji.|**/MDd**|_DEBUG, _MT, _DLL|

Biblioteka vcruntime zawiera Visual C++ CRT specyficzne dla implementacji kodu, na przykład wyjątek obsługi i pomocy technicznej, Sprawdzanie czasu wykonania i informacje o typie, szczegóły implementacji i niektórych funkcji rozszerzonej biblioteki debugowania. Ta biblioteka jest specyficzne dla wersji kompilatora używane.

Ta tabela zawiera listę bibliotek, które implementują biblioteki vcruntime.

|Biblioteka|Skojarzone biblioteki DLL|Właściwości|Opcja|Dyrektywy preprocesora|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libvcruntime.lib|Brak|Połączone statycznie do kodu.|**/MT**|_MT|
|libvcruntimed.lib|Brak|W wersji do debugowania statycznego łączenia. Nie do dystrybucji.|**/ MTd**|_MT, _DEBUG|
|vcruntime.lib|vcruntime\<version>.dll|Importuj biblioteki DLL vcruntime.|**/MD**|_MT, _DLL|
|vcruntimed.lib|vcruntime\<version>d.dll|Importuj biblioteki DLL vcruntime debugowania. Nie do dystrybucji.|**/MDd**|_DEBUG, _MT, _DLL|

Kod, który inicjuje CRT ma jeden z kilku bibliotek, zależnie od tego, czy biblioteka CRT ma statycznie lub dynamicznie połączone, lub macierzystego, zarządzanego lub mieszanym kodu. Ten kod obsługuje uruchamianie CRT, Wątek wewnętrznego inicjowania danych i kończenie działania. Dotyczy wersji kompilatora używane. Ta biblioteka jest zawsze połączone statycznie, nawet w przypadku korzystania z dynamicznie połączony Biblioteka UCRT.

Ta tabela zawiera listę bibliotek, które implementują CRT inicjowanie i kończenie działania.

|Biblioteka|Właściwości|Opcja|Dyrektywy preprocesora|
|-------------|---------------------|------------|-----------------------------|
|libcmt.lib|Statycznie łączy natywnego uruchamiania CRT w kodzie.|**/MT**|_MT|
|libcmtd.lib|Statycznie łączy wersja do debugowania natywnego uruchamiania CRT. Nie do dystrybucji.|**/ MTd**|_DEBUG, _MT|
|msvcrt.lib|Biblioteka statyczna dla natywnej uruchomienia CRT do użycia z biblioteki DLL Biblioteka UCRT i vcruntime.|**/MD**|_MT, _DLL|
|msvcrtd.lib|Biblioteka statyczna dla wersji do debugowania natywnego uruchamiania CRT do użycia z biblioteki DLL Biblioteka UCRT i vcruntime. Nie do dystrybucji.|**/MDd**|_DEBUG, _MT, _DLL|
|msvcmrt.lib|Biblioteka statyczna mieszanych początkowa CRT natywnych i zarządzanych do użycia z biblioteki DLL Biblioteka UCRT i vcruntime.|**/clr**||
|msvcmrtd.lib|Biblioteka statyczna dla wersji do debugowania mieszanych uruchamiania CRT natywnego i zarządzanego służących do biblioteki DLL Biblioteka UCRT i vcruntime. Nie do dystrybucji.|**/clr**||
|msvcurt.lib|**Przestarzałe** biblioteki statycznej dla czystych zarządzanego CRT.|**/ CLR: pure**||
|msvcurtd.lib|**Przestarzałe** biblioteki statycznej wersji debugowania czyste zarządzanego CRT. Nie do dystrybucji.|**/ CLR: pure**||

Jeśli łączysz się z programem w wierszu polecenia bez opcji kompilatora, która określa biblioteki wykonawczej języka C, konsolidator użyje statycznie połączonych bibliotek CRT: libcmt.lib, libvcruntime.lib i libucrt.lib.

Przy użyciu statycznie połączone CRT oznacza, że żadnych informacji o stanie zapisane przez bibliotekę środowiska uruchomieniowego C będzie być lokalne dla danego wystąpienia CRT. Na przykład, jeśli używasz [strtok —, _strtok_l —, wcstok —, _wcstok_l —, _mbstok —, _mbstok_l —](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) używając statycznie połączone CRT, pozycja `strtok` Analizator jest niezwiązanych ze sobą `strtok` stanu używane w kodzie w tym samym procesie (ale innego pliku DLL lub EXE) jest połączony do innego wystąpienia CRT statycznych. Z kolei dynamicznie połączony CRT udostępnia stanu dla całego kodu w ramach procesu, która jest połączona dynamicznie CRT. Tego problemu nie ma zastosowania, jeśli używasz bezpieczniejsze nowe wersje tych funkcji; na przykład `strtok_s` ten problem nie występuje.

Ponieważ utworzony przez łączenie z statycznych CRT biblioteki DLL nie będzie mieć stanu CRT, nie zaleca się statycznie Połącz z CRT w bibliotece DLL, chyba że skutków to specjalnie są potrzebne i zrozumienie. Na przykład, jeśli wywołujesz [_set_se_translator —](../c-runtime-library/reference/set-se-translator.md) w pliku wykonywalnego, który ładuje bibliotekę DLL, połączony z własną CRT statycznych, wszelkie wyjątki sprzętowe wygenerowane przez kod w bibliotece DLL nie zostanie przechwycony przez translator, ale wyjątki sprzętowe wygenerowane przez kod w głównym pliku wykonywalnego, który zostanie przechwycony.

Jeśli używasz **/CLR** przełącznika kompilatora, kod zostanie połączony z biblioteką statyczną, msvcmrt.lib. Biblioteka statyczna zawiera serwer proxy między kodu zarządzanego i natywnego CRT. Nie można użyć statycznie połączone CRT ( **/MT** lub **/MTd** opcje) z **/CLR**. Użyj połączone dynamicznie biblioteki (**/ / MD** lub **/mdd**) zamiast tego. Czysty bibliotek CRT zarządzanym są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

Aby uzyskać więcej informacji na temat używania CRT z **/CLR**, zobacz [zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md).

Aby utworzyć wersję debugowania aplikacji, [_DEBUG](../c-runtime-library/debug.md) flagi muszą być zdefiniowane i aplikacji musi być połączony z wersją debugowania jednego z tych bibliotek. Aby uzyskać więcej informacji o korzystaniu z wersji debugowania plików bibliotek, zobacz [techniki testowania CRT](/visualstudio/debugger/crt-debugging-techniques).

Ta wersja CRT nie jest w pełni zgodna ze standardem C99. W szczególności \<tgmath.h > nagłówka i makra pragma CX_LIMITED_RANGE/FP_CONTRACT nie są obsługiwane. Niektóre elementy, takie jak znaczenie specyfikatory parametrów w standardowych funkcjach we/wy domyślnie używają interpretacje starszej wersji. Można użyć zgodność-opcje kompilatora /Zc i określ opcje konsolidatora, aby kontrolować niektóre aspekty zgodność biblioteki

## <a name="c-standard-library"></a>Standardowa biblioteka C++

|Standardowa biblioteka C++|Właściwości|Opcja|Dyrektywy preprocesora|
|----------------------------|---------------------|------------|-----------------------------|
|libcpmt.lib|Wielowątkowe, statyczne łącze|**/MT**|_MT|
|msvcprt.lib|Łącze wielowątkowe, dynamicznych (Importuj biblioteki MSVCP*wersji*.dll)|**/MD**|_MT, _DLL|
|libcpmtd.lib|Wielowątkowe, statyczne łącze|**/ MTd**|_DEBUG, _MT|
|msvcprtd.lib|Łącze wielowątkowe, dynamicznych (Importuj biblioteki MSVCP*wersji*D.DLL)|**/MDd**|_DEBUG, _MT, _DLL|

Podczas tworzenia wersji projektu w jeden z podstawowych biblioteki wykonawcze języka C (libcmt.lib, msvcmrt.lib, msvcrt.lib) jest domyślnie połączony, w zależności od opcji kompilatora wybierz (wielowątkowe, biblioteki DLL, / CLR). Jeśli dołączysz jedną z [pliki nagłówkowe standardowej biblioteki C++](../standard-library/cpp-standard-library-header-files.md) w kodzie, to standardowa biblioteka C++ zostaną połączone w automatycznie przez program Visual C++ w czasie kompilacji. Na przykład:

```cpp
#include <ios>
```

W celu zapewnienia zgodności z binarnej więcej niż jeden plik DLL może zostać określona przez bibliotekę importu jednego. Wersja aktualizacji może powodować *kropka bibliotek*, oddziel bibliotek DLL, które wprowadzenie nowych funkcji biblioteki. Na przykład Visual Studio 2017 msvcp140_1.dll wersji 15,6 wprowadzone do obsługi funkcji dodatkowe biblioteki standardowej bez przerywania ABI obsługiwane przez msvcp140.dll. Biblioteki importu msvcprt.lib zawartych w zestawie narzędzi dla programu Visual Studio 2017 wersji 15,6 obsługuje zarówno bibliotek DLL, a program vcredist dla tej wersji instaluje zarówno biblioteki dll. Po dostarczonym, biblioteki kropka ma stały ABI i nigdy nie będą miały zależności w bibliotece nowsze kropka.

## <a name="what-problems-exist-if-an-application-uses-more-than-one-crt-version"></a>Jakie problemy istnieje, jeśli aplikacja korzysta z więcej niż jedną wersję CRT?

Jeśli masz więcej niż jeden plik DLL lub EXE, następnie może być więcej niż jeden CRT, czy korzystają z różnych wersji programu Visual C++. Na przykład statycznie łączenie CRT w wielu bibliotek DLL może stanowić ten sam problem. Ten problem z statycznych im monitory CRT deweloperzy zalecił kompilacji z **/ / MD** CRT biblioteki dll. Niepowodzenie z biblioteki DLL zasobów CRT granicy biblioteki DLL, mogą wystąpić problemy z niezgodnymi im monitory CRT i konieczne ponowne skompilowanie projektu za pomocą programu Visual C++.

Jeśli program używa więcej niż jedną wersję CRT, niektóre uwagę podczas przekazywania niektórych obiektów CRT (na przykład dojść do plików, ustawień regionalnych i zmiennych środowiskowych) poprzek granic DLL. Aby uzyskać więcej informacji na temat zagadnień związanych oraz sposobu ich rozwiązania zobacz [potencjalne błędy przekazywanie CRT obiektów między granic DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja biblioteki środowiska uruchomieniowego języka C](../c-runtime-library/c-run-time-library-reference.md)
