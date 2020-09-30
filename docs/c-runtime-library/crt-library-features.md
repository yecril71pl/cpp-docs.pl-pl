---
title: Biblioteka CRT — Funkcje
description: Lista plików, które zawierają biblioteki środowiska uruchomieniowego języka Microsoft C i ich skojarzone opcje kompilatora i dyrektywy preprocesora.
ms.date: 09/03/2020
ms.topic: conceptual
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
ms.openlocfilehash: 0e0d34c1121f0bf4e2fdfabc521e0365084761eb
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589786"
---
# <a name="crt-library-features"></a>Biblioteka CRT — Funkcje

W tym temacie omówiono różne pliki. lib, które składają się z bibliotek środowiska uruchomieniowego C, a także ich skojarzone opcje kompilatora i dyrektywy preprocesora.

## <a name="c-run-time-libraries-crt"></a>Biblioteki C-Run-Time (CRT)

Biblioteka uruchomieniowa C (CRT) jest częścią standardowej biblioteki języka C++, która obejmuje standardową bibliotekę ISO C99. Biblioteki Visual C++, które implementują środowisko CRT obsługują Programowanie kodu natywnego, oraz kod natywny i zarządzany. Wszystkie wersje CRT obsługują programowanie wielowątkowe. Większość bibliotek obsługuje zarówno statyczne konsolidacje, aby połączyć bibliotekę bezpośrednio w kodzie, jak i dynamiczne łączenie, aby kod używał wspólnych plików DLL.

Począwszy od programu Visual Studio 2015, CRT został przestawiony do nowych plików binarnych. Uniwersalne środowisko CRT (UCRT) zawiera funkcje i Globals eksportowane przez standardową bibliotekę CRT C99. UCRT jest teraz składnikiem systemu Windows i jest dostarczany jako część systemu Windows 10. Biblioteki statycznej, biblioteka DLL importu i pliki nagłówkowe dla UCRT są teraz dostępne w zestawie SDK systemu Windows 10. Podczas instalowania Visual C++ Instalator programu Visual Studio instaluje podzestaw zestawu Windows 10 SDK wymaganego do korzystania z UCRT. UCRT można użyć w dowolnej wersji systemu Windows obsługiwanej przez program Visual Studio 2015 i jego nowsze wersje. Można ją rozpowszechniać za pomocą VCRedist dla obsługiwanych wersji systemu Windows innych niż Windows 10. Aby uzyskać więcej informacji, zobacz [Redystrybuowanie plików Visual C++](../windows/redistributing-visual-cpp-files.md).

Poniższa tabela zawiera listę bibliotek, które implementują UCRT.

| Biblioteka | Skojarzona Biblioteka DLL | Właściwości | Opcja | Dyrektywy preprocesora |
|--|--|--|--|--|
| *`libucrt.lib`* | Brak | Statycznie łączy UCRT z kodem. | **`/MT`** | `_MT` |
| *`libucrtd.lib`* | Brak | Wersja debugowania UCRT do konsolidacji statycznej. Nie redystrybucyjny. | **`/MTd`** | `_DEBUG`, `_MT` |
| *`ucrt.lib`* | *`ucrtbase.dll`* | Biblioteka importowania biblioteki DLL dla UCRT. | **`/MD`** | `_MT`, `_DLL` |
| *`ucrtd.lib`* | *`ucrtbased.dll`* | Biblioteka importowania bibliotek DLL dla wersji debugowania UCRT. Nie redystrybucyjny. | **`/MDd`** | `_DEBUG`, `_MT`, `_DLL` |

Biblioteka vcruntime Visual C++ zawiera kod specyficzny dla implementacji CRT, taki jak obsługa wyjątków i obsługa debugowania, kontrole środowiska uruchomieniowego i informacje o typie, szczegóły implementacji i niektóre funkcje biblioteki rozszerzonej. Ta biblioteka jest specyficzna dla używanej wersji kompilatora.

Ta tabela zawiera listę bibliotek implementujących bibliotekę vcruntime.

