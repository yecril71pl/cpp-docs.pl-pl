---
title: Opcje EDITBIN
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: e7338c6a45d74aa8efac1b72683cca7661c62e0a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820107"
---
# <a name="editbin-options"></a>Opcje EDITBIN

Aby zmodyfikować pliki obiektów, plików wykonywalnych i bibliotek dołączanych dynamicznie (dll), można użyć polecenia EDITBIN. Opcje określają zmiany, które sprawia, że polecenia EDITBIN.

Opcja składa się z specyfikator opcji kreski (-) lub ukośnikiem (/), następuje nazwa opcji. Nie należy skracać nazwy opcji. Niektóre opcje przyjmują argumentów, które są określone po dwukropek (:). Nie spacje lub tabulatory są dozwolone w obrębie Specyfikacja opcji. Użyj miejsc do magazynowania lub karty do oddzielenia specyfikacje opcji w wierszu polecenia. Nazwy opcji i ich argumentów — słowo kluczowe lub argumenty nazwy pliku nie jest rozróżniana wielkość liter. Na przykład - bind i /BIND oznaczają to samo.

EDITBIN ma następujące opcje:

|Opcja|Cel|
|------------|-------------|
|[/ALLOWBIND](allowbind.md)|Określa, czy biblioteka DLL może być powiązana.|
|[/ALLOWISOLATION](allowisolation.md)|Określa plik DLL lub pliku wykonywalnego, zachowanie wyszukiwania plików manifestu.|
|[/APPCONTAINER](appcontainer.md)|Określa, czy aplikacja musi pracować w ramach kontenera aplikacji — na przykład aplikacji platformy uniwersalnej systemu Windows.|
|[/BIND](bind.md)|Ustawia adresów dla punktów wejścia w określonych obiektów, aby przyspieszyć czas ładowania.|
|[/DYNAMICBASE](dynamicbase.md)|Określa, czy plik DLL lub pliku wykonywalnego obrazu może być losowo przebazowanych w czasie ładowania przy użyciu randomizacji układu przestrzeni adresowej (ASLR).|
|[/ERRORREPORT](errorreport-editbin-exe.md)|Raporty wewnętrzne błędy do firmy Microsoft.|
|[/HEAP](heap.md)|Ustawia rozmiar sterty obrazu pliku wykonywalnego w bajtach.|
|[/HIGHENTROPYVA](highentropyva.md)|Określa, czy plik DLL lub obraz wykonywalny obsługuje randomizacji układu przestrzeni adresowej (64-bitowy) o wysokiej entropii (ASLR).|
|[/INTEGRITYCHECK](integritycheck.md)|Określa, czy do sprawdzenia podpisu cyfrowego w czasie ładowania.|
|[/LARGEADDRESSAWARE](largeaddressaware.md)|Określa, czy obiekt obsługuje adresy, które są większe niż dwa gigabajty.|
|[/NOLOGO](nologo-editbin.md)|Wyłącza transparent startowy EDITBIN.|
|[/NXCOMPAT](nxcompat.md)|Określa, czy obraz wykonywalny jest zgodny z zapobieganiem wykonywaniu danych Windows.|
|[/REBASE](rebase.md)|Ustawia adres podstawowy dla określonych obiektów.|
|[/RELEASE](release.md)|Ustawia sumę kontrolną w nagłówku.|
|[/ SECTION](section-editbin.md)|Zastępuje atrybuty sekcji.|
|[/STACK](stack.md)|Ustawia rozmiar stosu obrazu pliku wykonywalnego w bajtach.|
|[/SUBSYSTEM](subsystem.md)|Określa środowisko wykonawcze.|
|[/SWAPRUN](swaprun.md)|Określa, czy obraz wykonywalny musi być kopiowane do pliku wymiany, a następnie uruchom z tego miejsca.|
|[/TSAWARE](tsaware.md)|Określa, że aplikacja jest przeznaczona do uruchamiania w środowisku wielu użytkowników.|
|[/VERSION](version.md)|Ustawia numer wersji w nagłówku.|

## <a name="see-also"></a>Zobacz także

[MSVC dodatkowe narzędzia do kompilacji](c-cpp-build-tools.md)<br/>
[EDITBIN — dokumentacja](editbin-reference.md)
