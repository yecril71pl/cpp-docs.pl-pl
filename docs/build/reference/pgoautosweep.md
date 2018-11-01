---
title: PgoAutoSweep
ms.date: 03/14/2018
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
ms.openlocfilehash: 356504da91a6778b5e873ca218df01944461d59c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456644"
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep` Zapisuje bieżące informacje o liczniku profilu do pliku, a następnie resetuje liczniki. Użyj funkcji podczas optymalizacji sterowanej profilem, szkolenia zapisać wszystkie dane profilu z uruchomionego programu pliku .pgc do późniejszego użytku w kompilacji o optymalizacji.

## <a name="syntax"></a>Składnia

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>Parametry

*Nazwa*<br/>
Ciąg identyfikujący plik .pgc zapisane.

## <a name="remarks"></a>Uwagi

Możesz wywołać `PgoAutoSweep` z aplikacji w taki sposób, aby zapisać i przywrócić dane profilu w dowolnym momencie podczas wykonywania aplikacji. W kompilacji instrumentowanej `PgoAutoSweep` przechwytuje bieżące dane profilowania, zapisuje go w pliku i resetuje liczniki profilu. Jest to równoważne z wywoływaniem [pgosweep](pgosweep.md) polecenia w określonym punkcie w plik wykonywalny. Zoptymalizowane kompilacji `PgoAutoSweep` jest pusta.

Dane licznika zapisywanego profilu jest umieszczany w pliku o nazwie *base_name*-*nazwa*! *wartość*.pgc, gdzie *base_name* jest nazwa podstawowa pliku wykonywalnego, *nazwa* jest parametr przekazany do `PgoAutoSweep`, i *wartość* jest wartością unikatową, zwykle monotonicznie rosnący numer, aby zapobiec kolizjom nazw plików.

Utworzone przez pliki .pgc `PgoAutoSweep` muszą zostać scalone plik .pgd ma być używany do utworzenia zoptymalizowanego pliku wykonywalnego. Możesz użyć [pgomgr](pgomgr.md) polecenie, aby wykonać scalanie.

Można przekazać nazwę pliku .pgd scalone do konsolidatora podczas kompilacji o optymalizacji przy użyciu **PGD =**_filename_ argument [/USEPROFILE](useprofile.md) — opcja konsolidatora, lub za pomocą przestarzałego **/PGD** — opcja konsolidatora. Jeśli Scal pliki .pgc w pliku o nazwie *base_name*.pgd, nie należy określić nazwę pliku w wierszu polecenia, ponieważ konsolidator przejmuje ta nazwa pliku domyślnie.

`PgoAutoSweep` Funkcja obsługuje ustawienie bezpieczeństwo wątków określone, po utworzeniu kompilację instrumentowaną. Jeśli ustawienie domyślne lub określ **NOEXACT** argument [przełączników/genprofile i/fastgenprofile]() — opcja konsolidatora, wywołania `PgoAutoSweep` nie są wątkowo. **EXACT** argument tworzy ale metodą o bezpiecznych wątkach i bardziej precyzyjne wolniejsze, instrumentowanego pliku wykonywalnego.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun.h>|

Plik wykonywalny musi zawierać plik pgobootrun.lib łączonych bibliotek. Ten plik znajduje się w instalacji programu Visual Studio w katalogu biblioteki VC dla każdej obsługiwanej architektury.

## <a name="example"></a>Przykład

W poniższym przykładzie użyto `PgoAutoSweep` utworzyć dwa. Pliki PGC w różnych momentach podczas wykonywania. Pierwszy zawiera dane, które określa zachowanie środowiska uruchomieniowego aż do `count` jest równa 3, a drugi zawiera dane zebrane po tym punkcie, dopóki nie tylko przed zakończeniem działania aplikacji.

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

W wierszu polecenia dla deweloperów należy skompilować kod do pliku obiektu za pomocą tego polecenia:

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

Następnie Generuj kompilację instrumentowaną, szkolenia, za pomocą tego polecenia:

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

Uruchom zinstrumentowany plik wykonywalny do przechwytywania danych szkoleniowych. Dane wyjściowe przez wywołanie `PgoAutoSweep` jest zapisywany w plikach o nazwie pgoautosweep func1! 1.pgc i pgoautosweep func2! 1.pgc. Dane wyjściowe programu powinien wyglądać następująco podczas jej działania:

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

Scalanie danych zapisanych w profilowej bazie danych szkoleniowych, uruchamiając **pgomgr** polecenia:

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
