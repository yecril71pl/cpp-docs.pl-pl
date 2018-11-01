---
title: _heapwalk
ms.date: 11/04/2016
apiname:
- _heapwalk
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- heapwalk
- _heapwalk
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
ms.openlocfilehash: cc2a49d9032746cc6c82c9dc401fc96baabbe2e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454902"
---
# <a name="heapwalk"></a>_heapwalk

Przechodzi sterty i zwraca informacje o następnej pozycji.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach, które są wykonywane w środowisku uruchomieniowym Windows z wyjątkiem w kompilacjach do debugowania. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _heapwalk( _HEAPINFO *entryinfo );
```

### <a name="parameters"></a>Parametry

*entryinfo*<br/>
Bufor do przechowywania informacji stosu.

## <a name="return-value"></a>Wartość zwracana

**_heapwalk** zwraca jedną z następujących stałych całkowitych manifestu w Malloc.h.

|Wartość zwracana|Znaczenie|
|-|-|
|**_HEAPBADBEGIN —**| Informacje początkowego nagłówka nieprawidłowe lub nie został odnaleziony.|
|**_HEAPBADNODE —**| Sterty uszkodzony lub zły węzeł, do których odnaleźć.|
|**_HEAPBADPTR —**| **_Pentry** pole **_heapinfo —** struktury nie zawiera prawidłowego wskaźnika do sterty lub *entryinfo* jest wskaźnikiem wartości null.|
|**_HEAPEND —**| Koniec sterty osiągnięty pomyślnie.|
|**_HEAPEMPTY —**| Nie zainicjowano stosu.|
|**_HEAPOK —**| Brak błędów do tej pory; *entryinfo* jest aktualizowana informacjami o następnej pozycji stosu.|

Ponadto, jeśli wystąpi błąd **_heapwalk** ustawia **errno** do **ENOSYS**.

## <a name="remarks"></a>Uwagi

**_Heapwalk** funkcja pomaga debugować problemy związane ze stertą w programach. Funkcja przechodzi przez stertę, trawersując przez jeden zapis dla połączenia i zwraca wskaźnik do struktury typu **_heapinfo —** zawierająca informacje o następnej pozycji stosu. **_Heapinfo —** typu, określony w Malloc.h, zawiera następujące elementy.

|Pole|Znaczenie|
|-|-|
|`int *_pentry`|Wskaźnik wejścia stosu.|
|`size_t _size`|Rozmiar zapisu sterty.|
|`int _useflag`|Flaga wskazująca, czy wpis stosu jest w użyciu.|

Wywołanie **_heapwalk** zwracającego **_heapok —** przechowuje rozmiar wpisu w **_rozmiar** pola i zestawy **_useflag** pola na wartość **_FREEENTRY** lub **_USEDENTRY** (obie to stałe zdefiniowane w Malloc.h). Aby uzyskać te informacje dotyczące pierwszej pozycji w stosie, należy przekazać **_heapwalk** wskaźnik do **_heapinfo —** struktury, której **_pentry** element członkowski jest **o wartości NULL** . Jeśli system operacyjny nie obsługuje **_heapwalk**(na przykład Windows 98), funkcja zwraca **_heapend —** i ustawia **errno** do **ENOSYS**.

Ta funkcja sprawdza poprawność swojego parametru. Jeśli *entryinfo* jest pustym wskaźnikiem, wywoływany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca **_heapbadptr —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_heapwalk**|\<malloc.h>|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_heapwalk.c

// This program "walks" the heap, starting
// at the beginning (_pentry = NULL). It prints out each
// heap entry's use, location, and size. It also prints
// out information about the overall state of the heap as
// soon as _heapwalk returns a value other than _HEAPOK
// or if the loop has iterated 100 times.

#include <stdio.h>
#include <malloc.h>

void heapdump(void);

int main(void)
{
    char *buffer;

    heapdump();
    if((buffer = (char *)malloc(59)) != NULL)
    {
        heapdump();
        free(buffer);
    }
    heapdump();
}

void heapdump(void)
{
    _HEAPINFO hinfo;
    int heapstatus;
    int numLoops;
    hinfo._pentry = NULL;
    numLoops = 0;
    while((heapstatus = _heapwalk(&hinfo)) == _HEAPOK &&
          numLoops < 100)
    {
        printf("%8s block at %Fp of size %4.4X\n",
               (hinfo._useflag == _USEDENTRY ? "USED" : "FREE"),
               hinfo._pentry, hinfo._size);
        numLoops++;
    }

    switch(heapstatus)
    {
    case _HEAPEMPTY:
        printf("OK - empty heap\n");
        break;
    case _HEAPEND:
        printf("OK - end of heap\n");
        break;
    case _HEAPBADPTR:
        printf("ERROR - bad pointer to heap\n");
        break;
    case _HEAPBADBEGIN:
        printf("ERROR - bad start of heap\n");
        break;
    case _HEAPBADNODE:
        printf("ERROR - bad node in heap\n");
        break;
    }
}
```

```Output
    USED block at 00310650 of size 0100
    USED block at 00310758 of size 0800
    USED block at 00310F60 of size 0080
    FREE block at 00310FF0 of size 0398
    USED block at 00311390 of size 000D
    USED block at 003113A8 of size 00B4
    USED block at 00311468 of size 0034
    USED block at 003114A8 of size 0039
...
    USED block at 00312228 of size 0010
    USED block at 00312240 of size 1000
    FREE block at 00313250 of size 1DB0
OK - end of heap
```

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapchk](heapchk.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