| Biblioteka | Skojarzona Biblioteka DLL | Właściwości | Opcja | Dyrektywy preprocesora |
|--|--|--|--|--|
| *`libvcruntime.lib`* | Brak | Statycznie połączone z kodem. | **`/MT`** | `_MT` |
| *`libvcruntimed.lib`* | Brak | Wersja do debugowania dla konsolidacji statycznej. Nie redystrybucyjny. | **`/MTd`** | `_MT`, `_DEBUG` |
| *`vcruntime.lib`* | *`vcruntime<version>.dll`* | Biblioteka importowania biblioteki DLL dla vcruntime. | **`/MD`** | `_MT`, `_DLL` |
| *`vcruntimed.lib`* | *`vcruntime<version>d.dll`* | Biblioteka importowania bibliotek DLL dla elementu Debug vcruntime. Nie redystrybucyjny. | **`/MDd`** | `_DEBUG`, `_MT`, `_DLL` |

> [!NOTE]
> Po wystąpieniu refaktoryzacji UCRT funkcje środowisko uruchomieniowe współbieżności zostały przeniesione do elementu *`concrt140.dll`* , który został dodany do pakietu redystrybucyjnego języka C++. Ta biblioteka DLL jest wymagana dla kontenerów równoległych C++ i algorytmów, takich jak `concurrency::parallel_for` . Ponadto standardowa biblioteka języka C++ wymaga, aby ta biblioteka DLL w systemie Windows XP obsługiwała elementy pierwotne synchronizacji, ponieważ system Windows XP nie zawiera zmiennych warunku.

Kod inicjujący CRT znajduje się w jednej z kilku bibliotek, w zależności od tego, czy Biblioteka CRT jest statycznie czy dynamicznie połączona, czy natywny, zarządzany czy mieszany kod. Ten kod obsługuje uruchamianie CRT, wewnętrzne inicjowanie danych dla wątku i zakończenie. Jest on specyficzny dla używanej wersji kompilatora. Ta biblioteka jest zawsze statycznie łączona, nawet w przypadku korzystania z dynamicznie połączonych UCRT.

Ta tabela zawiera listę bibliotek, które implementują inicjalizację i zakończenie CRT.

| Biblioteka | Właściwości | Opcja | Dyrektywy preprocesora |
|--|--|--|--|
| *`libcmt.lib`* | Statycznie łączy natywne uruchomienie CRT z kodem. | **`/MT`** | `_MT` |
| *`libcmtd.lib`* | Statycznie łączy wersję debugową natywnego uruchamiania CRT. Nie redystrybucyjny. | **`/MTd`** | `_DEBUG`, `_MT` |
| *`msvcrt.lib`* | Biblioteka statyczna dla natywnego uruchamiania CRT do użytku z bibliotekami DLL UCRT i vcruntime. | **`/MD`** | `_MT`, `_DLL` |
| *`msvcrtd.lib`* | Biblioteka statyczna dla wersji debugowania natywnego uruchamiania CRT do użytku z bibliotekami DLL UCRT i vcruntime. Nie redystrybucyjny. | **`/MDd`** | `_DEBUG`, `_MT`, `_DLL` |
| *`msvcmrt.lib`* | Biblioteka statyczna natywnego i zarządzanego rozruchowego CRT do użycia z biblioteką DLL UCRT i vcruntime. | **`/clr`** |  |
| *`msvcmrtd.lib`* | Biblioteka statyczna dla wersji debugowania natywnego i zarządzanego rozruchowego CRT do użycia z biblioteką DLL UCRT i vcruntime. Nie redystrybucyjny. | **`/clr`** |  |
| *`msvcurt.lib`* | **Przestarzałe** Biblioteka statyczna dla czystej zarządzanej CRT. | **`/clr:pure`** |  |
| *`msvcurtd.lib`* | **Przestarzałe** Biblioteka statyczna dla wersji debugowania czystego zarządzanego CRT. Nie redystrybucyjny. | **`/clr:pure`** |  |

Jeśli połączysz program z wiersza polecenia bez opcji kompilatora, która określa bibliotekę wykonawczą C, konsolidator będzie używać statycznie połączonych bibliotek CRT: *`libcmt.lib`* , *`libvcruntime.lib`* i *`libucrt.lib`* .

