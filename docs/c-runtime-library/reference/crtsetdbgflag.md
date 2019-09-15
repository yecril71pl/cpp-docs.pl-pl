---
title: _CrtSetDbgFlag
ms.date: 11/04/2016
api_name:
- _CrtSetDbgFlag
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CRTDBG_REPORT_FLAG
- _CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_EVERY_128_DF
- CRTDBG_CHECK_EVERY_1024_DF
- _CRTDBG_CHECK_EVERY_128_DF
- CrtSetDbgFlag
- CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_EVERY_1024_DF
- _CrtSetDbgFlag
- CRTDBG_REPORT_FLAG
helpviewer_keywords:
- _CRTDBG_CHECK_EVERY_16_DF macro
- CRTDBG_CHECK_EVERY_16_DF macro
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_ALLOC_MEM_DF macro
- CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_ALLOC_MEM_DF macro
- _CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_1024_DF macro
- CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_CHECK_EVERY_1024_DF macro
- _CrtSetDbgFlag function
- CrtSetDbgFlag function
- _CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: b5657ffb-6178-4cbf-9886-1af904ede94c
ms.openlocfilehash: 8506b593a579c8dd1791e56c320bd9d8e2ee9ba2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938616"
---
# <a name="_crtsetdbgflag"></a>_CrtSetDbgFlag

