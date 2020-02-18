---
title: Narzędzia środowiska IDE programu Visual Studio C++ do uaktualniania kodu
description: Edytor C++ kodu i narzędzia do analizy kodu w programie Visual Studio ułatwiają modernizację bazy C++ kodu.
ms.date: 11/13/2019
ms.topic: conceptual
ms.openlocfilehash: 409fc0a2fa6cd39c7751dc34b20b231ffbea3956
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416153"
---
# <a name="visual-studio-ide-tools-for-upgrading-c-code"></a>Narzędzia środowiska IDE programu Visual Studio C++ do uaktualniania kodu

Program Visual Studio pomaga uaktualnić starszy C++ kod przy użyciu opcji kompilatora, ostrzeżeń analizy kodu i funkcji edytora, takich jak szybkie poprawki, szybkie informacje i udoskonalony pasek przewijania. Termin "starszy kod" odnosi się do żadnej z następujących kategorii:

- Kod, który był wcześniej dozwolony przez kompilator C++ firmy Microsoft (MSVC), ale nigdy nie jest C++ zgodny ze standardem.

   Aby uaktualnić starszy niezgodny kod MSVC, Włącz opcję kompilatora [/permissive-](../build/reference/permissive-standards-conformance.md) . Wszystkie wystąpienia niezgodnych użycia są podkreślone czerwonymi zygzakami w edytorze kodu. Komunikaty o błędach w oknie **Lista błędów** zawierają zalecenia dotyczące sposobu naprawienia błędu. Kliknij kod błędu, aby przejść do jego strony pomocy w dokumentacji. W przypadku niepraktycznego naprawienia wszystkich błędów, można uaktualnić niezgodny kod w etapach, włączając opcję **ograniczającą** , rozwiązując niektóre błędy, a następnie ponownie włączając opcję. Kod zostanie skompilowany przy użyciu nowych ulepszeń i można wrócić i naprawić pozostałe problemy w późniejszym czasie. Zobacz stronę [/permissive-](../build/reference/permissive-standards-conformance.md) , aby zapoznać się z przykładami niezgodnego kodu MSVC.

- Kod, który był dozwolony we wcześniejszej wersji standardu, C++ ale został uznany za przestarzały lub usunięty w nowszej wersji.

   Aby uaktualnić program do nowszej wersji Standard, ustaw dla opcji [ C++ standardowy język](../build/reference/std-specify-language-standard-version.md) odpowiednią wartość Standard i Usuń wszystkie zgłoszone błędy kompilacji. Ogólnie rzecz biorąc, zalecamy ustawienie standardu języka na [/std: c++ 17](../build/reference/std-specify-language-standard-version.md). Błędy wywoływane podczas uaktualniania do nowszej wersji Standard nie są związane z błędami zgłoszonymi podczas korzystania z opcji **"zależna"** .

- Kod, który jest zgodny ze wszystkimi wersjami standardu, ale nie jest już uznawany za najlepsze C++rozwiązanie w nowoczesnej.

   Aby zidentyfikować kod, w którym są zalecane zmiany, uruchom [analizę kodu](/cpp/code-quality/code-analysis-for-c-cpp-overview).

## <a name="open-and-convert-a-legacy-project"></a>Otwieranie i konwertowanie starszego projektu

Jeśli starszy projekt jest oparty na starszej wersji programu Visual Studio, można go otworzyć w programie Visual Studio 2017 lub Visual Studio 2019. Program Visual Studio automatycznie konwertuje go na bieżący schemat projektu z obsługą wszystkich najnowszych funkcji kompilatora i środowiska IDE.

![Uaktualnianie projektu](media/upgrade-dialog-v142.png "Uaktualnianie projektu")

Aby uzyskać więcej informacji, [Zobacz C++ uaktualnianie projektów ze starszych wersji programu Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md).

## <a name="search-the-code-base"></a>Przeszukaj bazę kodu

Uaktualnianie bazy kodu często polega na przeszukiwaniu wielu plików. Aby wyszukać wszystko w bazie kodu, naciśnij **klawisze Ctrl + T** , aby wyświetlić pole wyszukiwania **do wszystkich** .

![Przejdź do wszystkiego](media/go-to-all.png "Przejdź do wszystkiego")

Aby zawęzić zakres wyszukiwania, wpisz jeden z 1-literowego filtru, a następnie miejsce, a następnie wyszukiwany element.

## <a name="error-list"></a>Lista błędów

C++ Po ustawieniu żądanego standardu języka i innych opcji kompilatora ( **właściwości** > **projektu** > **Ogólne**) Naciśnij **kombinację klawiszy Ctrl + Shift + B** , aby skompilować projekt. Można oczekiwać, że niektóre błędy i ostrzeżenia są wyświetlane w postaci czerwonych zygzaków w różnych miejscach w kodzie. Błędy są również wyświetlane w **Lista błędów**. Aby uzyskać więcej informacji o konkretnym błędzie, kliknij kod błędu, aby przejść do strony pomocy w dokumentacji. Kody błędów zaczynające się od znaku "C" są błędami kompilatora. Kody zaczynające się od ciągu "MSB" to błędy programu MSBuild wskazujące problem z konfiguracją projektu.

![Błędy kompilatora i MSBuild w Lista błędów](media/compiler-error-list.png "Błędy kompilatora i MSBuild w Lista błędów")

## <a name="document-health-indicator"></a>Wskaźnik kondycji dokumentu

Wskaźnik kondycji dokumentu w dolnej części edytora pokazuje liczbę błędów i ostrzeżeń w bieżącym dokumencie i umożliwia przejście bezpośrednio z jednego ostrzeżenia/błędu do następnego.

