---
title: pgosweep
ms.date: 03/14/2018
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
ms.openlocfilehash: 3ba31671fc3794e1cc959d86d914ba1eef2e01e4
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341195"
---
# <a name="pgosweep"></a>pgosweep

Używane w optymalizacji profilowanej do zapisywania wszystkich danych profilu z działającego programu do pliku. pgc.

## <a name="syntax"></a>Składnia

> **pgosweep** [*Opcje*] *obraz* *pgcfile*

### <a name="parameters"></a>Parametry

*Opcje*<br/>
Obowiązkowe Prawidłowe wartości dla *opcji* są następujące:

- **/?** lub **/help** wyświetla komunikat pomocy.

- **/NORESET** zachowuje liczbę w strukturach danych środowiska uruchomieniowego.

*Image*<br/>
Pełna ścieżka pliku. exe lub. dll, który został utworzony przy użyciu opcji [/GENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md), [/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)lub [/LTCG: PGINSTRUMENT](reference/ltcg-link-time-code-generation.md) .

*pgcfile*<br/>
Plik. PGC, w którym to polecenie zapisuje liczby danych.

## <a name="remarks"></a>Uwagi

**Pgosweep** polecenie działa w programach, które zostały skompilowane przy użyciu opcji [/GENPROFILE lub/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) lub przestarzałej opcji [/LTCG: PGINSTRUMENT](reference/ltcg-link-time-code-generation.md) . Przerywa uruchomiony program i zapisuje dane profilu do nowego pliku. pgc. Domyślnie polecenie Resetuje licznik po każdej operacji zapisu. W przypadku określenia opcji **/NORESET** polecenie zapisze wartości, ale nie zresetuje ich w uruchomionym programie. Ta opcja umożliwia duplikowanie danych w przypadku późniejszego pobrania danych profilu.

Alternatywne użycie **pgosweep** polega na pobieraniu informacji o profilu tylko w przypadku normalnego działania aplikacji. Na przykład można uruchomić **pgosweep** krótko po uruchomieniu aplikacji i odrzucić ten plik. Spowoduje to usunięcie danych profilu skojarzonych z kosztami uruchomienia. Następnie możesz uruchomić **pgosweep** przed zakończeniem aplikacji. Teraz zebrane dane zawierają informacje o profilu tylko od momentu, w którym użytkownik może korzystać z programu.

Po nazwie pliku. PGC (przy użyciu parametru *pgcfile* ) można użyć formatu standardowego, czyli *nazwa_aplikacji! n*. pgc. Jeśli używasz tego formatu, kompilator automatycznie odnajdzie te dane w fazie **/LTCG/USEPROFILE** lub **/LTCG: PGO** . Jeśli nie używasz formatu standardowego, musisz użyć [pgomgr](pgomgr.md) , aby scalić pliki. pgc.

> [!NOTE]
> To narzędzie można uruchomić tylko z poziomu wiersza polecenia programu Visual Studio Developer. Nie można uruchomić go z poziomu wiersza polecenia systemu lub Eksploratora plików.

Aby uzyskać informacje na temat przechwytywania danych profilu z pliku wykonywalnego, zobacz [PgoAutoSweep](pgoautosweep.md).

## <a name="example"></a>Przykład

W tym przykładowym poleceniu **pgosweep** zapisuje informacje o bieżącym profilu dla programu MojaApl. exe do MojaApl! 1. pgc.

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>Zobacz też

[Optymalizacje sterowane profilem](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
