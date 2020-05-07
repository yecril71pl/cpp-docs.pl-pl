---
title: PgoAutoSweep
ms.date: 07/02/2019
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
ms.openlocfilehash: 57bcd1b2e9f0a3312867c4373fd1e50bcf91576e
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552242"
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep`zapisuje informacje o bieżącym liczniku profilu do pliku, a następnie resetuje liczniki. Użyj funkcji podczas szkolenia z przewodnikiem po profilowaniu, aby zapisać wszystkie dane profilu z działającego programu do `.pgc` pliku do późniejszego użycia w kompilacji optymalizacji.

## <a name="syntax"></a>Składnia

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>Parametry

*Nazwij*<br/>
Ciąg identyfikacyjny dla zapisanego `.pgc` pliku.

## <a name="remarks"></a>Uwagi

Możesz wywołać `PgoAutoSweep` z aplikacji, aby zapisać i zresetować dane profilu w dowolnym momencie podczas wykonywania aplikacji. W przypadku kompilacji z instrumentacją `PgoAutoSweep` program przechwytuje bieżące dane profilowania, zapisuje je w pliku i resetuje liczniki profilu. Jest to odpowiednik wywołania polecenia [pgosweep](pgosweep.md) w określonym punkcie w pliku wykonywalnym. W zoptymalizowanej kompilacji `PgoAutoSweep` to no-op.

Zapisane dane licznika profilu są umieszczane w pliku o nazwie *base_name*-*name*! *Value*. PGC, gdzie *base_name* jest podstawową nazwą pliku wykonywalnego, *Nazwa* jest parametrem przesłanym do `PgoAutoSweep`, a *wartość* jest unikatową wartością, zazwyczaj monotonicznie zwiększania liczby, aby zapobiec kolizjom nazw plików.

`.pgc` Pliki utworzone przez `PgoAutoSweep` program muszą zostać scalone w `.pgd` pliku, który ma zostać użyty do utworzenia zoptymalizowanego pliku wykonywalnego. Aby wykonać scalanie, można użyć polecenia [pgomgr](pgomgr.md) .

Podczas kompilowania optymalizacji można przekazać nazwę scalonego `.pgd` pliku do konsolidatora przy użyciu argumentu **PGD =**_filename_ do [/USEPROFILE](reference/useprofile.md) opcji konsolidatora lub przy użyciu opcji konsolidatora **/PGD** . W przypadku scalania `.pgc` plików do pliku o nazwie *base_name*. PGD nie trzeba określać nazwy pliku w wierszu polecenia, ponieważ konsolidator domyślnie wybiera tę nazwę pliku.

`PgoAutoSweep` Funkcja utrzymuje ustawienie bezpieczeństwa wątku określone podczas tworzenia konstruowanej kompilacji. Jeśli używasz ustawienia domyślnego lub określono argument **noexact** dla opcji konsolidatora [/GENPROFILE lub/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) , wywołania do nie są bezpieczne `PgoAutoSweep` dla wątków. **Dokładny** argument tworzy bezpieczny wątkowo i bardziej precyzyjny, ale wolniejszy, instrumentację pliku wykonywalnego.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun. h>|

Plik wykonywalny musi zawierać pgobootrun. lib w połączonych bibliotekach. Ten plik jest dołączany do instalacji programu Visual Studio w katalogu bibliotek VC dla każdej obsługiwanej architektury.

## <a name="example"></a>Przykład

Poniższy przykład używa `PgoAutoSweep` do tworzenia dwóch `.pgc` plików w różnych punktach podczas wykonywania. Pierwszy zawiera dane opisujące zachowanie środowiska uruchomieniowego do `count` momentu, gdy wartość jest równa 3, a druga zawiera dane zebrane po tym punkcie do momentu zakończenia działania aplikacji.

```cpp
// pgoautosweep.cpp
// Compile by using: cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp
// Link to instrument: link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj
// Run to generate data: pgoautosweep
// Merge data by using command line pgomgr tool:
// pgomgr /merge pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc pgoautosweep.pgd
// Link to optimize: link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj

#include <iostream>
#include <windows.h>
#include <pgobootrun.h>

void func2(int count)
{
    std::cout << "hello from func2 " << count << std::endl;
    Sleep(2000);
}

void func1(int count)
{
    std::cout << "hello from func1 " << count << std::endl;
    Sleep(2000);
}

int main()
{
    int count = 10;
    while (count--)
    {
        if (count < 3)
            func2(count);
        else
        {
            func1(count);
            if (count == 3)
            {
                PgoAutoSweep("func1");
            }
        }
    }
    PgoAutoSweep("func2");
}
```

W wierszu polecenia dla deweloperów Skompiluj kod do pliku obiektu za pomocą tego polecenia:

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

Następnie Wygeneruj kompilację instrumentacji do szkolenia przy użyciu tego polecenia:

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

Uruchom instrumentację pliku wykonywalnego, aby przechwycić dane szkoleniowe. Dane wyjściowe przez wywołania `PgoAutoSweep` są zapisywane w plikach o nazwie pgoautosweep-func1! 1. PGC i pgoautosweep-func2! 1. pgc. Dane wyjściowe programu powinny wyglądać następująco:

```Output
hello from func1 9
hello from func1 8
hello from func1 7
hello from func1 6
hello from func1 5
hello from func1 4
hello from func1 3
hello from func2 2
hello from func2 1
hello from func2 0
```

Aby scalić zapisane dane w bazę danych szkoleń profilu, należy uruchomić polecenie **pgomgr** :

`pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc`

Dane wyjściowe tego polecenia wyglądają następująco:

```Output
Microsoft (R) Profile Guided Optimization Manager 14.13.26128.0
Copyright (C) Microsoft Corporation. All rights reserved.

Merging pgoautosweep-func1!1.pgc
pgoautosweep-func1!1.pgc: Used  3.8% (22304 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
Merging pgoautosweep-func2!1.pgc
pgoautosweep-func2!1.pgc: Used  3.8% (22424 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
```

Teraz możesz użyć tych danych szkoleniowych do wygenerowania zoptymalizowanej kompilacji. Użyj tego polecenia, aby skompilować zoptymalizowany plik wykonywalny:

`link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj`

```Output
Microsoft (R) Incremental Linker Version 14.13.26128.0
Copyright (C) Microsoft Corporation.  All rights reserved.

Merging pgoautosweep!1.pgc
pgoautosweep!1.pgc: Used  3.9% (22904 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
  Reading PGD file 1: pgoautosweep.pgd
Generating code

0 of 0 ( 0.0%) original invalid call sites were matched.
0 new call sites were added.
294 of 294 (100.00%) profiled functions will be compiled for speed
348 of 1239 inline instances were from dead/cold paths
294 of 294 functions (100.0%) were optimized using profile data
16870 of 16870 instructions (100.0%) were optimized using profile data
Finished generating code
```

## <a name="see-also"></a>Zobacz też

[Optymalizacje sterowane profilem](profile-guided-optimizations.md)<br/>
[pgosweep](pgosweep.md)<br/>