Pobiera lub modyfikuje stan flagi **_crtDbgFlag** w celu sterowania zachowaniem alokacji menedżera sterty debugowania (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
int _CrtSetDbgFlag(
   int newFlag
);
```

### <a name="parameters"></a>Parametry

*newFlag*<br/>
Nowy stan dla **_crtDbgFlag**.

## <a name="return-value"></a>Wartość zwracana

Zwraca poprzedni stan **_crtDbgFlag**.

## <a name="remarks"></a>Uwagi

Funkcja **_CrtSetDbgFlag** umożliwia aplikacji kontrolowanie, jak Menedżer sterty debugowania śledzi alokacje pamięci, modyfikując pola bitowe flagi **_crtDbgFlag** . Ustawienie bitów (Włączanie) powoduje, że aplikacja może nakazać menedżerowi sterty debugowania wykonywanie specjalnych operacji debugowania, w tym sprawdzanie przecieków pamięci, gdy aplikacja zakończy działanie i raportowanie, czy zostały znalezione, symulując warunki braku pamięci przez określenie, że zwolnione bloki pamięci powinny pozostawać w połączonej liście sterty i sprawdzać integralność sterty, sprawdzając każdy blok pamięci w każdym żądaniu alokacji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtSetDbgFlag** są usuwane podczas przetwarzania wstępnego.

W poniższej tabeli wymieniono pola bitowe dla **_crtDbgFlag** i opisano ich zachowanie. Ponieważ ustawienie BITS skutkuje zwiększonym wyjściem diagnostycznym i ograniczoną szybkością wykonywania programu, te bity nie są domyślnie ustawione (wyłączone). Aby uzyskać więcej informacji na temat tych pól bitowych, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details).

|Pole bitowe|Domyślny|Opis|
|---------------|-------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|Z|Z Włącz alokacje sterty debugowania i użycie identyfikatorów typów bloków pamięci, takich jak **_CLIENT_BLOCK**. LOGOWANIE Dodaj nowe alokacje do połączonej listy sterty, ale ustaw typ bloku na **_IGNORE_BLOCK**.<br /><br /> Można również łączyć z dowolnym makrem sprawdzania częstotliwości sterty.|
|**_CRTDBG_CHECK_ALWAYS_DF**|WYŁĄCZONE|Z Wywołaj [_CrtCheckMemory](crtcheckmemory.md) przy każdym żądaniu alokacji i cofania alokacji. WYŁĄCZONE: **_CrtCheckMemory** musi być wywołana jawnie.<br /><br /> Makra sprawdzania częstotliwości sterty nie działają, gdy flaga jest ustawiona.|
|**_CRTDBG_CHECK_CRT_DF**|WYŁĄCZONE|Z Uwzględnij typy **_CRT_BLOCK** w operacjach wykrywania przecieków i różnic stanu pamięci. LOGOWANIE Pamięć używana wewnętrznie przez bibliotekę wykonawczą jest ignorowana przez te operacje.<br /><br /> Można również łączyć z dowolnym makrem sprawdzania częstotliwości sterty.|
|**_CRTDBG_DELAY_FREE_MEM_DF**|WYŁĄCZONE|Z Zachowaj zwolnione bloki pamięci na połączonej liście sterty, przypisz im typ **_FREE_BLOCK** i wypełnij je wartością Byte 0xDD. LOGOWANIE Nie przechowuj zwolnionych bloków na liście połączonej sterty.<br /><br /> Można również łączyć z dowolnym makrem sprawdzania częstotliwości sterty.|
|**_CRTDBG_LEAK_CHECK_DF**|WYŁĄCZONE|Z Przeprowadź automatyczne sprawdzanie przecieków przy zamykaniu programu przez wywołanie [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) i Wygeneruj raport o błędach, jeśli aplikacja nie może zwolnić całej przypisanej pamięci. LOGOWANIE Nie przeprowadzaj kontroli przecieków przy zamykaniu programu.<br /><br /> Można również łączyć z dowolnym makrem sprawdzania częstotliwości sterty.|

**Sterty — makra częstotliwości sprawdzania**

Można określić, jak często Biblioteka wykonawcza C wykonuje walidację sterty debugowania ( **_CrtCheckMemory**) na podstawie liczby wywołań funkcji **malloc**, **realloc**, **Free**i **_msize**.

**_CrtSetDbgFlag** następnie sprawdzi górne 16 bitów parametru *newFlag* dla wartości. Określona wartość to liczba wywołań **malloc**, **realloc**, **Free**i **_msize** między wywołaniami **_CrtCheckMemory** . Do tego celu są dostępne cztery wstępnie zdefiniowane makra.

|Macro|Liczba wywołań funkcji malloc, realloc, Free i _msize między wywołaniami do _CrtCheckMemory|
|-----------|------------------------------------------------------------------------------------------|
|_CRTDBG_CHECK_EVERY_16_DF|16|
|_CRTDBG_CHECK_EVERY_128_DF|128|
|_CRTDBG_CHECK_EVERY_1024_DF|1024|
|_CRTDBG_CHECK_DEFAULT_DF|0 (domyślnie bez sprawdzania sterty)|

Domyślnie **_CrtCheckMemory** jest wywoływana raz co 1 024 razy wywołania **malloc**, **realloc**, **Free**i **_msize**.

Na przykład można określić sprawdzanie sterty co 16 **malloc**, **realloc**, **Free**i **_msize** operacji przy użyciu następującego kodu:

```C
#include <crtdbg.h>
int main( )
{
    int tmp;

    // Get the current bits
    tmp = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);

    // Clear the upper 16 bits and OR in the desired frequency
    tmp = (tmp & 0x0000FFFF) | _CRTDBG_CHECK_EVERY_16_DF;

    // Set the new bits
    _CrtSetDbgFlag(tmp);
}
```

W przypadku określenia wartości _CRTDBG_CHECK_ALWAYS_DF są ignorowane górne 16 bitów parametru *newFlag* . W takim przypadku **_CrtCheckMemory** jest wywoływana za każdym razem, gdy wywołasz **malloc**, **realloc**, **Free**i **_msize**.

*newFlag* jest nowym stanem do zastosowania do **_crtDbgFlag** i jest kombinacją wartości dla każdego pola bitowego.

### <a name="to-change-one-or-more-of-these-bit-fields-and-create-a-new-state-for-the-flag"></a>Aby zmienić co najmniej jedno z tych pól bitowych i utworzyć nowy stan dla flagi

1. Wywołaj **_CrtSetDbgFlag** z *NewFlag* równą **_CRTDBG_REPORT_FLAG** , aby uzyskać bieżący stan **_crtDbgFlag** i zapisać zwracaną wartość w zmiennej tymczasowej.

1. Włącz wszystkie bity przez bitową **lub** tymczasową zmienną z odpowiednimi masek bitowych (przedstawionymi w kodzie aplikacji przez stałe manifestu).

1. Wyłącz inne bity **i**przenotuj zmienną z **nieprawidłowym** masek bitowych.

1. Wywołaj **_CrtSetDbgFlag** z *newFlag* równą wartości przechowywanej w zmiennej tymczasowej, aby ustawić nowy stan dla **_crtDbgFlag**.

Poniższy kod ilustruje sposób symulowania warunków braku pamięci przez utrzymywanie zwolnionych bloków pamięci na liście połączonej sterty i zapobiega wywoływaniu **_CrtCheckMemory** w każdym żądaniu alokacji:

```C
// Get the current state of the flag
// and store it in a temporary variable
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );

