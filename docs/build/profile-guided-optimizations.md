---
title: Optymalizacje sterowane profilem
ms.date: 04/23/2019
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
ms.openlocfilehash: 46619e77861b6a3a78d74ce6c6d9173a3a5f270f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341133"
---
# <a name="profile-guided-optimizations"></a>Optymalizacje sterowane profilem

Profilowana Optymalizacja (PGO) umożliwia optymalizowanie pliku całego pliku wykonywalnego, że optymalizator używa danych z przebiegów testowych pliku .exe lub .dll. Dane pokazują, prawdopodobnie wydajności programu w środowisku produkcyjnym.

Optymalizacje sterowane profilem są dostępne tylko dla x86 lub x64 natywnych obiektów docelowych. Optymalizacje sterowane profilem są niedostępne dla plików wykonywalnych, które są uruchamiane w środowisku uruchomieniowym języka wspólnego. Nawet w przypadku utworzenia zestawu z mieszanym kodem natywnych i zarządzanych (przy użyciu **/CLR** — opcja kompilatora), nie można używać optymalizacji sterowanej profilem na tylko do kodu macierzystego. Próba skompilowania projektu po ustawieniu tych opcji w środowisku IDE powoduje błąd kompilacji.

> [!NOTE]
> Informacje zebrane w trakcie przebiegów testowych profilowania zastępuje optymalizacje, które normalnie w efekcie w przypadku określenia **/Ob**, **/Os**, lub **/Ot**. Aby uzyskać więcej informacji, zobacz [/Ob (rozszerzenie funkcji wbudowanej)](reference/ob-inline-function-expansion.md) i [/OS, /Ot (Preferuj mały kod, Preferuj szybko kod)](reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Kroki, aby zoptymalizować aplikację

Aby używać optymalizacji sterowanej profilem, wykonaj następujące kroki, aby zoptymalizować aplikację:

- Skompiluj jeden lub więcej plików kodu źródłowego za pomocą [/GL](reference/gl-whole-program-optimization.md).

   Każdy moduł skompilowany z **/GL** może być badany w trakcie przebiegów testowych optymalizacji sterowanej profilem do przechwytywania zachowania w czasie wykonywania. Każdy moduł kompilacji optymalizacji sterowanej profilem nie muszą być kompilowane przy użyciu **/GL**. Jednak tylko moduły skompilowane z **/GL** są instrumentowane i później dostępne dla optymalizacji sterowanych profilem.

- Połącz przy użyciu [opcję/LTCG](reference/ltcg-link-time-code-generation.md) i [przełączników/genprofile i/fastgenprofile](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).

   Przy użyciu zarówno **opcję/LTCG** i **przełączników/genprofile** lub **/fastgenprofile** tworzy `.pgd` plików po uruchomieniu instrumentowanego aplikacji. Po dodaniu danych przebiegu testu do `.pgd` pliku, może służyć jako dane wejściowe do następnego kroku łączenia (tworzenie zoptymalizowanego obrazu). Podczas określania **przełączników/genprofile**, możesz opcjonalnie dodać **PGD =**_filename_ argument określający niedomyślną nazwą lub lokalizację `.pgd` pliku. Kombinacja **opcję/LTCG** i **przełączników/genprofile** lub **/fastgenprofile** opcje konsolidatora zastępuje przestarzałego **pginstrument** — Opcja konsolidatora.

- Wykonaj profilowanie aplikacji.

   Kończy się profilowana sesja pliku EXE w każdym lub profilowana Biblioteka DLL jest zwalniana, `appname!N.pgc` zostanie utworzony plik. A `.pgc` plik zawiera informacje o konkretnym przebiegu testowym aplikacji. *AppName* to nazwa aplikacji, a *N* jest liczba począwszy od 1, która jest zwiększany na podstawie liczby innych `appname!N.pgc` pliki w katalogu. Możesz usunąć `.pgc` plik, jeśli przebieg testu nie reprezentuje scenariusza, którą chcesz zoptymalizować.

   Podczas przebiegu testu, możesz wymusić zamknięcie aktualnie otwartego `.pgc` plików i utworzenia nowego `.pgc` plik z [pgosweep](pgosweep.md) utility (na przykład gdy koniec scenariusza testu nie jest zgodna z aplikacją zamykanie).

   Aplikację można także bezpośrednio wywołać funkcją PGO [PgoAutoSweep](pgoautosweep.md), aby przechwycić dane profilu punkcie wywołanie jako `.pgc` pliku. Oferuje bardziej precyzyjną kontrolę nad kodu objętych przechwyconych danych w Twojej `.pgc` plików. Na przykład jak używać tej funkcji, zobacz [PgoAutoSweep](pgoautosweep.md) dokumentacji.

   Podczas tworzenia kompilacji instrumentowanej, domyślnie, zbieranie danych odbywa się w trybie bez wątkowo, który jest szybszy, ale może być niedokładna. Za pomocą **EXACT** argument **przełączników/genprofile** lub **/fastgenprofile**, zbieranie danych można określić w trybie wątkowo, co jest bardziej precyzyjne, ale wolniej. Ta opcja jest również dostępna, jeśli ustawisz przestarzałego [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode) zmiennej środowiskowej lub przestarzałego **/POGOSAFEMODE** — opcja konsolidatora, tworząc kompilację instrumentowaną.

- Połącz przy użyciu **opcję/LTCG** i **/USEPROFILE**.

   Korzystanie z obu **opcję/LTCG** i [/USEPROFILE](reference/useprofile.md) opcje konsolidatora do utworzenia zoptymalizowanego obrazu. Ten krok zajmuje jako danych wejściowych `.pgd` pliku. Po określeniu **/USEPROFILE**, możesz opcjonalnie dodać **PGD =**_filename_ argumentu, aby określić inne niż domyślne nazwy bądź lokalizację dla `.pgd` pliku. Można również określić tę nazwę, za pomocą przestarzałego **/PGD** — opcja konsolidatora. Kombinacja **opcję/LTCG** i **/USEPROFILE** zastępuje przestarzałego **/LTCG:PGOPTIMIZE** i **/LTCG:PGUPDATE** opcje konsolidatora.

Użytkownik może nawet utworzyć zoptymalizowany plik wykonywalny, a następnie stwierdzić, że się dodatkowe profilowanie przydatne w celu utworzenia bardziej zoptymalizowanego obrazu. Jeśli instrumentowany obraz i jego `.pgd` plików są dostępne, można wykonać dodatkowe przebiegi testowe i ponownie skompilować zoptymalizowany obraz przy użyciu nowszego `.pgd` plik, korzystając z tych samych **opcję/LTCG** i **/USEPROFILE** opcje konsolidatora.

## <a name="optimizations-performed-by-pgo"></a>Optymalizacje wykonywane przez PGO

Optymalizacje sterowane profilem obejmują te testy i ulepszenia:

- **Wbudowanie** — na przykład, jeśli funkcja A często wywołuję funkcję B, a funkcja B jest stosunkowo mały, a następnie sterowane profilem wbudują funkcję optymalizacji B do funkcji A.

- **Spekulacja wywołania wirtualnego** — Jeśli wywołanie wirtualne lub inne wywołanie za pomocą wskaźnika funkcji jest często jest przeznaczony dla niektórych funkcji, optymalizacji sterowanej profilem może wstawić wykonanych warunkowo bezpośrednie wywołanie funkcji często docelowych, a bezpośrednie wywołanie może być śródwierszowa.

- **Alokacja rejestru** — Optymalizacja oparte na danych profilu powoduje lepsze przydzielanie rejestru.

- **Optymalizacja podstawowego bloku** — Optymalizacja podstawowego bloku pozwala często wykonywane podstawowe bloki, które są przejściowo wykonywane w podanej ramce można umieścić w tym samym zestawie stron (lokalizacja). Minimalizuje liczbę używanych stron, co minimalizuje obciążenie pamięci.

- **Optymalizacja rozmiaru/prędkości** — funkcje, których program zużywa najwięcej czasu wykonywania może być zoptymalizowany pod kątem szybkości.

- **Układ funkcji** — oparte na wykresu wywołań i profilowane zachowanie wywołujący/wywoływany funkcje, które przeważnie mają taką samą ścieżkę wykonywania są umieszczane w tej samej sekcji.

- **Warunkowa Optymalizacja rozgałęzień** — wykorzystując sondy wartości profilowanej optymalizacji można znaleźć, jeśli danej wartości w instrukcji switch jest używana częściej niż inne wartości.  Następnie taką wartość można usunąć z instrukcji switch.  Taka sama może odbywać się przy użyciu `if`... `else` instrukcje, w którym Optymalizator może zamówić łączność obejmującą `if`... `else` więc dowolna `if` lub `else` będzie umieszczał, zależności od tego, który blok więcej często jest wartość PRAWDA.

- **Separacja martwego kodu** — kod, który nie jest wywoływany podczas profilowania jest przenoszony do specjalnej sekcji dołączanej na końcu zestawu sekcji. Jego wygodny sposób utrzymania tej sekcji poza często używanymi stronami.

- **Separacja kodu EH** — kod EH ponieważ tylko w wyjątkowych przypadkach jest wykonywana, często można przenieść do osobnej sekcji. Jest on przeniesiony, gdy optymalizacje sterowane profilem można określić, że wyjątki mają następować tylko w wyjątkowych warunkach.

- **Funkcje wewnętrzne pamięci** — czy rozwiń wewnętrznie, czy nie zależy od tego, czy jest często wywoływana. Funkcję wewnętrzną można również optymalizować na podstawie rozmiaru bloku operacji przenoszenia i kopiowania.

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat tych zmiennych środowiskowych, funkcje i narzędzia, których można używać w sterowanych profilem:

[Zmienne środowiskowe dla optymalizacji sterowanych profilem](environment-variables-for-profile-guided-optimizations.md)<br/>
Te zmienne były używane do określania zachowania w czasie wykonywania testowania scenariuszy. Teraz jest przestarzały i zastąpiony przez nowe opcje konsolidatora. W tym dokumencie pokazano, jak przenieść ze zmiennych środowiskowych, opcje konsolidatora.

[PgoAutoSweep](pgoautosweep.md)<br/>
Funkcję można dodać do swojej aplikacji w celu zapewnienia szczegółowych `.pgc` kontroli przechwytywania danych plików.

[pgosweep](pgosweep.md)<br/>
Narzędzie wiersza polecenia, który zapisuje wszystkie dane profilu do `.pgc` pliku i zamyka `.pgc` pliku i otwiera nową `.pgc` pliku.

[pgomgr](pgomgr.md)<br/>
Narzędzie wiersza polecenia, dodaje dane profilu z co najmniej jeden `.pgc` plików `.pgd` pliku.

[Instrukcje: Scalanie wielu profili PGO w jeden profil](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
Przykłady **pgomgr** użycia.

## <a name="see-also"></a>Zobacz także

[Dodatkowe narzędzia kompilacji kompilatora MSVC](reference/c-cpp-build-tools.md)
