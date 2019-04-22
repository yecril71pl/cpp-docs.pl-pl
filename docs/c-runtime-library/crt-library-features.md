---
title: Biblioteka CRT — Funkcje
ms.date: 08/20/2018
f1_keywords:
- c.runtime
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
ms.openlocfilehash: b9a2691d492a277ffe0018b6e86b00cd245840ed
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767694"
---
# <a name="crt-library-features"></a>Biblioteka CRT — Funkcje

W tym temacie omówiono różne pliki .lib, wchodzące w skład biblioteki wykonawczej C, a także ich opcje kompilatora skojarzone i dyrektywy preprocesora.

## <a name="c-run-time-libraries-crt"></a>Biblioteki C-Run-Time (CRT)

Biblioteki wykonawczej języka C (CRT) jest częścią standardowej biblioteki języka C++, zawierające biblioteki standardowej ISO C99. Bibliotek języka Visual C++, które implementują CRT obsługuje tworzenie kodu natywnego, a oba mieszane kodu natywnego i zarządzanego. Wszystkie wersje CRT obsługuje programowanie wielowątkowe. Większość bibliotek obsługuje zarówno łączenia statycznego, aby połączyć bibliotekę bezpośrednio w kodzie, lub łączenia dynamicznego, aby umożliwić plików kodu Użyj wspólnej biblioteki DLL.

Począwszy od programu Visual Studio 2015, CRT ma zostały zaprojektowane od nowa do nowych danych binarnych. Universal CRT (UCRT) zawiera funkcje i zmienne globalne wyeksportowany przez standardowa biblioteka C99 CRT. UCRT jest teraz składnika Windows i jest dostarczany jako część systemu Windows 10. Biblioteka statyczna, biblioteki importowanej biblioteki DLL i pliki nagłówkowe dla UCRT, teraz znajdują się w zestawie SDK systemu Windows 10. Po zainstalowaniu programu Visual C++, Instalator programu Visual Studio instaluje podzbiór musieli używać UCRT SDK systemu Windows 10. UCRT można użyć w dowolnej wersji systemu Windows, obsługiwane przez program Visual Studio 2015 i nowszych wersjach. Można redystrybuować go za pomocą programu vcredist dla obsługiwanych wersji systemu Windows innych niż Windows 10. Aby uzyskać więcej informacji, zobacz [Redistributing Visual C++ Files](../windows/redistributing-visual-cpp-files.md).

Poniższa tabela zawiera listę bibliotek, które implementują UCRT.

|Biblioteka|Associated DLL|Właściwości|Opcja|Dyrektywy preprocesora|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libucrt.lib|Brak|Statycznie łączy UCRT w kodzie.|**/MT**|_MT|
|libucrtd.lib|Brak|Debuguj wersję UCRT dla łączenia statycznego. Nie do dystrybucji.|**/MTd**|_DEBUG, _MT|
|ucrt.lib|ucrtbase.dll|Importuj biblioteki DLL UCRT.|**/MD**|_MT, _DLL|
|ucrtd.lib|ucrtbased.dll|Biblioteki DLL Importuj biblioteki dla wersji 140_xp Biblioteka UCRT debugowania. Nie do dystrybucji.|**/MDd**|_DEBUG, _MT, _DLL|

Biblioteka vcruntime zawiera kod specyficzne dla implementacji Visual C++ CRT, takich jak wyjątek, obsługi i pomocy technicznej, testy środowiska uruchomieniowego i informacje o typie, szczegóły implementacji i niektórych funkcji rozszerzonej biblioteki debugowania. Wersja kompilatora używane dotyczy tej biblioteki.

Poniższa tabela zawiera listę bibliotek, które implementują biblioteki vcruntime.

