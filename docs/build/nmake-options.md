---
title: Opcje NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, options
ms.assetid: 00ba1aec-ef27-44cf-8d82-c5c095e45bae
ms.openlocfilehash: 84130afea6cc73c480b46f065d6d85e365101b38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455344"
---
# <a name="nmake-options"></a>Opcje NMAKE

Opcje NMAKE są opisane w poniższej tabeli. Opcje są poprzedzone kreską (-) lub ukośnika (/) i nie jest uwzględniana wielkość liter. Użyj [! CMDSWITCHES](../build/makefile-preprocessing-directives.md) Aby zmienić ustawienia opcji w pliku reguł programu make lub Tools.ini.

|Opcja|Cel|
|------------|-------------|
|/A|Kompilacja wymusza wszystkich ocenianych obiektów docelowych, nawet jeśli nie nieaktualne w odniesieniu do elementów zależnych. Wymuszaj kompilacji niepowiązane elementy docelowe.|
|/B|Wymusza kompilacji, nawet jeśli sygnatury czasowe są równe. Zalecane tylko dla systemów bardzo szybko (rozdzielczość dwóch sekund lub mniej).|
|/C|Pomija domyślne dane wyjściowe, w tym błędy niekrytyczne NMAKE lub ostrzeżenia, sygnatur czasowych i komunikat o prawach autorskich NMAKE. Powoduje pominięcie ostrzeżenia /K.|
|/D|Wyświetla sygnatury czasowe w każdej wyznaczane docelowego i zależnych od ustawień lokalnych oraz wiadomość, element docelowy nie istnieje. Przydatne podczas debugowania pliku reguł programu make w za pomocą /P. Użyj **! CMDSWITCHES** do ustawiania i czyszczenia /D dla części pliku reguł programu make.|
|/E|Powoduje, że zmiennych środowiskowych w celu zastąpienia pliku reguł programu make definicje makr.|
|/ ERRORREPORT [BRAK &AMP;#124; MONITU &AMP;#124; KOLEJKI &AMP;#124; WYSYŁANIA]|Jeśli nmake.exe zakończy się niepowodzeniem w czasie wykonywania, można użyć/errorreport do wysyłania informacji do firmy Microsoft dotyczących tych błędów wewnętrznych.<br /><br /> Aby uzyskać więcej informacji na temat/errorreport zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](../build/reference/errorreport-report-internal-compiler-errors.md).|
|/F *nazwy pliku*|Określa *filename* jako pliku reguł programu make. Spacje lub tabulatory może poprzedzać *filename*. Określ /F jeden raz dla każdego pliku reguł programu make. Aby przekazać pliku reguł programu make ze standardowego wejścia, należy określić kreski (-) *filename*i Zakończ wprowadzanie z klawiatury F6 lub CTRL + Z.|
|/G|Wyświetla pliki reguł programu make dołączone! Dyrektywy #INCLUDE.  Zobacz [dyrektywy przetwarzania wstępnego pliku reguł programu make](../build/makefile-preprocessing-directives.md) Aby uzyskać więcej informacji.|
|/ HELP, /?|Wyświetla krótkie podsumowanie NMAKE składni wiersza polecenia.|
|/I|Ignoruje kody wyjścia z wszystkich poleceń. Aby ustawić lub wyczyścić /I dla części pliku reguł programu make, należy użyć **! CMDSWITCHES**. Ignoruje kody zakończenia dla części pliku reguł programu make, użyj modyfikatora polecenia kreski (-) lub [. Ignoruj](../build/dot-directives.md). /K zastępuje, jeśli są określone oba.|
|/K|Kontynuuje tworzenie niepowiązanych zależności, jeśli polecenie zwróci błąd. Również generuje ostrzeżenie i zwraca kod zakończenia o 1. Domyślnie NMAKE zatrzymuje się jeśli dowolne polecenie zwróci kod zakończenia różny od zera. Ostrzeżenia z /K są pomijane przez /C; /I zastępuje /K, jeśli są określone oba.|
|/N|Wyświetla, ale nie wykonuj polecenia; poleceń przetwarzania wstępnego są wykonywane. Nie są wyświetlane polecenia w wywołaniach NMAKE cykliczne. Przydatne w przypadku debugowania plików reguł programu make i sprawdzanie sygnatur czasowych. Aby ustawić lub wyczyścić /N dla części pliku reguł programu make, należy użyć **! CMDSWITCHES**.|
|/NOLOGO|Pomija komunikat o prawach autorskich NMAKE.|
|/P|Wyświetla informacje (definicje makr, reguły wnioskowania, obiekty docelowe, [. SUFIKSY](../build/dot-directives.md) listy) do wyjścia standardowego, a następnie uruchamia kompilację. W przypadku braku pliku reguł programu make lub docelowego wiersza polecenia wyświetla tylko informacje. Za pomocą /D do debugowania pliku reguł programu make.|
|/ Q|Sprawdzanie sygnatur czasowych, celów; nie powoduje uruchomienia kompilacji. Zwraca niezerowy kod zakończenia, jeśli wszystkie elementy docelowe są aktualne i kod zakończenia różny od zera, jeśli wszystkie element docelowy nie jest. Poleceń przetwarzania wstępnego są wykonywane. Parametr jest przydatne, gdy uruchomienie NMAKE z pliku wsadowego.|
|/ R|Czyści **. SUFIKSY** listy i ignoruje reguły wnioskowania i makra, które są zdefiniowane w pliku Tools.ini lub które są wstępnie zdefiniowane.|
|/S|Pomija wyświetlanie wykonane polecenia. Aby wyłączyć wyświetlanie części pliku reguł programu make, należy użyć **\@** modyfikator polecenia lub [. DYSKRETNEJ](../build/dot-directives.md). Aby ustawić lub wyczyścić /S dla części pliku reguł programu make, należy użyć **! CMDSWITCHES**.|
|/ T|Aktualizuje sygnatury czasowe cele wiersza polecenia (lub pierwszego obiektu docelowego pliku reguł programu make) i wykonuje poleceń przetwarzania wstępnego, ale nie uruchamia kompilację.|
|/U|Należy używać w połączeniu z /N. Zrzuty plików NMAKE wbudowanych tak, aby dane wyjściowe /N może służyć jako pliku wsadowego.|
|/X *nazwy pliku*|Wysyła dane wyjściowe błędów NMAKE w *filename* zamiast błędu standardowego. Spacje lub tabulatory może poprzedzać *filename*. Aby wysłać dane wyjściowe błędu do wyjścia standardowego, należy określić kreski (-) *filename*. Nie ma wpływu na dane wyjściowe z polecenia do błędu standardowego.|
|/Y|Wyłącza reguły wnioskowania w trybie wsadowym. Po wybraniu tej opcji wszystkie reguły wnioskowania w trybie wsadowym są traktowane jako reguły wnioskowania regularne.|

## <a name="see-also"></a>Zobacz też

[Uruchomienie NMAKE](../build/running-nmake.md)
