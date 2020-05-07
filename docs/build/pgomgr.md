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

Dodaje dane profilu z jednego lub więcej plików. PGC do pliku. pgd.

## <a name="syntax"></a>Składnia

> **pgomgr** [*Opcje*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>Parametry

*Opcje*<br/>
Do **pgomgr**można określić następujące opcje:

- **/help** lub **/?** Wyświetla dostępne opcje **pgomgr** .

- **/Clear** Powoduje, że plik. PGD ma zostać wyczyszczony ze wszystkich informacji o profilu. Nie można określić pliku. PGC, gdy **/Clear** jest określony.

- **/detail** Wyświetla szczegółowe dane statystyczne, w tym informacje o zapotrzebowaniu grafu przepływu.

- **/Summary** Wyświetla statystyki dla poszczególnych funkcji.

- **/Unique** Gdy jest używany z **/Summary**, powoduje wyświetlenie nazw funkcji dekoracyjnych. Wartość domyślna, gdy **/Unique** nie jest używana, jest przeznaczony do wyświetlania niedekoracyjnych nazw funkcji.

- **/Merge**\[**:**<em>n</em>] powoduje dodanie danych z pliku. PGC lub plików do pliku. pgd. Opcjonalny parametr *n*, umożliwia określenie, że dane powinny być dodawane *n* razy. Na przykład, jeśli scenariusz będzie często wykonywany sześć razy, aby odzwierciedlić, jak często jest wykonywane przez klientów, można wykonać tę czynność jeden raz w przebiegu testowym i dodać go do pliku. PGD sześć razy z **pgomgr/MERGE: 6**.

*pgcfiles*<br/>
Jeden lub więcej plików. PGC, których dane profilowe mają zostać scalone w pliku. pgd. Można określić pojedynczy plik PGC lub wiele plików. pgc. Jeśli nie określisz żadnych plików PGC, **pgomgr** scala wszystkie pliki. PGC, których nazwy plików są takie same jak plik. pgd.

*pgdfile*<br/>
Plik. pgd, do którego są scalane dane z pliku. PGC lub plików.

## <a name="remarks"></a>Uwagi

> [!NOTE]
> To narzędzie można uruchomić tylko z poziomu wiersza polecenia programu Visual Studio Developer. Nie można uruchomić go z poziomu wiersza polecenia systemu lub Eksploratora plików.

## <a name="example"></a>Przykład

To przykładowe polecenie czyści plik MojaApl. PGD danych profilu:

`pgomgr /clear myapp.pgd`

To przykładowe polecenie dodaje dane profilowe w myapp1. PGC do pliku. PGD trzy razy:

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

W tym przykładzie dane profilowe wszystkich plików MojaApl #. pgc są dodawane do pliku Mojaapl. pgd.

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>Zobacz też

[Optymalizacje sterowane profilem](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
