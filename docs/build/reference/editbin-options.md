---
title: Opcje EDITBIN
description: Przewodnik referencyjny dotyczący opcji wiersza polecenia narzędzia Microsoft polecenia EDITBIN.
ms.date: 02/09/2020
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: 9fd4170e5ee020780963d83936f1a9fd08d2be11
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439977"
---
# <a name="editbin-options"></a>Opcje EDITBIN

Można użyć polecenia EDITBIN do modyfikacji plików obiektów, plików wykonywalnych i bibliotek dołączanych dynamicznie (dll). Opcje określają zmiany wprowadzane przez polecenia EDITBIN.

Opcja składa się ze specyfikatora opcji, który jest kreską (`-`) lub ukośnikiem (`/`), po którym następuje nazwa opcji. Nazwy opcji nie mogą być skracane. Niektóre opcje przyjmują argumenty, które są określone po dwukropku (`:`). W specyfikacji opcji nie można używać spacji ani tabulatorów. Użyj co najmniej jednej spacji lub kart, aby oddzielić specyfikacje opcji w wierszu polecenia. Nazwy opcji i ich argumenty słów kluczowych lub argumenty nazwy pliku nie są rozróżniane wielkości liter. Na przykład `-bind` i `/BIND` oznaczają to samo.

POLECENIA EDITBIN z następującymi opcjami:

|Opcja|Przeznaczenie|
|------------|-------------|
|[/ALLOWBIND](allowbind.md)|Określa, czy można powiązać bibliotekę DLL.|
|[/ALLOWISOLATION](allowisolation.md)|Określa zachowanie wyszukiwania pliku DLL lub wykonywalnego manifestu.|
|[/APPCONTAINER](appcontainer.md)|Określa, czy aplikacja musi być uruchomiona w kontenerze aplikacji, na przykład w aplikacji platformy UWP.|
|[/BIND](bind.md)|Ustawia adresy dla punktów wejścia w określonych obiektach, aby skrócić czas ładowania.|
|[/DYNAMICBASE](dynamicbase.md)|Określa, czy obraz DLL lub plik wykonywalny może być losowo zmieniany w czasie ładowania przy użyciu losowego generowania układu przestrzeni adresowej (ASLR).|
|[/ERRORREPORT](errorreport-editbin-exe.md)| Przestarzałe. Raportowanie błędów jest kontrolowane przez ustawienia [raportowanie błędów systemu Windows (wer)](/windows/win32/wer/windows-error-reporting) . |
|[/HEAP](heap.md)|Ustawia rozmiar sterty obrazu wykonywalnego w bajtach.|
|[/HIGHENTROPYVA](highentropyva.md)|Określa, czy obraz DLL lub wykonywalny 64 obsługuje losowe generowanie układu przestrzeni adresowej (ASLR).|
|[/INTEGRITYCHECK](integritycheck.md)|Określa, czy podpis cyfrowy ma być sprawdzany w czasie ładowania.|
|[/LARGEADDRESSAWARE](largeaddressaware.md)|Określa, czy obiekt obsługuje adresy, które są większe niż dwa gigabajty.|
|[/NOLOGO](nologo-editbin.md)|Pomija transparent startowy polecenia EDITBIN.|
|[/NXCOMPAT](nxcompat.md)|Określa, czy obraz wykonywalny jest zgodny z funkcją zapobiegania wykonywaniu danych systemu Windows.|
|[/REBASE](rebase.md)|Ustawia adresy podstawowe dla określonych obiektów.|
|[/RELEASE](release.md)|Ustawia sumę kontrolną w nagłówku.|
|[/SECTION](section-editbin.md)|Zastępuje atrybuty sekcji.|
|[/STACK](stack.md)|Ustawia rozmiar stosu obrazu wykonywalnego w bajtach.|
|[/SUBSYSTEM](subsystem.md)|Określa środowisko wykonawcze.|
|[/SWAPRUN](swaprun.md)|Określa, czy obraz wykonywalny jest kopiowany do pliku wymiany, a następnie uruchamia z tego miejsca.|
|[/TSAWARE](tsaware.md)|Określa, że aplikacja została zaprojektowana do działania w środowisku wielodostępnym.|
|[/VERSION](version.md)|Ustawia numer wersji w nagłówku.|

## <a name="see-also"></a>Zobacz też

[Dodatkowe\ narzędzia kompilacji MSVC](c-cpp-build-tools.md)
[EDITBIN — dokumentacja](editbin-reference.md)