|Biblioteka|Associated DLL|Właściwości|Opcja|Dyrektywy preprocesora|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libvcruntime.lib|Brak|Statycznie połączone w kodzie.|**/MT**|_MT|
|libvcruntimed.lib|Brak|W wersji do debugowania dla łączenia statycznego. Nie do dystrybucji.|**/MTd**|_MT, _DEBUG|
|vcruntime.lib|vcruntime\<version>.dll|Importuj biblioteki DLL vcruntime.|**/MD**|_MT, _DLL|
|vcruntimed.lib|vcruntime\<version>d.dll|Importuj biblioteki DLL vcruntime debugowania. Nie do dystrybucji.|**/MDd**|_DEBUG, _MT, _DLL|

> [!NOTE]
> Podczas refaktoryzacji UCRT wystąpienia funkcji środowiska uruchomieniowego współbieżności zostało przeniesionych do concrt140.dll, który został dodany do pakietu redystrybucyjnego języka C++. Ta biblioteka DLL jest wymagany dla kontenerów równoległych C++ i algorytmy, takie jak `concurrency::parallel_for`. Oprócz standardowej biblioteki C++ wymaga tej biblioteki DLL w systemie Windows XP do obsługi podstawowych synchronizacji, ponieważ Windows XP nie ma zmiennych warunków.

Kod, który inicjuje CRT ma jeden z kilku bibliotek, na podstawie informacji o tego, czy biblioteka CRT statycznie lub dynamicznie połączone, lub natywnego, zarządzanego lub mieszanym kodu. Ten kod obsługuje uruchamianie CRT, wątek wewnętrznych danych inicjowanie i kończenie działania. Odnosi się do wersji kompilatora używane. Ta biblioteka jest zawsze połączone statycznie, nawet w przypadku używania UCRT połączone dynamicznie.

Poniższa tabela zawiera listę bibliotek, które implementują CRT, inicjowanie i kończenie działania.

|Biblioteka|Właściwości|Opcja|Dyrektywy preprocesora|
|-------------|---------------------|------------|-----------------------------|
|libcmt.lib|Statycznie łączy natywnych uruchamiania CRT w kodzie.|**/MT**|_MT|
|libcmtd.lib|Statycznie łączy wersję debugowania natywnych uruchamiania CRT. Nie do dystrybucji.|**/MTd**|_DEBUG, _MT|
|msvcrt.lib|Natywne uruchamianie CRT do użytku z biblioteki DLL UCRT i vcruntime biblioteki statycznej.|**/MD**|_MT, _DLL|
|msvcrtd.lib|Wersja do debugowania natywnych uruchamiania CRT do użytku z biblioteki DLL UCRT i vcruntime biblioteki statycznej. Nie do dystrybucji.|**/MDd**|_DEBUG, _MT, _DLL|
|msvcmrt.lib|Biblioteka statyczna mieszane początkowa CRT natywnego i zarządzanego do użycia z biblioteki DLL UCRT i vcruntime.|**/clr**||
|msvcmrtd.lib|Wersja do debugowania mieszane uruchamiania CRT natywnego i zarządzanego do użycia z UCRT biblioteki DLL i vcruntime biblioteki statycznej. Nie do dystrybucji.|**/clr**||
|msvcurt.lib|**Przestarzałe** biblioteki statycznej czystych zarządzanego CRT.|**/ CLR: pure**||
|msvcurtd.lib|**Przestarzałe** biblioteki statycznej wersji debugowania czystych zarządzanego CRT. Nie do dystrybucji.|**/ CLR: pure**||

Jeśli łączysz się programu, w wierszu polecenia bez opcji kompilatora, który określa bibliotekę uruchomieniową C, konsolidator użyje statycznie łączonych bibliotek CRT: libcmt.lib, libvcruntime.lib i libucrt.lib.

Za pomocą statycznie łączonych CRT oznacza wszelkich informacji o stanie zapisane przez Biblioteka uruchomieniowa C będzie lokalnych do tego wystąpienia CRT. Na przykład, jeśli używasz [strtok —, _strtok_l —, wcstok —, _wcstok_l —, _mbstok —, _mbstok_l —](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) podczas korzystania ze statycznie łączonych CRT, pozycja `strtok` analizatora nie jest powiązana z `strtok` stanu użytą w kodzie, w tym samym procesie (ale inne biblioteki DLL lub EXE) połączony do innego wystąpienia statycznego CRT. Z kolei CRT połączone dynamicznie udostępnia stanu dla całego kodu w ramach procesu, która jest połączona dynamicznie do CRT. Ten problem nie ma zastosowania, jeśli używasz nowego bardziej bezpieczne wersje tych funkcji; na przykład `strtok_s` ten problem nie występuje.

