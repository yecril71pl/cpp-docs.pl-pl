---
title: Opcje NMAKE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, options
ms.assetid: 00ba1aec-ef27-44cf-8d82-c5c095e45bae
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ef3b987de737d8300f88690754456b73c946180
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-options"></a>Opcje NMAKE
Opcje NMAKE zostały opisane w poniższej tabeli. Opcje są poprzedzone ukośnika (/) i myślnik (-) i nie jest uwzględniana wielkość liter. Użyj [! CMDSWITCHES](../build/makefile-preprocessing-directives.md) Aby zmienić ustawienia opcji w pliku reguł programu make lub Tools.ini.  
  
|Opcja|Cel|  
|------------|-------------|  
|/A|Kompilacja wymusza wszystkich celów obliczane, nawet jeśli nie są nieaktualne względem zależności. Nie wymusza kompilacji niepowiązane elementy docelowe.|  
|/B|Wymusza kompilacji, nawet jeśli sygnatury czasowe są równe. Zalecane tylko dla systemów bardzo szybko (rozdzielczość dwóch sekund lub mniej).|  
|/C|Pomija domyślne danych wyjściowych w tym błędy niekrytyczne NMAKE lub ostrzeżenia, sygnatury czasowe i NMAKE komunikat o prawach autorskich. Pomijaj ostrzeżenia /K.|  
|/D|Sygnatury czasowe Wyświetla każdego oceniać docelowych i zależne od i komunikat, jeśli element docelowy nie istnieje. Przydatne z /P do debugowania pliku reguł programu make. Użyj **! CMDSWITCHES** do ustawiania i czyszczenia /D części pliku reguł programu make.|  
|/E|Powoduje, że zmienne środowiskowe w celu zastąpienia pliku reguł programu make definicje makr.|  
|/ ERRORREPORT [BRAK &#124; WIERSZ &#124; KOLEJKI &#124; WYŚLIJ]|Jeśli nmake.exe zakończy się niepowodzeniem w czasie wykonywania, można użyć/errorreport wysyłać informacje do firmy Microsoft informacji o tych błędach wewnętrznych.<br /><br /> Aby uzyskać więcej informacji na temat/errorreport, zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](../build/reference/errorreport-report-internal-compiler-errors.md).|  
|/F`filename`|Określa `filename` jako pliku reguł programu make. Spacji ani karty należy poprzedzić `filename`. Określ /F raz dla każdego pliku reguł programu make. Aby przekazać pliku reguł programu make z standardowe dane wejściowe, należy określić kreski (-) `filename`i zakończyć wprowadzanie z klawiatury F6 lub CTRL + Z.|  
|/G|Wyświetla pliki reguł programu make dołączonego! Dyrektywy #INCLUDE.  Zobacz [dyrektywy przetwarzania wstępnego pliku reguł programu make](../build/makefile-preprocessing-directives.md) Aby uzyskać więcej informacji.|  
|/ HELP, /?|Wyświetla krótki opis NMAKE składni wiersza polecenia.|  
|/I|Ignoruje kody wyjścia z wszystkich poleceń. Aby ustawić lub wyczyścić /I części pliku reguł programu make, użyj **! CMDSWITCHES**. Aby Ignoruj kody wyjścia części pliku reguł programu make, użyj modyfikatora polecenia kreski (-) lub [. Ignoruj](../build/dot-directives.md). Zastępuje /K, jeśli określono oba.|  
|/K|Kontynuuje tworzenie niepowiązanych zależności, jeśli polecenie zwróci błąd. Ponadto wyświetli ostrzeżenie, a zwraca kod zakończenia 1. Domyślnie NMAKE zostaje zatrzymana, jeśli dowolne polecenie zwróci kod zakończenia różną od zera. Ostrzeżenia /K są pomijane przez /C; /I przesłania /K, jeśli określono oba.|  
|/N|Wyświetla, ale nie wykonuje polecenia; przetwarzania wstępnego polecenia są wykonywane. Nie wyświetlaj polecenia w wywołaniach NMAKE cyklicznego. Przydatne w przypadku debugowania pliki reguł programu make i sprawdzania sygnatur czasowych. Aby ustawić lub wyczyścić /N części pliku reguł programu make, użyj **! CMDSWITCHES**.|  
|/NOLOGO|Pomija komunikat o prawach autorskich NMAKE.|  
|/P|Wyświetla informacje (definicje makr, reguły wnioskowania, obiekty docelowe, [. SUFIKSY](../build/dot-directives.md) listy) do wyjścia standardowego, a następnie uruchomi kompilacji. Jeśli nie pliku reguł programu make wiersza polecenia docelowym istnieje ani, wyświetla tylko informacje. /D za pomocą debugowania pliku reguł programu make.|  
|/Q|Sygnatury czasowe kontroli celów; nie powoduje uruchomienia kompilacji. Zwraca niezerowy kod zakończenia, jeśli wszystkie elementy docelowe są aktualne i kodu zakończenia różną od zera, jeśli wszystkie miejsce docelowe nie jest. Przetwarzania wstępnego polecenia są wykonywane. Przydatne w przypadku uruchomienie NMAKE z pliku wsadowego.|  
|/R|Czyści **. SUFIKSY** listę i ignoruje reguły wnioskowania i makra, które zostały zdefiniowane w pliku Tools.ini lub które są wstępnie zdefiniowane.|  
|/ S|Pomija wyświetlanie wykonanego polecenia. Aby uniknąć wyświetlania w części pliku reguł programu make, użyj  **@**  modyfikator polecenia lub [. DYSKRETNEJ](../build/dot-directives.md). Aby ustawić lub wyczyścić /S części pliku reguł programu make, użyj **! CMDSWITCHES**.|  
|/T|Aktualizuje sygnatury czasowe cele wiersza polecenia (lub pierwszy element docelowy pliku reguł programu make) i wykonuje wstępnego przetwarzania polecenia, ale nie można uruchomić kompilacji.|  
|/U|Należy używać w połączeniu z /N. Zrzuty plików NMAKE wbudowanych, dzięki czemu dane wyjściowe /N mogą być używane jako plik wsadowy.|  
|/X`filename`|Wysyła dane wyjściowe błędów NMAKE do `filename` zamiast standardowego błędu. Spacji ani karty należy poprzedzić `filename`. Aby wysłać dane wyjściowe błędów do wyjścia standardowego, określ kreski (-) `filename`. Nie wpływa na dane wyjściowe polecenia do standardowego błędu.|  
|/ Y|Wyłącza zasady wnioskowania w trybie wsadowym. Gdy ta opcja jest zaznaczona, wszystkie zasady wnioskowania w trybie wsadowym są traktowane jako zasady wnioskowania regularne.|  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchomienie NMAKE](../build/running-nmake.md)