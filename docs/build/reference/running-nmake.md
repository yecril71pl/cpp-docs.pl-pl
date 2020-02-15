---
title: Uruchomienie NMAKE
description: Przewodnik referencyjny dotyczący opcji wiersza polecenia w programie Microsoft NMAKE.
ms.date: 02/09/2020
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
ms.openlocfilehash: bfada33a89c04d25bf7444cbf3b1e7ef3ed44385
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257597"
---
# <a name="running-nmake"></a>Uruchomienie NMAKE

## <a name="syntax"></a>Składnia

> **NMAKE** [*opcja* ...] [*makra* ...] [*elementy docelowe* ...] [ **\@** _plik polecenia_ ...]

## <a name="remarks"></a>Uwagi

NMAKE kompiluje tylko określone *elementy docelowe* lub, jeśli żadna nie jest określona, pierwszy element docelowy w pliku reguł programu make. Pierwszy obiekt docelowy pliku reguł programu make może być [pseudotarget](description-blocks.md#pseudotargets) , który kompiluje inne elementy docelowe. NMAKE używa plików reguł programu make określonych za pomocą **/f**lub jeśli **/f** nie jest określony, plik reguł programu make w bieżącym katalogu. Jeśli plik reguł programu make nie zostanie określony, używa reguł wnioskowania do kompilowania *obiektów docelowych*wiersza polecenia.

Plik tekstowy *pliku polecenia* (lub plik odpowiedzi) zawiera dane wejściowe wiersza polecenia. Inne dane wejściowe mogą poprzedzać lub stosować \@*pliku poleceń*. Ścieżka jest dozwolona. W *pliku poleceń*podziały wierszy są traktowane jako spacje. Należy ująć definicje makr w cudzysłowy, jeśli zawierają one spacje.

## <a name="nmake-options"></a>Opcje NMAKE

Opcje NMAKE są opisane w poniższej tabeli. Opcje są poprzedzone ukośnikiem (`/`) lub kreską (`-`) i nie jest rozróżniana wielkość liter. Użyj [`!CMDSWITCHES`](makefile-preprocessing-directives.md) , aby zmienić ustawienia opcji w pliku reguł programu make lub pliku Tools. ini.

| Opcja | Przeznaczenie |
| ------------ | ------------- |
| **/A** | Wymusza kompilację wszystkich ocenionych elementów docelowych nawet wtedy, gdy nie są one nieaktualne w porównaniu do elementów zależnych. Nie wymusza kompilacji niepowiązanych elementów docelowych. |
| **/B** | Wymusza kompilację, nawet jeśli sygnatury czasowe są równe. Zalecane tylko w przypadku systemów szybkich (rozdzielczości co najmniej dwa sekundy). |
| **/C** | Pomija domyślne dane wyjściowe, w tym niekrytyczne Błędy NMAKE lub ostrzeżenia, sygnatury czasowe i wiadomości o prawach autorskich NMAKE. Pomija ostrzeżenia wystawione przez **/k**. |
| **Parametr** | Wyświetla sygnatury czasowe każdego ocenianego elementu docelowego, zależnie i komunikat, gdy element docelowy nie istnieje. Przydatne w przypadku opcji **/p** dla debugowania pliku reguł programu make. Użyj `!CMDSWITCHES`, aby ustawić lub wyczyścić element **/d** dla części pliku reguł programu make. |
| **/E** | Powoduje, że zmienne środowiskowe przesłaniają definicje makr pliku reguł programu make. |
| **/errorreport** [ **Brak** &#124; **monitu o potwierdzenie** &#124; **kolejki** &#124; **]** | Przestarzałe. Ustawienia funkcji [raportowanie błędów systemu Windows (raportowanie błędów)](/windows/win32/wer/windows-error-reporting) kontrolują raportowanie. |
| **/F** *filename* | Określa *nazwę pliku* jako plik reguł programu make. Spacje lub tabulatory mogą poprzedzać *nazwę pliku*. Określ **/f** jednokrotnie dla każdego pliku reguł programu make. Aby udostępnić plik reguł programu make ze standardowego wejścia, określ kreskę (`-`) dla *nazwy pliku*, a następnie Zakończ wprowadzanie klawiatury przy użyciu **klawisza F6** lub **Ctrl + z**. |
| **/G** | Wyświetla listę plików reguł programu make uwzględnioną w dyrektywie `!INCLUDE`. Aby uzyskać więcej informacji, zobacz [dyrektywy wstępnego przetwarzania plików reguł programu make](makefile-preprocessing-directives.md). |
| **/Help**, **/?** | Wyświetla krótkie podsumowanie składni wiersza polecenia NMAKE. |
| **/I** | Ignoruje kody zakończenia ze wszystkich poleceń. Aby ustawić lub wyczyścić polecenie **/i** dla części pliku reguł programu make, użyj `!CMDSWITCHES`. Aby zignorować kody zakończenia dla części pliku reguł programu make, należy użyć modyfikatora poleceń (`-`) lub [`.IGNORE`](dot-directives.md). Przesłanias **/k** , jeśli oba są określone. |
| **/K** | Kontynuuje Tworzenie niepowiązanych zależności, jeśli polecenie zwróci błąd. Generuje również ostrzeżenie i zwraca kod zakończenia 1. Domyślnie NMAKE zatrzymuje się, Jeśli dowolne polecenie zwróci kod zakończenia różny od zera. Ostrzeżenia z **/k** są pomijane przez **/c**; **/I** przesłania **/k** , jeśli oba są określone. |
| **/N** | Wyświetla, ale nie wykonuje poleceń; polecenia przetwarzania wstępnego są wykonywane. Nie wyświetla poleceń w cyklicznych wywołaniach NMAKE. Przydatne do debugowania plików reguł programu make i sprawdzania sygnatur czasowych. Aby ustawić lub wyczyścić **/n** dla części pliku reguł programu make, użyj `!CMDSWITCHES`. |
| **/NOLOGO** | Pomija komunikat o prawach autorskich NMAKE. |
| **/P** | Wyświetla informacje (definicje makr, reguły wnioskowania, elementy docelowe, lista [`.SUFFIXES`](dot-directives.md) ) do wyjścia standardowego, a następnie uruchamia kompilację. Jeśli nie istnieje plik reguł programu make lub wiersza polecenia, zawiera on tylko informacje. Użyj parametru **/d** , aby debugować plik reguł programu make. |
| **Parametru** | Sprawdza sygnatury czasowe obiektów docelowych; nie uruchamia kompilacji. Zwraca zerowy kod zakończenia, jeśli wszystkie elementy docelowe są aktualne, a niezerowy kod zakończenia, jeśli którykolwiek element docelowy jest nieaktualny. Polecenia przetwarzania wstępnego są wykonywane. Przydatne podczas uruchamiania NMAKE z pliku wsadowego. |
| **/R** | Czyści listę `.SUFFIXES` i ignoruje reguły wnioskowania i makra, które są zdefiniowane w pliku Tools. ini lub wstępnie zdefiniowane. |
| **/S** | Pomija wyświetlanie wykonanych poleceń. Aby pominąć wyświetlanie w części pliku reguł programu make, użyj modyfikatora poleceń **\@** lub [`.SILENT`](dot-directives.md). Aby ustawić lub wyczyścić **/s** dla części pliku reguł programu make, użyj `!CMDSWITCHES`. |
| **/T** | Aktualizuje sygnatury czasowe obiektów docelowych wiersza polecenia (lub pierwszy element docelowy pliku reguł programu make) i wykonuje polecenia przetwarzania wstępnego, ale nie uruchamia kompilacji. |
| **Określ** | Musi być używany w połączeniu z **/n**. Wykonuje zrzuty wbudowanych plików NMAKE, aby **/n** dane wyjściowe mogły być używane jako plik wsadowy. |
| **/X** *filename* | Wysyła dane wyjściowe błędu NMAKE do *nazwy pliku* zamiast standardowego błędu. Spacje lub tabulatory mogą poprzedzać *nazwę pliku*. Aby wysłać dane wyjściowe z błędami do wyjścia standardowego, określ kreskę (`-`) dla *nazwy pliku*. Nie ma wpływu na dane wyjściowe z poleceń na błąd standardowy. |
| **/Y** | Wyłącza reguły wnioskowania w trybie wsadowym. Po wybraniu tej opcji wszystkie reguły wnioskowania w trybie wsadowym są traktowane jak regularne reguły wnioskowania. |

## <a name="toolsini-and-nmake"></a>Tools.ini i NMAKE

NMAKE odczytuje pliki Tools. ini przed odczytem plików reguł programu make, chyba że **/r** jest używany. Szuka najpierw pliku Tools. ini w bieżącym katalogu, a następnie w katalogu określonym przez zmienną środowiskową INIT. Sekcja dla ustawień NMAKE w pliku inicjującym rozpoczyna się od `[NMAKE]` i może zawierać wszelkie informacje dotyczące pliku reguł programu make. Określ komentarz w osobnym wierszu zaczynający się od znaku numeru (`#`).

## <a name="exit-codes-from-nmake"></a>Kody zakończenia z NMAKE

NMAKE zwraca następujące kody zakończenia:

| Kod | Znaczenie |
| ---------- | ------------- |
| 0 | Brak błędu (prawdopodobnie ostrzeżenie) |
| 1 | Niekompletna kompilacja (wystawiona tylko wtedy, gdy jest używana **/k** ) |
| 2 | Błąd programu, prawdopodobnie spowodowany przez jeden z następujących problemów:<br /> -Błąd składniowy w pliku reguł programu make<br /> -Błąd lub kod zakończenia z polecenia<br /> -Przerwanie przez użytkownika |
| 4 | Błąd systemu — za mało pamięci |
| 255 | Element docelowy jest nieaktualny (wydano tylko wtedy, gdy jest używany **/q** ) |

## <a name="see-also"></a>Zobacz też

[NMAKE — dokumentacja](nmake-reference.md)