Użycie statycznie połączonej klasy CRT oznacza, że wszelkie informacje o stanie zapisane przez bibliotekę środowiska uruchomieniowego języka C będą lokalne dla tego wystąpienia CRT. Na przykład jeśli używasz [`strtok`](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) przy użyciu statycznie połączonej CRT, pozycja `strtok` analizatora nie jest powiązana ze `strtok` stanem użytym w kodzie w tym samym procesie (ale w innej bibliotece DLL lub exe), który jest połączony z innym wystąpieniem statycznej CRT. W przeciwieństwie do dynamicznego połączonego elementu CRT stan dla całego kodu w ramach procesu, który jest dynamicznie połączony z CRT. Ten problem nie dotyczy, jeśli są używane nowe, bezpieczniejsze wersje tych funkcji; na przykład nie `strtok_s` ma tego problemu.

Ponieważ biblioteka DLL utworzona przez połączenie ze statyczną CRT ma swój własny stan CRT, nie zaleca się łączenia statycznie z CRT w bibliotece DLL, chyba że konsekwencje tego działania są odpowiednie i zrozumiałe. Na przykład w przypadku wywołania [`_set_se_translator`](../c-runtime-library/reference/set-se-translator.md) w pliku wykonywalnym, który ładuje bibliotekę DLL połączonej ze statyczną metodą CRT, wszelkie wyjątki sprzętowe wygenerowane przez kod w bibliotece DLL nie zostaną przechwycone przez translator, ale zostaną przechwycone wyjątki sprzętowe generowane przez kod w głównym pliku wykonywalnym.

Jeśli używasz **`/clr`** przełącznika kompilatora, kod zostanie połączony z biblioteką statyczną msvcmrt. lib. Biblioteka statyczna zapewnia serwer proxy między kodem zarządzanym i natywną CRT. Nie można użyć statycznie połączonej CRT ( **`/MT`** lub **`/MTd`** opcji) z **`/clr`** . Zamiast tego użyj dynamicznie połączonych bibliotek ( **`/MD`** lub **`/MDd`** ). Czyste zarządzane biblioteki CRT są przestarzałe w programie Visual Studio 2015 i nie są obsługiwane w programie Visual Studio 2017.

Aby uzyskać więcej informacji na temat używania CRT z **`/clr`** , zobacz [zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md).

Aby skompilować wersję do debugowania aplikacji, [`_DEBUG`](../c-runtime-library/debug.md) należy zdefiniować flagę, a aplikacja musi być połączona z wersją Debug jednej z tych bibliotek. Aby uzyskać więcej informacji o korzystaniu z wersji debugowania plików biblioteki, zobacz [techniki debugowania CRT](/visualstudio/debugger/crt-debugging-techniques).

Ta wersja CRT nie jest w pełni zgodna ze standardem C99. W wersjach wcześniejszych niż wersja 16,8 programu Visual Studio 2019 \<tgmath.h> nagłówek nie jest obsługiwany. We wszystkich wersjach `CX_LIMITED_RANGE` `FP_CONTRACT` makra i dyrektywy pragma nie są obsługiwane. Niektóre elementy, takie jak znaczenie specyfikatorów parametrów w standardowych funkcjach we/wy, domyślnie używają starszych interpretacji. Można użyć **`/Zc`** opcji zgodności kompilatora i określić Opcje konsolidatora do kontrolowania niektórych aspektów zgodności biblioteki.

## <a name="c-standard-library"></a>Standardowa biblioteka C++

| Standardowa biblioteka C++ | Właściwości | Opcja | Dyrektywy preprocesora |
|--|--|--|--|
| *`libcpmt.lib`* | Wielowątkowe, statyczne łącze | **`/MT`** | `_MT` |
| *`msvcprt.lib`* | Wielowątkowy, dynamiczny link (Biblioteka importowana dla *`msvcp<version>.dll`* ) | **`/MD`** | `_MT`, `_DLL` |
| *`libcpmtd.lib`* | Wielowątkowe, statyczne łącze | **`/MTd`** | `_DEBUG`, `_MT` |
| *`msvcprtd.lib`* | Wielowątkowy, dynamiczny link (Biblioteka importowana dla *`msvcp<version>d.dll`* ) | **`/MDd`** | `_DEBUG`, `_MT`, `_DLL` |

Podczas kompilowania wersji wydania projektu, jedna z podstawowych bibliotek środowiska uruchomieniowego C ( *`libcmt.lib`* , *`msvcmrt.lib`* , *`msvcrt.lib`* ) jest domyślnie łączona, w zależności od wybranej opcji kompilatora (wielowątkowy, DLL, **`/clr`** ). Jeśli dołączysz jeden z [plików nagłówkowych standardowej biblioteki języka c++](../standard-library/cpp-standard-library-header-files.md) w kodzie, standardowa biblioteka języka c++ zostanie automatycznie połączona przez Visual C++ w czasie kompilacji. Na przykład:

