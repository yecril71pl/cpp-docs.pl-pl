---
title: "_heapwalk — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _heapwalk
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
dev_langs: C++
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 87ff27007734f84b93d0ecb36f637ae22f72098b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="heapwalk"></a>_heapwalk
Przechodzi przez stos i zwraca informacje o następnej pozycji.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows z wyjątkiem w kompilacjach debugowania. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _heapwalk(   
   _HEAPINFO *entryinfo   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `entryinfo`  
 Bufor zawiera informacje o stercie.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_heapwalk`Zwraca jedną z następujących manifestu stałe całkowite zdefiniowane w Malloc.h.  
  
 `_HEAPBADBEGIN`  
 Informacje o nagłówku początkowej nieprawidłowy lub nie została znaleziona.  
  
 `_HEAPBADNODE`  
 Stercie odnaleziono uszkodzony lub nieprawidłowy węzeł.  
  
 `_HEAPBADPTR`  
 `_pentry`pole `_HEAPINFO` struktura nie zawiera prawidłowego wskaźnika w stercie lub `entryinfo` jest wskaźnika o wartości null.  
  
 `_HEAPEND`  
 Osiągnięto koniec sterty pomyślnie się.  
  
 `_HEAPEMPTY`  
 Stos nie jest zainicjowany.  
  
 `_HEAPOK`  
 Do tej pory; bez błędów `entryinfo` został zaktualizowany o informacje o następnej wpisu stosu.  
  
 Ponadto, jeśli wystąpi błąd `_heapwalk` ustawia `errno` do `ENOSYS`.  
  
## <a name="remarks"></a>Uwagi  
 `_heapwalk` Funkcja pomaga debugowania problemy związane ze stosem w programach. Funkcja przeprowadzi Cię przez sterty, przechodzenie przez jednego wpisu na połączenie i zwraca wskaźnik do struktury typu `_HEAPINFO` zawierający informacje dotyczące następnego wpisu stosu. `_HEAPINFO` Typu zdefiniowanego w Malloc.h, zawiera następujące elementy.  
  
 `int *_pentry`  
 Wskaźnik wpisu stosu.  
  
 `size_t _size`  
 Rozmiar wpisu stosu.  
  
 `int _useflag`  
 Flaga wskazująca, czy wpis stosu jest w użyciu.  
  
 Wywołanie `_heapwalk` zwracającą `_HEAPOK` przechowuje rozmiar wpisu w `_size` pola i zestawy `_useflag` pole jednej `_FREEENTRY` lub `_USEDENTRY` (oba są stałe zdefiniowane w Malloc.h). Aby uzyskać informacje o pierwszej pozycji w stosie, należy przekazać `_heapwalk` wskaźnik do `_HEAPINFO` struktury, którego `_pentry` element członkowski jest `NULL`. Jeśli system operacyjny nie obsługuje `_heapwalk`(na przykład Windows 98), funkcja zwraca `_HEAPEND` i ustawia `errno` do `ENOSYS`.  
  
 Ta funkcja weryfikuje jej parametr. Jeśli `entryinfo` wskaźnika o wartości null, jest program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i funkcja zwraca `_HEAPBADPTR`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_heapwalk`|\<malloc.h >|\<errno.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
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
        printf("%6s block at %Fp of size %4.4X\n",  
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
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)   
 [_heapadd —](../../c-runtime-library/heapadd.md)   
 [_heapchk —](../../c-runtime-library/reference/heapchk.md)   
 [_heapmin —](../../c-runtime-library/reference/heapmin.md)   
 [_heapset](../../c-runtime-library/heapset.md)