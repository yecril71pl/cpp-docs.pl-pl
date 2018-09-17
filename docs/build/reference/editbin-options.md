---
title: Opcje EDITBIN | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- editbin
dev_langs:
- C++
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0850f242b8368a9592a5622e627c781b4df4cde5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710141"
---
# <a name="editbin-options"></a>Opcje EDITBIN

Aby zmodyfikować pliki obiektów, plików wykonywalnych i bibliotek dołączanych dynamicznie (dll), można użyć polecenia EDITBIN. Opcje określają zmiany, które sprawia, że polecenia EDITBIN.

Opcja składa się z specyfikator opcji kreski (-) lub ukośnikiem (/), następuje nazwa opcji. Nie należy skracać nazwy opcji. Niektóre opcje przyjmują argumentów, które są określone po dwukropek (:). Nie spacje lub tabulatory są dozwolone w obrębie Specyfikacja opcji. Użyj miejsc do magazynowania lub karty do oddzielenia specyfikacje opcji w wierszu polecenia. Nazwy opcji i ich argumentów — słowo kluczowe lub argumenty nazwy pliku nie jest rozróżniana wielkość liter. Na przykład - bind i /BIND oznaczają to samo.

EDITBIN ma następujące opcje:

|Opcja|Cel|
|------------|-------------|
|[/ALLOWBIND](../../build/reference/allowbind.md)|Określa, czy biblioteka DLL może być powiązana.|
|[/ALLOWISOLATION](../../build/reference/allowisolation.md)|Określa plik DLL lub pliku wykonywalnego, zachowanie wyszukiwania plików manifestu.|
|[/APPCONTAINER](../../build/reference/appcontainer.md)|Określa, czy aplikacja musi pracować w ramach kontenera aplikacji — na przykład aplikacji platformy uniwersalnej systemu Windows.|
|[/BIND](../../build/reference/bind.md)|Ustawia adresów dla punktów wejścia w określonych obiektów, aby przyspieszyć czas ładowania.|
|[/DYNAMICBASE](../../build/reference/dynamicbase.md)|Określa, czy plik DLL lub pliku wykonywalnego obrazu może być losowo przebazowanych w czasie ładowania przy użyciu randomizacji układu przestrzeni adresowej (ASLR).|
|[/ERRORREPORT](../../build/reference/errorreport-editbin-exe.md)|Raporty wewnętrzne błędy do firmy Microsoft.|
|[/HEAP](../../build/reference/heap.md)|Ustawia rozmiar sterty obrazu pliku wykonywalnego w bajtach.|
|[/HIGHENTROPYVA](../../build/reference/highentropyva.md)|Określa, czy plik DLL lub obraz wykonywalny obsługuje randomizacji układu przestrzeni adresowej (64-bitowy) o wysokiej entropii (ASLR).|
|[/INTEGRITYCHECK](../../build/reference/integritycheck.md)|Określa, czy do sprawdzenia podpisu cyfrowego w czasie ładowania.|
|[/LARGEADDRESSAWARE](../../build/reference/largeaddressaware.md)|Określa, czy obiekt obsługuje adresy, które są większe niż dwa gigabajty.|
|[/NOLOGO](../../build/reference/nologo-editbin.md)|Wyłącza transparent startowy EDITBIN.|
|[/NXCOMPAT](../../build/reference/nxcompat.md)|Określa, czy obraz wykonywalny jest zgodny z zapobieganiem wykonywaniu danych Windows.|
|[/REBASE](../../build/reference/rebase.md)|Ustawia adres podstawowy dla określonych obiektów.|
|[/RELEASE](../../build/reference/release.md)|Ustawia sumę kontrolną w nagłówku.|
|[/ SECTION](../../build/reference/section-editbin.md)|Zastępuje atrybuty sekcji.|
|[/STACK](../../build/reference/stack.md)|Ustawia rozmiar stosu obrazu pliku wykonywalnego w bajtach.|
|[/SUBSYSTEM](../../build/reference/subsystem.md)|Określa środowisko wykonawcze.|
|[/SWAPRUN](../../build/reference/swaprun.md)|Określa, czy obraz wykonywalny musi być kopiowane do pliku wymiany, a następnie uruchom z tego miejsca.|
|[/TSAWARE](../../build/reference/tsaware.md)|Określa, że aplikacja jest przeznaczona do uruchamiania w środowisku wielu użytkowników.|
|[/VERSION](../../build/reference/version.md)|Ustawia numer wersji w nagłówku.|

## <a name="see-also"></a>Zobacz też

[Narzędzia kompilacji C/C++](../../build/reference/c-cpp-build-tools.md)<br/>
[EDITBIN — dokumentacja](../../build/reference/editbin-reference.md)