```cpp
#include <ios>
```

W przypadku zgodności binarnej można określić więcej niż jeden plik DLL za pomocą pojedynczej biblioteki importu. Aktualizacje wersji mogą wprowadzać *biblioteki mozaikowe*, osobne biblioteki DLL, które wprowadzają nowe funkcje biblioteki. Na przykład program Visual Studio 2017 w wersji 15,6 wprowadzono *`msvcp140_1.dll`* do obsługi dodatkowych funkcji biblioteki standardowej bez przerywania ABI obsługiwanego przez program *`msvcp140.dll`* . *`msvcprt.lib`* Biblioteka importowana dołączona do zestawu narzędzi dla programu Visual Studio 2017 w wersji 15,6 obsługuje obie biblioteki DLL, a VCRedist dla tej wersji instaluje obie biblioteki DLL. Po wysłaniu Biblioteka z kropką ma stały ABI i nigdy nie będzie miała zależności od nowszej biblioteki kropek.

## <a name="what-problems-exist-if-an-application-uses-more-than-one-crt-version"></a>Jakie problemy występują, jeśli aplikacja używa więcej niż jednej wersji CRT?

Każdy obraz wykonywalny (EXE lub DLL) może mieć własny statycznie połączony CRT lub może dynamicznie łączyć się z CRT. Wersja CRT statycznie dołączona do lub dynamicznie załadowana przez określony obraz zależy od wersji narzędzi i bibliotek, z którymi została skompilowana. Pojedynczy proces może ładować wiele obrazów EXE i DLL, z których każdy ma własną CRT. Każdy z tych CRTs może używać innego alokatora, może mieć różne układy wewnętrznej struktury i może korzystać z różnych rozwiązań magazynu. Oznacza to, że przydzieloną pamięć, zasoby CRT lub klasy przenoszone przez granicę biblioteki DLL mogą spowodować problemy związane z zarządzaniem pamięcią, wewnętrznym użyciem statycznym lub interpretacją układu. Na przykład, jeśli klasa jest przydzielone w jednej bibliotece DLL, ale jest ona przenoszona do i usuwana przez inny, który jest używany do dealokacji CRT? Przyczyną błędów mogą być przedziały od delikatnych do natychmiastowego poziomu krytycznego, dlatego nie zaleca się bezpośredniego transferu takich zasobów.

Można uniknąć wielu z tych problemów, korzystając z technologii interfejsu binarnego aplikacji (ABI), ponieważ zostały one zaprojektowane jako stabilne i w wersji. Zaprojektuj interfejsy eksportu biblioteki DLL w celu przekazania informacji przez wartość lub do pracy z pamięcią, która została przekazana przez obiekt wywołujący, zamiast przydzielonej lokalnie i zwróconej do obiektu wywołującego. Używaj technik organizowania do kopiowania danych strukturalnych między obrazami wykonywalnymi. Hermetyzowaj zasoby lokalnie i Zezwalaj na manipulowanie nimi tylko za poorednictwem dojść lub funkcji udostępnianych klientom.

Istnieje również możliwość uniknięcia niektórych z tych problemów, jeśli wszystkie obrazy w procesie używają tej samej dynamicznie załadowanej wersji CRT. Aby upewnić się, że wszystkie składniki korzystają z tej samej wersji biblioteki DLL, skompiluj je przy użyciu **`/MD`** opcji i Użyj tego samego zestawu narzędzi kompilatora i ustawień właściwości.

Należy zachować ostrożność, jeśli program przekaże pewne zasoby CRT między granicami DLL. Takie zasoby, jak dojścia do plików, ustawienia regionalne i zmienne środowiskowe, mogą spowodować problemy, nawet w przypadku korzystania z tej samej wersji CRT. Aby uzyskać więcej informacji o problemach i sposobach ich rozwiązywania, zobacz [potencjalne błędy przekazywania obiektów CRT między granicami bibliotek DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja biblioteki środowiska uruchomieniowego języka C](../c-runtime-library/c-run-time-library-reference.md)
