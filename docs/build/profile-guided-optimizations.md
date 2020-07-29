---
title: Optymalizacje sterowane profilem
ms.date: 04/23/2019
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
ms.openlocfilehash: efa4c35810f6272b89ff11cd1c890a7f535cfc1c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232732"
---
# <a name="profile-guided-optimizations"></a>Optymalizacje sterowane profilem

Optymalizacja oparta na profilach (PGO) pozwala zoptymalizować cały plik wykonywalny, gdzie Optymalizator używa danych z przebiegów testowych pliku exe lub dll. Dane przedstawiają możliwą wydajność programu w środowisku produkcyjnym.

Optymalizacje oparte na profilach są dostępne tylko dla natywnych obiektów docelowych x86 i x64. Optymalizacje oparte na profilach nie są dostępne dla plików wykonywalnych, które są uruchamiane w środowisku uruchomieniowym języka wspólnego. Nawet w przypadku tworzenia zestawu z mieszanym kodem natywnym i zarządzanym (przy użyciu opcji kompilatora **/CLR** ) nie można używać optymalizacji profilowanej tylko w kodzie natywnym. Jeśli podjęto próbę skompilowania projektu z tymi opcjami ustawionymi w środowisku IDE, pojawią się błędy kompilacji.

> [!NOTE]
> Informacje zbierane z przebiegów testów profilowania zastępują optymalizacje, które w przeciwnym razie będą obowiązywać w przypadku określenia **/ob**, **/OS**lub **/OT**. Aby uzyskać więcej informacji, zobacz [/ob (rozszerzenie funkcji wbudowanej)](reference/ob-inline-function-expansion.md) i [/OS,/OT (Preferuj mały kod, Preferuj szybki kod)](reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Kroki optymalizacji aplikacji

Aby skorzystać z optymalizacji profilowanej, wykonaj następujące kroki, aby zoptymalizować aplikację:

- Kompiluj jeden lub więcej plików kodu źródłowego za pomocą [/GL](reference/gl-whole-program-optimization.md).

   Każdy moduł skompilowany za pomocą **/GL** można sprawdzić podczas przebiegu testu optymalizacji z obsługą profilu, aby przechwycić zachowanie w czasie wykonywania. Każdy moduł kompilacji z optymalizacją z przewodnikiem nie musi być kompilowany przy użyciu **/GL**. Jednak tylko te moduły skompilowane za pomocą **/GL** są Instrumentacją i później dostępne dla optymalizacji z przewodnikiem.

- Link przy użyciu [/LTCG](reference/ltcg-link-time-code-generation.md) i [/GENPROFILE lub/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).

   Użycie zarówno **/LTCG** , jak i **/GENPROFILE** lub **/FASTGENPROFILE** tworzy `.pgd` plik, gdy aplikacja Instrumentacja jest uruchamiana. Po dodaniu danych do pliku Test-Run `.pgd` może być używany jako dane wejściowe do następnego kroku linku (Tworzenie zoptymalizowanego obrazu). Podczas określania **/GENPROFILE**można opcjonalnie dodać argumentu **PGD =**_filename_ , aby określić niedomyślną nazwę lub lokalizację `.pgd` pliku. Kombinacja opcji **/LTCG** i **/GENPROFILE** lub **/FASTGENPROFILE** konsolidatora zastępuje przestarzałą opcję konsolidatora **/LTCG: PGINSTRUMENT** .

- Wykonaj profilowanie aplikacji.

   Za każdym razem, gdy zostanie zakończona sesja pliku EXE lub profilowana Biblioteka DLL zostaje zwolniona, `appname!N.pgc` tworzony jest plik. `.pgc`Plik zawiera informacje o konkretnym przebiegu testu aplikacji. *nazwa_aplikacji* to nazwa aplikacji, a *N* to liczba, która rozpoczyna się od 1, która jest zwiększana na podstawie liczby innych `appname!N.pgc` plików w katalogu. Można usunąć plik, `.pgc` Jeśli przebieg testowy nie reprezentuje scenariusza, który ma zostać zoptymalizowany.

   W trakcie przebiegu testowego można wymusić zamknięcie aktualnie otwartego `.pgc` pliku i utworzenie nowego `.pgc` pliku za pomocą narzędzia [pgosweep](pgosweep.md) (na przykład gdy koniec scenariusza testowego nie pokrywa się z zamknięciem aplikacji).

   Aplikacja może również bezpośrednio wywołać funkcję PGO, [PgoAutoSweep](pgoautosweep.md), aby przechwytywać dane profilu w punkcie wywołania jako `.pgc` plik. Może to dać dokładniejszą kontrolę nad kodem pokrytym przez przechwycone dane w `.pgc` plikach. Przykład korzystania z tej funkcji można znaleźć w dokumentacji [PgoAutoSweep](pgoautosweep.md) .

   Podczas tworzenia kompilacji z instrumentacją domyślnie zbieranie danych odbywa się w trybie niebezpiecznym dla wątków, co jest szybsze, ale może być nieprecyzyjne. Używając **dokładnego** argumentu do **/GENPROFILE** lub **/FASTGENPROFILE**, można określić zbieranie danych w trybie bezpiecznym dla wątków, co jest bardziej precyzyjne, ale wolniejsze. Ta opcja jest również dostępna w przypadku ustawienia przestarzałej zmiennej środowiskowej [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode) lub przestarzałej opcji konsolidatora **/POGOSAFEMODE** podczas tworzenia kompilacji z instrumentacją.

- Link przy użyciu **/LTCG** i **/USEPROFILE**.

   Użyj opcji konsolidatora **/LTCG** i [/USEPROFILE](reference/useprofile.md) w celu utworzenia zoptymalizowanego obrazu. Ten krok przyjmuje jako plik wejściowy `.pgd` . Po określeniu **/USEPROFILE**można opcjonalnie dodać argumentu **PGD =**_filename_ , aby określić niedomyślną nazwę lub lokalizację `.pgd` pliku. Można również określić tę nazwę przy użyciu przestarzałej opcji konsolidatora **/PGD** . Kombinacja **/LTCG** i **/USEPROFILE** zastępuje przestarzałe Opcje konsolidatora **/LTCG: PGOPTIMIZE** i **/LTCG: PGUPDATE** .

Można nawet utworzyć zoptymalizowany plik wykonywalny i później określić, że dodatkowe profilowanie byłoby przydatne do tworzenia bardziej zoptymalizowanego obrazu. Jeśli obraz z instrumentacją i jego `.pgd` plik są dostępne, można wykonać dodatkowe przebiegi testowe i skompilować zoptymalizowany obraz przy użyciu nowszego `.pgd` pliku, używając tych samych opcji konsolidatora **/LTCG** i **/USEPROFILE** .

> [!NOTE]
> Oba `.pgc` `.pgd` pliki są typami plików binarnych. Jeśli jest przechowywany w systemie kontroli źródła, należy unikać żadnego automatycznego przekształcenia, które może zostać wykonane w plikach tekstowych.

## <a name="optimizations-performed-by-pgo"></a>Optymalizacje wykonywane przez PGO

Optymalizacje oparte na profilach obejmują następujące testy i ulepszenia:

- **Dekreślenie** — na przykład, jeśli funkcja a często wywołuje funkcję b, a funkcja b jest stosunkowo mała, a następnie Optymalizacja oparta na profilach jest wbudowana funkcja b w funkcji a.

- **Spekulacja wywołania wirtualnego** — w przypadku wywołania wirtualnego lub innych wywołań przez wskaźnik funkcji, często przeznaczonych dla pewnej funkcji, optymalizacja oparta na profilach może wstawić warunkowo wykonywane bezpośrednie wywołanie do często stosowanej funkcji, a bezpośrednie wywołanie może być wbudowane.

- **Rejestrowanie optymalizacji alokacji** na podstawie danych profilowych skutkuje lepszą alokacją rejestru.

- **Optymalizacja bloków podstawowych** — podstawowa Optymalizacja bloków umożliwia wykonywanie często wykonanych, podstawowych bloków, które są wykonywane w ramach danej ramki, które mają być umieszczane w tym samym zestawie stron (lokalizacji lokalnej). Minimalizuje liczbę używanych stron, co minimalizuje obciążenie pamięci.

- **Optymalizacja rozmiaru/szybkości** — funkcje, w których program spędza najwięcej czasu wykonywania, można zoptymalizować pod kątem szybkości.

- **Układ funkcji** — na podstawie grafu wywołań i PROFILOWANEGO zachowania wywołującego/wywoływanego, funkcje, które mają być wzdłuż tej samej ścieżki wykonywania, są umieszczane w tej samej sekcji.

- **Optymalizacja rozgałęzienia warunkowego** — z sondami wartości, optymalizacje oparte na profilach mogą stwierdzić, czy dana wartość w instrukcji switch jest używana częściej niż inne wartości.  Następnie taką wartość można usunąć z instrukcji switch.  Tę samą opcję można wykonać za pomocą **`if`** ... instrukcje, w **`else`** których Optymalizator może zamówić **`if`** ..., **`else`** tak aby **`if`** **`else`** blok lub został umieszczony w pierwszej kolejności, w zależności od tego, który blok jest częściej prawdziwe.

- Niedziałanie **separacji kodu** — kod, który nie jest wywoływany podczas profilowania, jest przenoszony do specjalnej sekcji, która jest dołączana na końcu zestawu sekcji. Efektywnie utrzymujemy tę sekcję na często używanych stronach.

- **Separacja kodu EH** — ponieważ kod EH jest wykonywany tylko wyjątkowo, można go często przenieść do osobnej sekcji. Jest on przenoszony, gdy optymalizacje oparte na profilach mogą określić, że wyjątki występują tylko w wyjątkowych warunkach.

- Elementy **wewnętrzne pamięci** — określa, czy ma być rozszerzane wewnętrznie, czy nie, zależy od tego, czy jest on często wywoływany. Funkcję wewnętrzną można również optymalizować na podstawie rozmiaru bloku operacji przenoszenia i kopiowania.

## <a name="next-steps"></a>Następne kroki

Przeczytaj więcej na temat tych zmiennych środowiskowych, funkcji i narzędzi, których można użyć w przypadku optymalizacji z przewodnikiem:

[Zmienne środowiskowe dla optymalizacji sterowanych profilem](environment-variables-for-profile-guided-optimizations.md)<br/>
Te zmienne zostały użyte do określenia zachowania w czasie wykonywania scenariuszy testowania. Są one teraz przestarzałe i zastępowane przez nowe Opcje konsolidatora. W tym dokumencie pokazano, jak przenieść zmienne środowiskowe do opcji konsolidatora.

[PgoAutoSweep](pgoautosweep.md)<br/>
Funkcja, którą można dodać do aplikacji w celu zapewnienia precyzyjnej `.pgc` kontroli przechwytywania danych plików.

[pgosweep](pgosweep.md)<br/>
Narzędzie wiersza polecenia, które zapisuje wszystkie dane profilu do `.pgc` pliku, zamyka ten `.pgc` plik i otwiera nowy `.pgc` plik.

[pgomgr](pgomgr.md)<br/>
Narzędzie wiersza polecenia, które dodaje dane profilu z jednego lub więcej `.pgc` plików do `.pgd` pliku.

[Instrukcje: Scalanie wielu profilów PGO w jeden profil](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
Przykłady użycia **pgomgr** .

## <a name="see-also"></a>Zobacz także

[Dodatkowe narzędzia kompilacji kompilatora MSVC](reference/c-cpp-build-tools.md)
