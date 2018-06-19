---
title: pgosweep | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ded5b692d7c51e5a46a325a69ad6969083025ff5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378928"
---
# <a name="pgosweep"></a>pgosweep

Używane w Optymalizacja sterowana profilem, aby zapisać wszystkie dane profilu z uruchomiony program plik .pgc.

## <a name="syntax"></a>Składnia

> **pgosweep** [*opcje*] *obrazu* *pgcfile*

### <a name="parameters"></a>Parametry

*opcje* (opcjonalnie)<br/>
Prawidłowe wartości dla *opcje* są:

- **/?** lub **/help** wyświetla komunikat pomocy.

- **/noreset** zachowuje liczba w strukturach danych w czasie wykonywania.

*image*<br/>
Pełna ścieżka pliku .exe lub .dll, który został utworzony przy użyciu [opcji/genprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md), [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md), lub [/LTCG:PGINSTRUMENT](ltcg-link-time-code-generation.md) opcji.

*pgcfile*<br/>
Plik .pgc, gdzie to polecenie zapisuje dane liczby.

## <a name="remarks"></a>Uwagi

**Pgosweep** polecenie działa programów, które zostały utworzone przy użyciu [opcji/genprofile lub /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) opcji lub przestarzałe [/LTCG:PGINSTRUMENT](ltcg-link-time-code-generation.md) opcji. Przerywa uruchomiony program, a zapisuje dane profilu do nowego pliku .pgc. Domyślnie polecenie resetuje licznik po zakończeniu każdej operacji zapisu. Jeśli określisz **/noreset** opcji polecenia zapisać wartości, ale nie ich ponownie w uruchomiony program. Ta opcja umożliwia zduplikowane dane po pobraniu danych profilu później.

Alternatywnego wykorzystania **pgosweep** pobieranie informacji o profilu do normalnego działania aplikacji. Na przykład można uruchomić **pgosweep** wkrótce po uruchomić aplikację i odrzucić tego pliku. Spowoduje to usunięcie profilu dane skojarzone z kosztami uruchomienia. Następnie można uruchomić **pgosweep** przed zakończeniem aplikacji. Informacje o profilu tylko od czasu się, że użytkownik może interakcyjnie program ma teraz zebranych danych.

Jeśli nazwa pliku .pgc (przy użyciu *pgcfile* parametru) można użyć standardowego formatu, który jest *appname! n*.pgc. Jeśli używasz tego formatu, kompilator automatycznie znajdzie te dane w **/LTCG /USEPROFILE** lub **/LTCG:PGO** fazy. Jeśli nie używasz standardowego formatu, należy użyć [pgomgr](pgomgr.md) można scalić plików PGC.

> [!NOTE]
> To narzędzie można uruchomić tylko z wiersza polecenia programu Visual Studio developer. Nie można uruchomić go z wiersza polecenia systemu lub z Eksploratora plików.

Aby uzyskać informacje na temat sposobu przechwytywania danych profilu z poziomu pliku wykonywalnego, zobacz [PgoAutoSweep](pgoautosweep.md).

## <a name="example"></a>Przykład

W tym przykładzie polecenia **pgosweep** zapisuje informacji o bieżącym profilu dla myapp.exe myapp!1.pgc.

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>Zobacz także

[Optymalizacje sterowane profilem](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
