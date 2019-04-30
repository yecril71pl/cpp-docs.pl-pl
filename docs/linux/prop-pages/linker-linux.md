---
title: Właściwości konsolidatora (Linux C++)
ms.date: 9/26/2017
ms.assetid: a0243a94-8164-425b-b2fe-b84ff363d546
ms.openlocfilehash: 2e5c3446d8daeeb052937b5e172fc9fa4b6ad302
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393041"
---
# <a name="linker-properties-linux-c"></a>Właściwości konsolidatora (Linux C++)

## <a name="general"></a>Ogólne

Właściwość | Opis | Opcje
--- | ---| ---
Plik wyjściowy | Opcja przesłania domyślną nazwę i lokalizację programu tworzonego przez konsolidatora. (-o)
Pokaż postęp | Drukuje wiadomości dotyczące postępu konsolidatora.
Wersja | -Version — opcja nakazuje konsolidatorowi umieszczenie numeru wersji w nagłówku pliku wykonywalnego.
Włącz pełne dane wyjściowe | Verbose — opcja nakazuje konsolidatorowi wysyłanie pełnych komunikatów na potrzeby debugowania.
Śledzenia | --Trace opcji informuje konsolidator, aby dane wyjściowe pliki wejściowe, jak są przetwarzane.
Śledź symbole | Drukuj listę plików, w których jest wyświetlany symbol. (--trace-symbol = symbol)
Drukuj mapę | Print-map — opcja nakazuje konsolidatorowi danych wyjściowych mapę linków.
Raport nierozpoznanych odwołań do symboli | Włączenie tej opcji będzie zgłaszać nierozpoznanych odwołań do symboli.
Optymalizacja pod kątem użycia pamięci | Optymalizuj pod kątem użycia pamięci przez kątem tabel symboli, zgodnie z potrzebami.
Ścieżka wyszukiwania biblioteki udostępnionej | Umożliwia użytkownikowi Wypełnianie ścieżki wyszukiwania biblioteki udostępnionej. (- rpath - link = path)
Dodatkowe katalogi biblioteki | Umożliwia użytkownikowi przesłanianie ścieżki środowiskowej biblioteki. (-L folder).
Konsolidator | Określa program do wywołania podczas łączenia lub ścieżkę do konsoliatora w systemie zdalnym.
Limit czasu łączenia | Limit czasu zdalnego łączenia, w milisekundach.
Kopiuj dane wyjściowe | Określa, czy można skopiować pliku danych wyjściowych kompilacji z systemu zdalnego na maszynę lokalną.

## <a name="input"></a>Dane wejściowe

Właściwość | Opis | Opcje
--- | ---| ---
Ignoruj określone biblioteki domyślne | Określa jedną lub więcej nazw bibliotek domyślnych do zignorowania. (--exclude-libs lib, lib)
Ignoruj biblioteki domyślne | Ignoruj biblioteki domyślne i przeszukiwać tylko biblioteki określone jawnie.
Wymuszaj odwołania do niezdefiniowanych symboli | Symbol wymuszania do można wpisać w pliku wyjściowym jako niezdefiniowanego symbolu. (- u symbol--undefined = symbol)
Zależności biblioteki | Ta opcja umożliwia określenie dodatkowych bibliotek, które mają zostać dodane do wiersza polecenia konsolidatora. Dodatkowa biblioteka zostanie dodany na końcu wiersza polecenia konsolidatora z prefiksem "lib" i kończyć się rozszerzeniem ".a".  (-lFILE)
{1&gt;Dodatkowe zależności&lt;1} | Określa dodatkowe elementy do dodania do wiersza polecenia konsolidacji.

## <a name="debugging"></a>Debugowanie

Właściwość | Opis | Opcje
--- | ---| ---
Informacje o symbolach debugera | Informacje o symbolach w pliku danych wyjściowych debugera. | **Uwzględnij wszystkie**<br>**Pomiń informacje o symbolach debugera tylko**<br>**Pomiń wszystkie informacje o symbolach**<br>
Nazwa pliku mapy | Opcja Map nakazuje konsolidatorowi utworzenie pliku mapy o nazwie określonej przez użytkownika. (-Map =)

## <a name="advanced"></a>Zaawansowane

Właściwość | Opis | Opcje
--- | ---| ---
Oznacz zmienne tylko do odczytu po relokacji | Ta opcja oznacza zmienne jako tylko do odczytu po relokacji.
Włącz natychmiastowe powiązanie funkcji | Ta opcja oznacza obiekt do natychmiastowego powiązania funkcji.
Nie wymagaj stosu wykonywalnego | Ta opcja oznacza dane wyjściowe jako niewymagające stosu wykonywalnego.
Całe archiwum | Całe archiwum używa całego kodu ze źródeł i zależności dodatkowych.
