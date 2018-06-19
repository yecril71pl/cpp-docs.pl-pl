---
title: pgomgr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bf7567cfe9f21effda913606ca3af9a19464f9d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377209"
---
# <a name="pgomgr"></a>pgomgr

Dodaje dane profilu z jednego lub więcej plików .pgc do plik .pgd.

## <a name="syntax"></a>Składnia

> **pgomgr** [*opcje*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>Parametry

*Opcje*<br/>
Można określić następujące opcje do **pgomgr**:

- **/ help** lub **/?** Wyświetla dostępne **pgomgr** opcje.

- **/ clear** powoduje, że plik .pgd do wyczyszczenia wszystkich danych profilu. Nie można określić .pgc plików podczas **/clear** jest określona.

- **/ detail** Wyświetla szczegółowe statystyki, w tym informacje o pokryciu Wykres przepływu.

- **/ summary** wyświetla na funkcji statystyk.

- **/ unique** w przypadku użycia z **/summary**, przyczyny dekorowane nazwy funkcji do wyświetlenia. Domyślnie, gdy **/ unique** nie jest używana, jest dla nazwy funkcji bez mają być wyświetlane.

- **/ merge**[**: *** n*] powoduje, że dane w pliku .pgc lub pliki, które mają zostać dodane do pliku .pgd. Opcjonalny parametr *n*, pozwala określić, czy dane powinny zostać dodane *n* razy. Na przykład, jeśli scenariusz często będą gotowe sześć razy do uwzględnienia, jak często jest wykonywane przez klientów, można odbywa się raz w uruchomienia testu i dodaj go do pliku .pgd sześć razy z **pgomgr /merge:6**.

*pgcfiles*<br/>
Co najmniej jeden .pgc pliki danych profilu, którego chcesz scalić plik .pgd. Można określić plik .pgc jednego lub wielu plików .pgc. Jeśli nie określono żadnych plików .pgc **pgomgr** scala wszystkie pliki .pgc, których nazwy plików są takie same jak plik .pgd.

*pgdfile* plik .pgd, do którego są scalane dane z pliku .pgc lub plików.

## <a name="remarks"></a>Uwagi

> [!NOTE]
> To narzędzie można uruchomić tylko z wiersza polecenia programu Visual Studio developer. Nie można uruchomić go z wiersza polecenia systemu lub z Eksploratora plików.

## <a name="example"></a>Przykład

To przykładowe polecenie powoduje wyczyszczenie plików myapp.pgd danych profilów:

`pgomgr /clear myapp.pgd`

To przykładowe polecenie dodaje dane profilu myapp1.pgc do pliku .pgd trzy razy:

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

W tym przykładzie danych profilu z wszystkie pliki # .pgc moja_aplikacja są dodawane do pliku myapp.pgd.

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>Zobacz także

[Optymalizacje sterowane profilem](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