// Turn On (OR) - Keep freed memory blocks in the
// heap's linked list and mark them as freed
tmpFlag |= _CRTDBG_DELAY_FREE_MEM_DF;

// Turn Off (AND) - prevent _CrtCheckMemory from
// being called at every allocation request
tmpFlag &= ~_CRTDBG_CHECK_ALWAYS_DF;

// Set the new state for the flag
_CrtSetDbgFlag( tmpFlag );
```

Aby zapoznać się z omówieniem zarządzania pamięcią i sterty debugowania, zobacz [szczegóły sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Aby wyłączyć flagę przy użyciu funkcji **_CrtSetDbgFlag** , należy **i** zmiennej z bitową, a **nie** maską bitową.

Jeśli *newFlag* nie jest prawidłową wartością, ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca poprzedni stan **_crtDbgFlag**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtSetDbgFlag**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje wyłącznie [bibliotek uruchomieniowych C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Przykład

```C
// crt_crtsetdflag.c
// compile with: /c -D_DEBUG /MTd -Od -Zi -W3 /link -verbose:lib /debug

// This program concentrates on allocating and freeing memory
// blocks to test the functionality of the _crtDbgFlag flag.

#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

int main( )
{
    char *p1, *p2;
    int tmpDbgFlag;

    _CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_FILE );
    _CrtSetReportFile( _CRT_ERROR, _CRTDBG_FILE_STDERR );

    // Set the debug-heap flag to keep freed blocks in the
    // heap's linked list - This will allow us to catch any
    // inadvertent use of freed memory
    tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);
    tmpDbgFlag |= _CRTDBG_DELAY_FREE_MEM_DF;
    tmpDbgFlag |= _CRTDBG_LEAK_CHECK_DF;
    _CrtSetDbgFlag(tmpDbgFlag);

    // Allocate 2 memory blocks and store a string in each
    p1 = malloc( 34 );
    p2 = malloc( 38 );
    strcpy_s( p1, 34, "p1 points to a Normal allocation block" );
    strcpy_s( p2, 38, "p2 points to a Client allocation block" );

    // Free both memory blocks
    free( p2 );
    free( p1 );

    // Set the debug-heap flag to no longer keep freed blocks in the
    // heap's linked list and turn on Debug type allocations (CLIENT)
    tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);
    tmpDbgFlag |= _CRTDBG_ALLOC_MEM_DF;
    tmpDbgFlag &= ~_CRTDBG_DELAY_FREE_MEM_DF;
    _CrtSetDbgFlag(tmpDbgFlag);

    // Explicitly call _malloc_dbg to obtain the filename and
    // line number of our allocation request and also so we can
    // allocate CLIENT type blocks specifically for tracking
    p1 = _malloc_dbg( 40, _NORMAL_BLOCK, __FILE__, __LINE__ );
    p2 = _malloc_dbg( 40, _CLIENT_BLOCK, __FILE__, __LINE__ );
    strcpy_s( p1, 40, "p1 points to a Normal allocation block" );
    strcpy_s( p2, 40, "p2 points to a Client allocation block" );

    // _free_dbg must be called to free the CLIENT block
    _free_dbg( p2, _CLIENT_BLOCK );
    free( p1 );

    // Allocate p1 again and then exit - this will leave unfreed
    // memory on the heap
    p1 = malloc( 10 );
}
```

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtCheckMemory](crtcheckmemory.md)<br/>