Ponieważ biblioteki DLL utworzonych przez łączenie statyczne CRT będzie miał stanu CRT, nie zaleca się dołączana statycznie do CRT w bibliotece DLL, chyba że konsekwencje tego są specjalnie żądanego i zrozumienie. Na przykład, jeśli wywołasz [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) w pliku wykonywalnego, który ładuje bibliotekę DLL, połączyć własne statyczne CRT, wszystkie wyjątki sprzętowe wygenerowane przez kod w pliku DLL nie zostanie przechwycony przez translator, ale wyjątki sprzętowe wygenerowane przez kod w głównym pliku wykonywalnego, który zostanie przechwycony.

Jeśli używasz **/CLR** przełącznika kompilatora Twój kod będzie połączony z biblioteki statycznej, msvcmrt.lib. Biblioteka statyczna zawiera serwer proxy między kodu zarządzanego i natywnego CRT. Nie można używać statycznie łączonych CRT ( **/MT** lub **/mtd** opcje) za pomocą **/CLR**. Korzystanie z bibliotek dołączanych dynamicznie (**/MD** lub **/mdd**) zamiast tego. Czysty zarządzane biblioteki CRT są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Aby uzyskać więcej informacji na temat korzystania z CRT z **/CLR**, zobacz [zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md).

Tworzenie wersji debugowania aplikacji [_DEBUG](../c-runtime-library/debug.md) flagi, które muszą być zdefiniowane i aplikacja muszą być połączone z wersji debugowania jednego z tych bibliotek. Aby uzyskać więcej informacji na temat korzystania z wersji debugowania plików biblioteki zobacz [techniki testowania CRT](/visualstudio/debugger/crt-debugging-techniques).

Ta wersja CRT nie jest w pełni zgodna ze standardem C99. W szczególności \<tgmath.h > nagłówka i makra pragma CX_LIMITED_RANGE/FP_CONTRACT nie są obsługiwane. Domyślnie niektóre elementy, takie jak znaczenie parametru specyfikatory standardowych funkcji we/wy używają starsze interpretacji. Możesz użyć /Zc — opcje zgodności kompilatora i określ opcje konsolidatora, aby kontrolować niektóre aspekty zgodność biblioteki

## <a name="c-standard-library"></a>Standardowa biblioteka C++

|Standardowa biblioteka C++|Właściwości|Opcja|Dyrektywy preprocesora|
|----------------------------|---------------------|------------|-----------------------------|
|libcpmt.lib|Wielowątkowe, statyczne łącze|**/MT**|_MT|
|msvcprt.lib|Link wielowątkowych i dynamiczne (Importuj biblioteki MSVCP*wersji*.dll)|**/MD**|_MT, _DLL|
|libcpmtd.lib|Wielowątkowe, statyczne łącze|**/MTd**|_DEBUG, _MT|
|msvcprtd.lib|Link wielowątkowych i dynamiczne (Importuj biblioteki MSVCP*wersji*D.DLL)|**/MDd**|_DEBUG, _MT, _DLL|

W przypadku tworzenia wersji projektu, jedną z podstawowych biblioteki wykonawczej języka C (libcmt.lib msvcmrt.lib, msvcrt.lib) jest domyślnie połączony, w zależności od opcji kompilatora, możesz wybrać (wielowątkowe, DLL i/CLR). Po wstawieniu z [pliki nagłówkowe standardowej biblioteki języka C++](../standard-library/cpp-standard-library-header-files.md) w swoim kodzie standardowej biblioteki języka C++ zostaną połączone w automatycznie przez Visual C++ w czasie kompilacji. Na przykład:

