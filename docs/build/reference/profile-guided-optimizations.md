---
title: Optymalizacja sterowana profilem | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c7d6de281097232b1b8abc10a103af9c186e3550
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="profile-guided-optimizations"></a>Optymalizacje sterowane profilem

Funkcjonalność optymalizacji sterowanej profilem umożliwia optymalizowanie pliku wyjściowego w taki sposób, że optymalizator używa danych z przebiegów testowych pliku .exe lub .dll. Dane pokazują, jak program będzie prawdopodobnie działał w środowisku produkcyjnym.

Optymalizacje sterowane profilem są dostępne tylko dla celów natywnego x86 lub x64. Optymalizacje sterowane profilem nie są dostępne dla plików wyjściowych, które działają w środowisko uruchomieniowe języka wspólnego. Nawet jeśli produkuj zestawu z mieszanym kodu natywnego i zarządzanego (przy użyciu **/CLR** — opcja kompilatora), optymalizacja sterowana profilem — nie można użyć tylko kod natywny. Próba zbudować projekt z tych opcji w IDE powoduje błąd kompilacji.

> [!NOTE]
> Informacje, które są zbierane z profilowania uruchomień testów zastępuje optymalizacji, które w przeciwnym razie będą w efekcie Jeśli określisz **/Ob**, **/OS**, lub **/Ot**. Aby uzyskać więcej informacji, zobacz [/Ob (rozszerzenie funkcji wbudowanej)](../../build/reference/ob-inline-function-expansion.md) i [/OS, /Ot (Preferuj mały kod, Preferuj szybki kod)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Kroki, aby zoptymalizować aplikacji

Aby używać optymalizacji, wykonaj następujące kroki, aby zoptymalizować aplikacji:

- Kompiluj jeden lub więcej plików kodu źródłowego z [/GL](../../build/reference/gl-whole-program-optimization.md).

   Każdy moduł skompilowany z **/GL** można zbadać podczas optymalizacji sterowanych profilem uruchomień testów do przechwytywania zachowania w czasie wykonywania. Każdy moduł kompilacji Optymalizacja sterowana profilem nie musi być kompilowana przy użyciu **/GL**. Jednak tylko moduły skompilowane z **/GL** są instrumentowane i później dostępne dla optymalizacji sterowanych profilem.

- Połącz przy użyciu [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md) i [opcji/genprofile lub /FASTGENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).

   Za pomocą obu **opcję/LTCG** i **opcji/genprofile** lub **/FASTGENPROFILE** tworzy plik .pgd po uruchomieniu instrumentowanego aplikacji. Po dodaniu danych z przebiegów testowych do pliku .pgd mogą one służyć jako dane wejściowe następnego kroku łączenia (tworzenie zoptymalizowanego obrazu). Podczas określania **opcji/genprofile**, można opcjonalnie dodawać **PGD =**_filename_ argumentu, aby określić niestandardowy nazwę lub lokalizację pliku .pgd. Kombinacja **opcję/LTCG** i **opcji/genprofile** lub **/FASTGENPROFILE** opcje konsolidatora zastępuje przestarzałe **/LTCG:PGINSTRUMENT** — Opcja konsolidatora.

- Wykonaj profilowanie aplikacji.

   Każde kończenia sesji PROFILOWANEGO EXE lub PROFILOWANEGO biblioteki DLL jest zwolniony, *appname*! zostanie utworzony plik # .pgc. Plik .pgc zawiera informacje o konkretnym przebiegu testowym aplikacji. # jest liczbą, począwszy od 1, która zwiększa się na podstawie liczby innych *appname*! # .pgc plików w katalogu. Plik .pgc można usunąć, jeśli przebieg testowy nie reprezentuje scenariusza, który ma być optymalizowany.

   Podczas uruchomienia testu, można wymusić zamknięcia .pgc aktualnie otwarty plik i utworzenie nowego pliku .pgc z [pgosweep](../../build/reference/pgosweep.md) narzędzia (na przykład, gdy koniec scenariusza testu nie pokrywa się z zamykania aplikacji).

   Aplikacji można również bezpośrednio wywołać funkcji PGO [PgoAutoSweep](pgoautosweep.md), do przechwytywania danych profilu w punkcie połączenia jako plik .pgc. To pozwala bardziej precyzyjną kontrolę nad kodem objęty przez przechwycone dane w plikach .pgc. Na przykład sposobu używania tej funkcji, zobacz [PgoAutoSweep](pgoautosweep.md) dokumentacji.

   Po utworzeniu instrumentowanej kompilacji, domyślnie zbieranie danych odbywa się w trybie z systemem innym niż wątkowo, który jest szybsze, ale nie może być dokładne. Za pomocą **EXACT** argument **opcji/genprofile** lub **/FASTGENPROFILE**, można określić zbierania danych w trybie wątkowo, który jest bardziej dokładne, ale wolniej. Ta opcja jest niedostępna, jeśli przestarzałe również [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode) zmiennej środowiskowej lub przestarzałe **/POGOSAFEMODE** — opcja konsolidatora, podczas tworzenia instrumentowanej kompilacji.

- Połącz przy użyciu **opcję/LTCG** i **/USEPROFILE**.

   Korzystanie z obu **opcję/LTCG** i [/USEPROFILE](useprofile.md) opcje konsolidatora do utworzenia zoptymalizowanego obrazu. W tym kroku danymi wejściowymi jest plik .pgd. Po określeniu **/USEPROFILE**, można opcjonalnie dodawać **PGD =**_filename_ argument można określić innych niż domyślne nazwę lub lokalizację pliku .pgd. Ta nazwa można również określić, używając przestarzałe **/PGD** — opcja konsolidatora. Kombinacja **opcję/LTCG** i **/USEPROFILE** zastępuje przestarzałe **/LTCG:PGOPTIMIZE** i **/LTCG:PGUPDATE** opcje konsolidatora.

Można nawet utworzyć zoptymalizowany plik wyjściowy, a następnie stwierdzić, że przydałoby się dodatkowe profilowanie w celu utworzenia bardziej zoptymalizowanego obrazu. Jeśli obrazu z Instrumentacją i jego plik .pgd są dostępne, może nie uruchomień testów dodatkowe i ponownie zoptymalizowanego obrazu za pomocą nowszej plik .pgd, za pomocą takie same **opcję/LTCG** i **/USEPROFILE** opcje konsolidatora .

## <a name="optimizations-performed-by-pgo"></a>Optymalizacje wykonywane przez PGO

Oto lista optymalizacji sterowanych profilem:

- **Ze śródwierszowaniem** — na przykład, jeśli istnieje funkcja A czy często wywołania funkcji B i funkcja B jest stosunkowo mały, a następnie funkcja wbudowana B w funkcji A. będzie optymalizacje sterowane profilem

- **Wirtualne spekulacji wywołać** -wywołanie wirtualnych lub innych połączeń za pomocą wskaźnika funkcji jest często przeznaczony dla niektórych funkcji, optymalizacja sterowana profilem — można wstawić warunkowo wykonywane bezpośrednie wywołanie funkcji często docelowe i bezpośrednie wywołanie może być wbudowane.

- **Zarejestruj alokacji** — Optymalizowanie z wynikami danych profilu w lepsze alokacja rejestru.

- **Podstawowe optymalizacji bloku** -optymalizacji bloku podstawowego umożliwia często wykonywane podstawowych bloków, które tymczasowo wykonywane w ramach danego ramkę, która będzie umieszczona w tym samym zestawie stron (miejscowości). Zmniejsza to liczbę używanych stron, a w efekcie obciążenie pamięci.

- **Optymalizacja rozmiaru i szybkość** — funkcje, których program zużywa dużo czasu może być zoptymalizowany pod kątem szybkości.

- **Funkcja układu** — oparte na wykresu wywołań i profilowane zachowanie wywołujący/wywoływany, funkcje, które są w tej samej ścieżce wykonywania są umieszczane w tej samej sekcji.

- **Warunkowe optymalizacji gałęzi** — z sondy wartość profilowana optymalizacje można znaleźć, jeśli danej wartości w instrukcji switch służy częściej niż innych wartości.  Następnie taką wartość można usunąć z instrukcji switch.  Analogicznie można postąpić z instrukcjami if/else. Optymalizator będzie umieszczał na początku blok „if” lub „else” w zależności od tego, który z nich częściej generuje wartość „true”.

- **Martwy separacją kodu** -kod, który nie jest wywoływana podczas profilowania zostanie przeniesiony do specjalnej sekcji dołączany na końcu zestawu sekcji. To wygodny sposób utrzymania tej sekcji poza często używanymi stronami.

- **EH separacją kodu** -wyjątkowo wykonywany, kod EH często mogą zostać przeniesione do osobnej sekcji, gdy optymalizacje sterowane profilem można określić, czy wyjątki występować tylko w wyjątkowych warunków.

- **Funkcje wewnętrzne pamięci** — rozszerzenie funkcje wewnętrzne może zostać podjęta lepiej, jeśli można określić, czy wewnętrzna nazywa się często. Funkcję wewnętrzną można również optymalizować na podstawie rozmiaru bloku operacji przenoszenia i kopiowania.

Jeśli używasz programu Visual Studio 2013, można użyć automatycznego [wtyczek optymalizacji opartej na profilu](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md) w języku Visual C++ w Centrum wydajności i diagnostyki uprościć i usprawnić proces optymalizacji w programie Visual Studio. Ten dodatek nie jest dostępny w nowszych wersjach programu Visual Studio.

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat tych zmiennych środowiskowych, funkcje i narzędzia można użyć w optymalizacje sterowane profilem:

[Zmienne środowiskowe dla optymalizacji sterowanych profilem](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
Tych zmiennych można używać do określania zachowania w czasie wykonywania testowania scenariuszy. Mają one została zastąpiona nowe opcje konsolidatora; Przeczytaj, ułatwiające przenoszenie ze zmiennych środowiskowych opcji konsolidatora.

[PgoAutoSweep](pgoautosweep.md)<br/>
Funkcja, które można dodać do aplikacji w celu zapewnienia kontroli przechwytywania danych pliku .pgc szczegółowych.

[pgosweep](../../build/reference/pgosweep.md)<br/>
Narzędzie wiersza polecenia, który zapisuje wszystkie dane profilu w pliku .pgc, zamyka plik .pgc i otwiera nowy plik .pgc.

[pgomgr](../../build/reference/pgomgr.md)<br/>
Narzędzie wiersza polecenia, które dodaje danych profilu z jednego lub więcej plików .pgc do pliku .pgd.

[Porady: scalanie wielu profili PGO w jeden profil](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md) przykłady **pgomgr** użycia.

## <a name="see-also"></a>Zobacz także

[Narzędzia kompilacji C/C++](../../build/reference/c-cpp-build-tools.md)
