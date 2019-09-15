---
title: _heapwalk
ms.date: 11/04/2016
api_name:
- _heapwalk
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- heapwalk
- _heapwalk
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
ms.openlocfilehash: 8dc7ee9335f227bde93a414748ff70b165c44f8d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954775"
---
# <a name="_heapwalk"></a>_heapwalk

Przechodzi przez stos i zwraca informacje o następnym wpisie.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows z wyjątkiem kompilacji debugowania. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _heapwalk( _HEAPINFO *entryinfo );
```

### <a name="parameters"></a>Parametry

*entryinfo*<br/>
Bufor zawierający informacje o stercie.

## <a name="return-value"></a>Wartość zwracana

**_heapwalk** zwraca jedną z następujących stałych literałów liczb całkowitych zdefiniowanych w malloc. h.

|Wartość zwracana|Znaczenie|
|-|-|
|**_HEAPBADBEGIN**| Informacje o początkowym nagłówku są nieprawidłowe lub nie zostały odnalezione.|
|**_HEAPBADNODE**| Znaleziono uszkodzony stertę lub zły węzeł.|
|**_HEAPBADPTR**| Pole **_pentry** struktury **_HEAPINFO** nie zawiera prawidłowego wskaźnika w stercie lub *entryinfo* jest wskaźnikiem o wartości null.|
|**_HEAPEND**| Pomyślnie osiągnięto koniec sterty.|
|**_HEAPEMPTY**| Sterta nie została zainicjowana.|
|**_HEAPOK**| Brak błędów do tej pory; *entryinfo* jest aktualizowany informacjami o następnym wpisie sterty.|

Ponadto, jeśli wystąpi błąd, **_heapwalk** ustawia **errno** na **ENOSYS**.

## <a name="remarks"></a>Uwagi

Funkcja **_heapwalk** pomaga debugować problemy związane z stertą w programach. Funkcja przeprowadzi przez stos, przechodząc do jednego wpisu na wywołanie i zwraca wskaźnik do struktury typu **_HEAPINFO** , który zawiera informacje o następnym wpisie sterty. Typ **_HEAPINFO** , zdefiniowany w malloc. h, zawiera następujące elementy.

|Pole|Znaczenie|
|-|-|
|`int *_pentry`|Wskaźnik wejścia sterty.|
|`size_t _size`|Rozmiar wpisu sterty.|
|`int _useflag`|Flaga wskazująca, czy wpis sterty jest używany.|

Wywołanie **_heapwalk** , które zwraca **_HEAPOK** przechowuje rozmiar wpisu w polu **_SIZE** i ustawia pole **_useflag** na **_FREEENTRY** lub **_USEDENTRY** (obie są stałymi zdefiniowanymi w malloc. h). Aby uzyskać te informacje o pierwszym wpisie w stercie, Przekaż **_heapwalk** wskaźnik do struktury **_HEAPINFO** , której członek **_pentry** ma **wartość null**. Jeśli system operacyjny nie obsługuje **_heapwalk**(na przykład Windows 98), funkcja zwraca **_HEAPEND** i ustawia **errno** na **ENOSYS**.

Ta funkcja sprawdza poprawność parametru. Jeśli *entryinfo* jest pustym wskaźnikiem, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca **_HEAPBADPTR**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_heapwalk**|\<malloc.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
