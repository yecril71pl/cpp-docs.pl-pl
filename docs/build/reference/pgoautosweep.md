---
title: PgoAutoSweep | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 988a73dd8c4ad6929ef04691ad1959df7ea7bdd7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep` Zapisuje bieżące informacje o liczniku profilu do pliku, a następnie resetuje liczniki. Funkcja podczas optymalizacji sterowanych profilem szkolenia zapisać wszystkie dane profilu z uruchomiony program pliku .pgc do późniejszego użytku w kompilacji optymalizacji.

## <a name="syntax"></a>Składnia

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>Parametry

*Nazwa*<br/>
Ciąg identyfikacyjny plik .pgc zapisany.

## <a name="remarks"></a>Uwagi

Możesz wywołać `PgoAutoSweep` z poziomu aplikacji, aby zapisać i zresetować dane profilu w dowolnym momencie podczas wykonywania aplikacji. W kompilacji instrumentowanej `PgoAutoSweep` przechwytuje bieżące dane profilowania, zapisuje go w pliku i resetuje liczniki profilu. Jest to odpowiednik wywołania [pgosweep](pgosweep.md) polecenia w określonym w pliku wykonywalnego. W optymalizowania kompilacji `PgoAutoSweep` jest pusta.

Dane liczników zapisywanego profilu znajduje się w pliku o nazwie *base_name*-*nazwa*! *wartość*.pgc, gdzie *base_name* jest podstawową nazwą pliku wykonywalnego, *nazwa* jest parametr przekazany do `PgoAutoSweep`, i *wartość* jest unikatową wartość, zwykle monotonicznie rosnący numer, aby uniknąć konfliktów nazw plików.

Pliki .pgc utworzone przez `PgoAutoSweep` muszą zostać scalone plik .pgd ma być używany do utworzenia zoptymalizowanego pliku wykonywalnego. Można użyć [pgomgr](pgomgr.md) polecenie do wykonania scalania.

Można przekazać nazwę pliku .pgd scalone do konsolidatora podczas kompilacji optymalizacji za pomocą **PGD =**_filename_ argument [/USEPROFILE](useprofile.md) — opcja konsolidatora, lub przy użyciu przestarzałe **/PGD** — opcja konsolidatora. Jeśli scalić pliki .pgc do pliku o nazwie *base_name*.pgd, nie należy określić nazwę pliku w wierszu polecenia, ponieważ konsolidator przejmuje tej nazwy pliku domyślnie.

`PgoAutoSweep` Funkcja zachowuje ustawienia bezpieczeństwo wątków określone podczas tworzenia instrumentowanej kompilacji. Użyj ustawienia domyślnego lub określ **NOEXACT** argument [opcji/genprofile lub /FASTGENPROFILE]() — opcja konsolidatora, wywołań `PgoAutoSweep` nie są wątkowo. **EXACT** argument tworzy bezpieczne wątkowo i dokładność, ale wolniej, instrumentowanego pliku wykonywalnego.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun.h>|

Plik wykonywalny musi zawierać plik pgobootrun.lib w połączonych bibliotek. Ten plik znajduje się w instalacji programu Visual Studio w katalogu biblioteki VC dla każdej obsługiwanej architektury.

## <a name="example"></a>Przykład

Poniższym przykładzie użyto `PgoAutoSweep` Aby utworzyć dwa. Pliki PGC w różnych punktach w czasie wykonywania. Pierwszy zawiera dane, które określa zachowanie środowiska uruchomieniowego do `count` wynosi 3, a drugi zawiera dane zebrane od tego momentu, aż po prostu przed zakończeniem działania aplikacji.

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

W wierszu polecenia dewelopera skompilować kod do pliku obiektu za pomocą tego polecenia:

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

Następnie można wygenerować instrumentowanej kompilacji szkoleń za pomocą tego polecenia:

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

Uruchom zinstrumentowany plik wykonywalny do przechwytywania danych szkoleniowych. Z danymi wyjściowymi wywołań `PgoAutoSweep` jest zapisywane w plikach o nazwie pgoautosweep func1! 1.pgc i pgoautosweep func2! 1.pgc. Dane wyjściowe programu powinna wyglądać następująco podczas jego działania:

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

Scal zapisane dane w bazie danych profili szkolenia, uruchamiając **pgomgr** polecenia:

`pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc`

Dane wyjściowe tego polecenia wygląda następująco:

```Output
Microsoft (R) Profile Guided Optimization Manager 14.13.26128.0
Copyright (C) Microsoft Corporation. All rights reserved.

Merging pgoautosweep-func1!1.pgc
pgoautosweep-func1!1.pgc: Used  3.8% (22304 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
Merging pgoautosweep-func2!1.pgc
pgoautosweep-func2!1.pgc: Used  3.8% (22424 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
```

Teraz można użyć tych danych szkoleniowych do generowania optymalizowania kompilacji. To polecenie umożliwia tworzenie zoptymalizowanego pliku wykonywalnego:

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

## <a name="see-also"></a>Zobacz także

[Optymalizacje sterowane profilem](profile-guided-optimizations.md)<br/>
[pgosweep](pgosweep.md)<br/>