```cpp
#include <ios>
```

W celu zapewnienia zgodności z binarne więcej niż jeden plik DLL może być określone przez bibliotekę importu jednego. Wersja aktualizacji może powodować *dot bibliotek*, oddzielnych bibliotek DLL, które wprowadzają nowe funkcje biblioteki. Na przykład program Visual Studio 2017 w wersji 15.6 wprowadzono msvcp140_1.dll na potrzeby obsługi dodatkowe biblioteki standardowej funkcji bez przerywania ABI obsługiwane przez msvcp140.dll. Biblioteka importowana msvcprt.lib, które są zawarte w zestawie narzędzi programu Visual Studio 2017 w wersji 15.6 obsługuje zarówno bibliotek DLL i vcredist dla tej wersji instaluje zarówno biblioteki dll. Po się bibliotekę z dot ma stały ABI i nigdy nie będzie mieć zależność na nowsze biblioteki kropka.

## <a name="what-problems-exist-if-an-application-uses-more-than-one-crt-version"></a>Jakie problemy istnieje, jeśli aplikacja używa więcej niż jedna wersja CRT?

Każdy obraz wykonywalny (EXE lub DLL) może mieć własną CRT statycznie połączone lub dynamicznie połączyć CRT. Wersja CRT objęte statycznie lub dynamicznie ładowany przez określonego obrazu, zależy od wersji narzędzi i bibliotek, który został utworzony z. Jeden proces może spowodować załadowanie obrazów wiele plików Wykonywalnych i bibliotek DLL, każdy z własną CRT. Każda z tych im monitory CRT może używać różnych alokatora, mogą mieć różnych wewnętrznej struktury układy i może używać uzgodnienia innego magazynu. Oznacza to, że przydzielonej pamięci, CRT zasobów lub klasy przekazywane granicę DLL może spowodować problemy, zarządzanie pamięcią, wewnętrznego użycia statycznego lub interpretacji układu. Na przykład jeśli klasa jest przydzielane w jedną bibliotekę DLL, ale przekazany do, usunięty przez innego które CRT, program wycofujący przydzielenia jest używany? Błędy spowodowane mogą należeć do zakresu od subtelne można od razu krytyczny i w związku z tym bezpośrednie, przeniesienie tych zasobów jest zdecydowanie odradzane.

Wiele z tych problemów można uniknąć przy użyciu technologii binarnym interfejsem aplikacji (ABI) zamiast tego, ponieważ są one przeznaczone stabilny i obsługą wersji. Projektowanie interfejsów eksportu biblioteki DLL do przekazywania informacji przez wartość lub w pamięci, która jest przekazany przez wywołującego, zamiast przydzielany lokalnie i zwracane do obiektu wywołującego. Użyj technik do skopiowania danych ze strukturą między obrazy wykonywalne kierowania. Hermetyzacji zasobów lokalnie i zezwolić tylko na manipulacje za pomocą dojścia lub funkcje, które należy udostępnić klientom.

Istnieje również możliwość uniknąć niektóre z tych problemów, jeśli wszystkie obrazy w procesie używa dynamicznie załadowane tę samą wersję CRT. Aby upewnić się, że wszystkie składniki używać tej samej wersji biblioteki DLL środowiska CRT, należy utworzyć je przy użyciu **/MD** opcji, a następnie użyć tych samych narzędzi i właściwości ustawień kompilatora.

Niektóre opieki jest potrzebny, jeśli program zakończy się pomyślnie niektórych zasobów CRT (takich jak dojścia do plików i ustawień regionalnych zmienne środowiskowe) poprzek granic DLL, nawet w przypadku korzystania z tej samej wersji środowiska CRT. Więcej informacji na temat zagadnień związanych oraz sposoby ich rozwiązywania, zobacz [potencjalne błędy przekazywania CRT obiektów w pliku DLL granicach](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja biblioteki środowiska uruchomieniowego języka C](../c-runtime-library/c-run-time-library-reference.md)
