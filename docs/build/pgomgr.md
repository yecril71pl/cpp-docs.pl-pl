---
title: pgomgr
ms.date: 03/14/2018
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
ms.openlocfilehash: 4e3eb08c88db9d0ed4e47649014a600c3e0ccb78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295256"
---
# <a name="pgomgr"></a>pgomgr

Dane profilowe z co najmniej jeden plik .pgc są dodawane do pliku .pgd.

## <a name="syntax"></a>Składnia

> **pgomgr** [*opcje*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>Parametry

*Opcje*<br/>
Można określić następujące opcje w celu **pgomgr**:

- **/ help** lub **/?** Wyświetla dostępne **pgomgr** opcje.

- **/ clear** powoduje, że plik .pgd do wyczyszczenia wszystkich informacji o profilu. Nie można określić .pgc pliku, kiedy **/clear** jest określony.

- **/ detail** Wyświetla szczegółowe statystyki, w tym informacje o pokryciu Wykres przepływu.

- **/ summary** Wyświetla poszczególnych funkcji statystyk.

- **/ Unikatowy** gdy jest używane z **/summary**, powoduje, że dekorowane nazwy funkcji, aby wyświetlić. Wartość domyślna, gdy **/ unikatowy** nie jest używany, to dla nazw niedekorowanego funkcji, które mają być wyświetlane.

- **/ merge**\[**:**<em>n</em>] powoduje, że dane w pliku .pgc lub plików, które mają zostać dodane do pliku .pgd. Opcjonalny parametr *n*, pozwala określić, że dane należy dodać *n* razy. Na przykład, jeśli scenariusz będzie najczęściej gotowe sześć razy do uwzględnienia, jak często jest wykonywane przez klientów, można ją wykonać jeden raz w przebiegu testu i dodać go do pliku .pgd sześciokrotnie z **pgomgr /merge:6**.

*pgcfiles*<br/>
Co najmniej jeden .pgc pliki danych profilu, którego chcesz scalić plik .pgd. Można określić plik .pgc jednego lub wielu plików .pgc. Jeśli nie określisz żadnych plików .pgc **pgomgr** scala wszystkie pliki .pgc, których nazwy plików są takie same jak plik .pgd.

*pgdfile*<br/>
Plik .pgd, do którego są scalane dane z pliku .pgc lub plików.

## <a name="remarks"></a>Uwagi

> [!NOTE]
> To narzędzie można uruchomić tylko z poziomu wiersza polecenia dla deweloperów programu Visual Studio. Nie można uruchomić go z wiersza poleceń systemu lub Eksploratora plików.

## <a name="example"></a>Przykład

To przykładowe polecenie usuwa plik myapp.pgd dane profilu:

`pgomgr /clear myapp.pgd`

To przykładowe polecenie dodaje dane profilu w myapp1.pgc do pliku .pgd trzy razy:

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

W tym przykładzie dane profilu ze wszystkich wygenerowanych plików # .pgc myapp jest dodawane do pliku myapp.pgd.

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>Zobacz także

[Optymalizacje sterowane profilem](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
