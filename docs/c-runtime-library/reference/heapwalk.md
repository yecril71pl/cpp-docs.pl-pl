---
title: _heapwalk — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d98260ce281bc8773f597dae5897afe4beee0bc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="heapwalk"></a>_heapwalk

Przechodzi przez stos i zwraca informacje o następnej pozycji.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows z wyjątkiem w kompilacjach debugowania. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _heapwalk( _HEAPINFO *entryinfo );
```

### <a name="parameters"></a>Parametry

*entryinfo*<br/>
Bufor zawiera informacje o stercie.

## <a name="return-value"></a>Wartość zwracana

**_heapwalk —** zwraca jedną z następujących manifestu stałe całkowite zdefiniowane w Malloc.h.

|Wartość zwracana|Znaczenie|
|-|-|
|**_HEAPBADBEGIN —**| Informacje o nagłówku początkowej nieprawidłowy lub nie została znaleziona.|
|**_HEAPBADNODE —**| Stercie odnaleziono uszkodzony lub nieprawidłowy węzeł.|
|**_HEAPBADPTR —**| **_Pentry** pole **_heapinfo —** struktura nie zawiera prawidłowego wskaźnika w stercie lub *entryinfo* jest wskaźnika o wartości null.|
|**_HEAPEND —**| Osiągnięto koniec sterty pomyślnie się.|
|**_HEAPEMPTY —**| Stos nie jest zainicjowany.|
|**_HEAPOK**| Do tej pory; bez błędów *entryinfo* został zaktualizowany o informacje o następnej wpisu stosu.|

Ponadto, jeśli wystąpi błąd **_heapwalk —** ustawia **errno** do **ENOSYS**.

## <a name="remarks"></a>Uwagi

**_Heapwalk —** funkcja pomaga debugowania problemy związane ze stosem w programach. Funkcja przeprowadzi Cię przez sterty, przechodzenie przez jednego wpisu na połączenie i zwraca wskaźnik do struktury typu **_heapinfo —** zawierający informacje dotyczące następnego wpisu stosu. **_Heapinfo —** typu zdefiniowanego w Malloc.h, zawiera następujące elementy.

|Pole|Znaczenie|
|-|-|
|`int *_pentry`|Wskaźnik wpisu stosu.|
|`size_t _size`|Rozmiar wpisu stosu.|
|`int _useflag`|Flaga wskazująca, czy wpis stosu jest w użyciu.|

Wywołanie **_heapwalk —** zwracającą **_HEAPOK** przechowuje rozmiar wpisu w **_size** pola i zestawy **_useflag** do każdego pola **_Freeentry —** lub **_usedentry —** (oba są stałe zdefiniowane w Malloc.h). Aby uzyskać informacje o pierwszej pozycji w stosie, należy przekazać **_heapwalk —** wskaźnik do **_heapinfo —** struktury, którego **_pentry** element członkowski jest **wartości NULL** . Jeśli system operacyjny nie obsługuje **_heapwalk —**(na przykład Windows 98), funkcja zwraca **_heapend —** i ustawia **errno** do **ENOSYS**.

Ta funkcja weryfikuje jej parametr. Jeśli *entryinfo* wskaźnika o wartości null, jest program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i funkcja zwraca **_heapbadptr —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_heapwalk**|\<malloc.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