![Wskaźnik kondycji dokumentu](media/document-health-indicator.png "Wskaźnik kondycji dokumentu")

W wielu przypadkach więcej informacji o konkretnym błędzie można znaleźć w dokumentacji dotyczącej historii zmian programu Visual Studio i ulepszeń zgodności.

- [C++ulepszenia zgodności](../overview/cpp-conformance-improvements.md)
- [Historia C++ zmian wizualnych 2003 – 2015](visual-cpp-change-history-2003-2015.md)
- [Omówienie potencjalnych problemów z uaktualnianiem](overview-of-potential-upgrade-issues-visual-cpp.md)

## <a name="use-code-analysis-to-modernize-your-code"></a>Korzystanie z analizy kodu do modernizacji kodu

Podczas uaktualniania zalecamy przeprowadzanie analizy kodu w projekcie, aby kod był zgodny z minimalnymi zalecanymi regułami natywnymi firmy Microsoft. Te reguły są kombinacją reguł zdefiniowanych przez firmę Microsoft i podzbiorem [ C++ podstawowych wytycznych](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines). Dzięki temu można znacznie zmniejszyć lub wyeliminować typowe źródła błędów, a jednocześnie poprawić kod i ułatwić jego konserwację. Analiza kodu przy użyciu zalecanych reguł natywnych firmy Microsoft jest domyślnie włączona. Możesz włączyć dodatkowe reguły w obszarze **właściwości** > **projektu** > **Analiza kodu**. Kod naruszający jedną z reguł jest oflagowany jako ostrzeżenie i jest podkreślony zieloną zygzakem w edytorze kodu. Umieść kursor na zygzaku, aby wyświetlić etykietkę narzędzia **sekcji szybkich informacji** , która opisuje problem.

![Etykietka narzędzia analizy kodu](media/code-analysis-tooltip.png "Ostrzeżenie analizy kodu")

Kliknij ikonę filtru w kolumnie **kod** , aby wybrać, które ostrzeżenia są wyświetlane.

![Filtry analizy kodu w Lista błędów](media/code-analysis-filter.png "Filtry analizy kodu w Lista błędów")

Błędy i ostrzeżenia analizy kodu są również wyświetlane w **Lista błędów** , podobnie jak błędy kompilatora.

![Ostrzeżenia analizy kodu w Lista błędów](media/code-analysis-error-list.png "Ostrzeżenia analizy kodu w Lista błędów")

Można zmienić reguły, które są aktywne, i utworzyć niestandardowe zestaw reguł. Aby uzyskać więcej informacji o korzystaniu z analizy kodu, zobacz [Analiza koduC++ dla C/przegląd](/cpp/code-quality/code-analysis-for-c-cpp-overview).

## <a name="use-quick-actions-to-modernize-code"></a>Używanie szybkich akcji do modernizacji kodu

Edytor kodu zapewnia szybkie akcje w przypadku niektórych typowych zaleceń. Gdy zostanie wyświetlona ikona żarówki, możesz ją kliknąć, aby wyświetlić dostępne szybkie akcje.

### <a name="convert-macros-to-constexpr-functions"></a>Konwertuj makra na funkcje constexpr

Na poniższej ilustracji przedstawiono użycie makra o nazwie `AVERAGE`, która ma domyślne kolorowanie semantyczne. Obraz zawiera również etykietkę narzędzia sekcji szybkich informacji, która jest wyświetlana po umieszczeniu kursora myszy na nim:

![Rozwinięcie makra sekcji szybkich informacji](media/macro-expansion-quick-info.png "Sekcji szybkich informacji — rozwinięcie makra etykietki narzędzia")

Ponieważ korzystanie z makr jest niezalecane w nowoczesnych C++, program Visual Studio ułatwia konwertowanie makr na funkcje **constexpr** :

1. Kliknij prawym przyciskiem myszy pozycję `AVERAGE` i wybierz polecenie **Przejdź do definicji**.
2. Kliknij ikonę śrubokrętu i wybierz polecenie **Konwertuj makro na wyrażenie constexpr**

   ![Szybkie makro akcji dla elementu constexpr](media/quick-action-macro-to-constexpr.png "Szybkie makro akcji dla elementu constexpr")

Makro jest konwertowane, jak pokazano poniżej:

![constexpr — funkcja](media/constexpr-function.png "constexpr — funkcja")

A wywołanie `AVERAGE` jest teraz kolorowe jako wywołanie funkcji, a etykietka Szybka podpowiedź pokazuje wywnioskowany typ funkcji:

![Wywołanie funkcji constexpr](media/constexpr-function-call.png "Wywołanie funkcji constexpr")

### <a name="initialize-variables"></a>Inicjowanie zmiennych

Niezainicjowane zmienne mogą przechowywać losowe wartości, które prowadzą do poważnych usterek. Analiza kodu flaguje te wystąpienia, a Edytor zapewnia szybką akcję:

![Zainicjuj zmienną](media/init-variable.png "Inicjowanie zmiennej szybkiej akcji")

### <a name="convert-to-raw-string-literal"></a>Konwertowanie na literał nieprzetworzonego ciągu

Nieprzetworzone literały ciągu są mniej podatne na błędy i wygodniejsze do pisania niż ciągi z osadzonymi znakami ucieczki. Kliknij prawym przyciskiem myszy ciąg i wybierz polecenie **szybkie akcje** , aby przekonwertować go na nieprzetworzony literał ciągu.

![Nieprzetworzony literał ciągu](media/raw-string-literal.png "Nieprzetworzony literał ciągu")

Ciąg jest konwertowany na: `R"(C:\Users\bjarnes\demo\output.txt)"`.
