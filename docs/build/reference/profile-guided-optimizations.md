---
title: Optymalizacje sterowane profilem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4914b809e8e88ca07cf97af2f4d5405087cf549
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417413"
---
# <a name="profile-guided-optimizations"></a>Optymalizacje sterowane profilem

Funkcjonalność optymalizacji sterowanej profilem umożliwia optymalizowanie pliku wyjściowego w taki sposób, że optymalizator używa danych z przebiegów testowych pliku .exe lub .dll. Dane pokazują, jak program będzie prawdopodobnie działał w środowisku produkcyjnym.

Optymalizacje sterowane profilem są dostępne tylko dla x86 lub x64 natywnych obiektów docelowych. Optymalizacje sterowane profilem nie są dostępne dla plików wyjściowych, które są uruchamiane w środowisku uruchomieniowym języka wspólnego. Nawet w przypadku utworzenia zestawu z mieszanym kodem natywnych i zarządzanych (przy użyciu **/CLR** — opcja kompilatora), nie można używać optymalizacji sterowanej profilem na tylko do kodu macierzystego. Próba skompilowania projektu po ustawieniu tych opcji w środowisku IDE powoduje błąd kompilacji.

> [!NOTE]
> Informacje zebrane w trakcie przebiegów testowych profilowania zastępuje optymalizacje, które normalnie w efekcie w przypadku określenia **/Ob**, **/Os**, lub **/Ot**. Aby uzyskać więcej informacji, zobacz [/Ob (rozszerzenie funkcji wbudowanej)](../../build/reference/ob-inline-function-expansion.md) i [/OS, /Ot (Preferuj mały kod, Preferuj szybko kod)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Kroki, aby zoptymalizować aplikację

Aby używać optymalizacji sterowanej profilem, wykonaj następujące kroki, aby zoptymalizować aplikację:

- Skompiluj jeden lub więcej plików kodu źródłowego za pomocą [/GL](../../build/reference/gl-whole-program-optimization.md).

   Każdy moduł skompilowany z **/GL** może być badany w trakcie przebiegów testowych optymalizacji sterowanej profilem do przechwytywania zachowania w czasie wykonywania. Każdy moduł kompilacji optymalizacji sterowanej profilem nie musi być skompilowana przy użyciu **/GL**. Jednak tylko moduły skompilowane z **/GL** są instrumentowane i później dostępne dla optymalizacji sterowanych profilem.

- Połącz przy użyciu [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md) i [przełączników/genprofile i/fastgenprofile](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).

   Przy użyciu zarówno **opcję/LTCG** i **przełączników/genprofile** lub **/fastgenprofile** tworzy plik .pgd po uruchomieniu instrumentowanego aplikacji. Po dodaniu danych z przebiegów testowych do pliku .pgd mogą one służyć jako dane wejściowe następnego kroku łączenia (tworzenie zoptymalizowanego obrazu). Podczas określania **przełączników/genprofile**, możesz opcjonalnie dodać **PGD =**_filename_ argument określający niedomyślną nazwą lub lokalizacją pliku .pgd. Kombinacja **opcję/LTCG** i **przełączników/genprofile** lub **/fastgenprofile** opcje konsolidatora zastępuje przestarzałego **pginstrument** — Opcja konsolidatora.

- Wykonaj profilowanie aplikacji.

   Każde kończy się profilowana sesja pliku EXE lub profilowana Biblioteka DLL jest zwalniana, *appname*! # .pgc plik zostanie utworzony. Plik .pgc zawiera informacje o konkretnym przebiegu testowym aplikacji. # to numer, począwszy od 1, która jest zwiększany na podstawie liczby innych *appname*! # .PGC istniejących plików w katalogu. Plik .pgc można usunąć, jeśli przebieg testowy nie reprezentuje scenariusza, który ma być optymalizowany.

   Podczas przebiegu testu, możesz wymusić zamknięcie aktualnie otwartego pliku .pgc i utworzenie nowego pliku .pgc z [pgosweep](../../build/reference/pgosweep.md) utility (na przykład gdy koniec scenariusza testu nie pokrywa się z zamknięciem aplikacji).

   Aplikację można także bezpośrednio wywołać funkcją PGO [PgoAutoSweep](pgoautosweep.md), aby przechwycić dane profilu punkcie wywołanie jako plik .pgc. To może dać bardziej precyzyjną kontrolę nad kodu objętych przechwycone dane w plikach .pgc. Na przykład jak używać tej funkcji, zobacz [PgoAutoSweep](pgoautosweep.md) dokumentacji.

   Podczas tworzenia kompilacji instrumentowanej, domyślnie, zbieranie danych odbywa się w trybie bez wątkowo, który jest szybszy, ale nie może być dokładne. Za pomocą **EXACT** argument **przełączników/genprofile** lub **/fastgenprofile**, zbieranie danych można określić w trybie metodą o bezpiecznych wątkach, który jest bardziej precyzyjne, ale wolniej. Ta opcja jest również dostępna, jeśli ustawisz przestarzałego [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode) zmiennej środowiskowej lub przestarzałego **/POGOSAFEMODE** — opcja konsolidatora, tworząc kompilację instrumentowaną.

- Połącz przy użyciu **opcję/LTCG** i **/USEPROFILE**.

   Korzystanie z obu **opcję/LTCG** i [/USEPROFILE](useprofile.md) opcje konsolidatora do utworzenia zoptymalizowanego obrazu. W tym kroku danymi wejściowymi jest plik .pgd. Po określeniu **/USEPROFILE**, możesz opcjonalnie dodać **PGD =**_filename_ argumentu, aby określić inne niż domyślne nazwą lub lokalizacją pliku .pgd. Można również określić tę nazwę, za pomocą przestarzałego **/PGD** — opcja konsolidatora. Kombinacja **opcję/LTCG** i **/USEPROFILE** zastępuje przestarzałego **/LTCG:PGOPTIMIZE** i **/LTCG:PGUPDATE** opcje konsolidatora.

Można nawet utworzyć zoptymalizowany plik wyjściowy, a następnie stwierdzić, że przydałoby się dodatkowe profilowanie w celu utworzenia bardziej zoptymalizowanego obrazu. Jeśli instrumentowany obraz i jego plik .pgd są dostępne, możesz wykonać dodatkowe przebiegi testowe i ponownie skompilować zoptymalizowany obraz przy użyciu nowszego pliku .pgd, korzystając z tych samych **opcję/LTCG** i **/USEPROFILE** opcje konsolidatora .

## <a name="optimizations-performed-by-pgo"></a>Optymalizacje wykonywane przez PGO

Oto lista optymalizacji sterowanych profilem:

- **Wbudowanie** — na przykład, jeśli istnieje funkcja A, często wywołuję funkcję B, a funkcja B jest stosunkowo niewielka, optymalizacje sterowane profilem będzie wbudują funkcję B do funkcji A.

- **Spekulacja wywołania wirtualnego** — Jeśli wywołanie wirtualne lub inne wywołanie za pomocą wskaźnika funkcji jest często jest przeznaczony dla niektórych funkcji, optymalizacja sterowana profilem — można wstawić wykonywane warunkowo bezpośrednie wywołanie do funkcji często docelowe i bezpośrednie wywołanie może być śródwierszowa.

- **Alokacja rejestru** — Optymalizacja z profilu danych spowoduje lepszą alokacja rejestru.

- **Optymalizacja podstawowego bloku** — Optymalizacja podstawowego bloku pozwala często wykonywane podstawowe bloki, które są przejściowo wykonywane w podanej ramce można umieścić w tym samym zestawie stron (lokalizacja). Zmniejsza to liczbę używanych stron, a w efekcie obciążenie pamięci.

- **Optymalizacja rozmiaru/prędkości** — funkcje, w którym program zużywa dużo czasu może być zoptymalizowany pod kątem szybkości.

- **Układ funkcji** — oparte na wykresu wywołań i profilowane zachowanie wywołujący/wywoływany funkcje, które przeważnie mają taką samą ścieżkę wykonywania są umieszczane w tej samej sekcji.

- **Warunkowa Optymalizacja rozgałęzień** — wykorzystując sondy wartości profilowanej optymalizacji można znaleźć, jeśli danej wartości w instrukcji switch jest używana częściej niż inne wartości.  Następnie taką wartość można usunąć z instrukcji switch.  Analogicznie można postąpić z instrukcjami if/else. Optymalizator będzie umieszczał na początku blok „if” lub „else” w zależności od tego, który z nich częściej generuje wartość „true”.

- **Separacja martwego kodu** — kod, który nie jest wywoływany podczas profilowania jest przenoszony do specjalnej sekcji dołączanej na końcu zestawu sekcji. To wygodny sposób utrzymania tej sekcji poza często używanymi stronami.

- **Separacja kodu EH** — kod EH, wyjątkowo wykonywana, często można przenieść do osobnej sekcji, gdy optymalizacje sterowane profilem można określić, że wyjątki mają następować tylko w wyjątkowych warunkach.

- **Funkcje wewnętrzne pamięci** — rozszerzenie funkcji wewnętrznych można decyzję o można określić, jeśli funkcja jest często wywoływana. Funkcję wewnętrzną można również optymalizować na podstawie rozmiaru bloku operacji przenoszenia i kopiowania.

Jeśli używasz programu Visual Studio 2013, możesz użyć automatycznego [wtyczki Optymalizacja z przewodnikiem profilu](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md) dla języka Visual C++ w Centrum wydajności i diagnostyki upraszczającego i usprawniającego proces optymalizacji w programie Visual Studio. Ta wtyczka nie jest dostępne w kolejnych wersjach programu Visual Studio.

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat tych zmiennych środowiskowych, funkcje i narzędzia, których można używać w sterowanych profilem:

[Zmienne środowiskowe dla optymalizacji sterowanych profilem](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
Te zmienne mogą służyć do określania zachowania w czasie wykonywania testowania scenariuszy. One zostały zaniechane i zastąpione nowe opcje konsolidatora; Przeczytaj, które ułatwiają przejście ze zmiennych środowiskowych, opcje konsolidatora.

[PgoAutoSweep](pgoautosweep.md)<br/>
Funkcję można dodać do swojej aplikacji, aby zapewnić kontrolę przechwytywania danych pliku .pgc szczegółowych.

[pgosweep](../../build/reference/pgosweep.md)<br/>
Narzędzie wiersza polecenia, który zapisuje wszystkie dane profilu do pliku .pgc, zamyka plik .pgc i zostanie otwarty nowy plik .pgc.

[pgomgr](../../build/reference/pgomgr.md)<br/>
Narzędzie wiersza polecenia do profilu danych z co najmniej jeden plik .pgc są dodawane do pliku .pgd.

[Instrukcje: scalanie wielu profili PGO w jeden profil](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
Przykłady **pgomgr** użycia.

## <a name="see-also"></a>Zobacz także

[Narzędzia kompilacji C/C++](../../build/reference/c-cpp-build-tools.md)
