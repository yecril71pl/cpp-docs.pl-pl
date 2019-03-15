---
title: pgosweep
ms.date: 03/14/2018
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
ms.openlocfilehash: 3ba31671fc3794e1cc959d86d914ba1eef2e01e4
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823821"
---
# <a name="pgosweep"></a>pgosweep

Używane w optymalizacji sterowanej profilem, aby zapisać wszystkie dane profilu z uruchomionego programu plik .pgc.

## <a name="syntax"></a>Składnia

> **pgosweep** [*options*] *image* *pgcfile*

### <a name="parameters"></a>Parametry

*Opcje*<br/>
(Opcjonalnie) Prawidłowe wartości dla *opcje* są:

- **/?** lub **/help** wyświetla komunikat pomocy.

- **/ noreset** zachowuje liczba struktur danych środowiska uruchomieniowego.

*image*<br/>
Pełna ścieżka pliku .exe lub .dll, który został utworzony przy użyciu [przełączników/genprofile](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md), [/fastgenprofile](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md), lub [pginstrument](reference/ltcg-link-time-code-generation.md) opcji.

*pgcfile*<br/>
Plik .pgc, gdzie to polecenie zapisuje dane liczników.

## <a name="remarks"></a>Uwagi

**Pgosweep** polecenie działa na programy, które zostały utworzone przy użyciu [przełączników/genprofile i/fastgenprofile](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) opcji lub przestarzałego [pginstrument](reference/ltcg-link-time-code-generation.md) opcji. Ona przerwania uruchomionego programu i zapisuje dane profilu do nowego pliku .pgc. Domyślnie polecenie resetuje licznik po zakończeniu każdej operacji zapisu. Jeśli określisz **/noreset** opcji polecenia zapisać wartości, ale nie je zresetować do uruchomionego programu. Ta opcja zapewnia zduplikowanych danych, jeśli później pobrać dane profilu.

Alternatywne użytek **pgosweep** pobieranie informacji o profilu tylko do normalnego działania aplikacji. Na przykład, można uruchomić **pgosweep** wkrótce po uruchomić aplikację i odrzucić tego pliku. Spowoduje to usunięcie danych profilu skojarzony z koszty uruchamiania. Następnie można uruchomić **pgosweep** przed zakończeniem aplikacji. Zebrane dane ma teraz informacji o profilu, tylko od momentu użytkownik może korzystać z programu.

Jeśli nazwa pliku .pgc (przy użyciu *pgcfile* parametr) można użyć standardowego formatu, który jest *appname! n*.pgc. Jeśli używasz tego formatu, kompilator automatycznie znajdzie te dane w **/LTCG /USEPROFILE** lub **/LTCG:PGO** fazy. Jeśli nie używasz formatu standardowego, należy użyć [pgomgr](pgomgr.md) można scalić plików PGC.

> [!NOTE]
> To narzędzie można uruchomić tylko z poziomu wiersza polecenia dla deweloperów programu Visual Studio. Nie można uruchomić go z wiersza poleceń systemu lub Eksploratora plików.

Aby uzyskać informacje na temat sposobu przechwytywania danych profilu z poziomu plik wykonywalny, zobacz [PgoAutoSweep](pgoautosweep.md).

## <a name="example"></a>Przykład

W tym przykładzie polecenia **pgosweep** zapisuje bieżące informacje o profilu dla myapp.exe myapp!1.pgc.

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>Zobacz także

[Optymalizacje sterowane profilem](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>