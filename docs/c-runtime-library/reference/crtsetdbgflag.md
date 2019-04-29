---
title: _CrtSetDbgFlag
ms.date: 11/04/2016
apiname:
- _CrtSetDbgFlag
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
apitype: DLLExport
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
ms.openlocfilehash: dcb8e37090e4c15ba849e76ca1cb1cc646a7bcc0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348188"
---
# <a name="crtsetdbgflag"></a>_CrtSetDbgFlag

Pobiera lub modyfikuje stan **_crtDbgFlag** flagi sterujące zachowaniem alokacji podczas menedżera stosu debugowania (tylko wersja debugowania).

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

Zwraca poprzedni stan programu **_crtDbgFlag**.

## <a name="remarks"></a>Uwagi

**_CrtSetDbgFlag** funkcja umożliwia aplikacji do kontrolowania, jak Menedżer stosu debugowania śledzi alokacje pamięci, modyfikując pola bitowe **_crtDbgFlag** flagi. W ustawieniu bitów (włączenie), aplikacja może wydać menedżera stosu debugowania, aby wykonać specjalne operacje debugowania, w tym sprawdzania dla przecieki pamięci, gdy aplikacja kończy działanie i raportowania, jeśli jakaś zostanie znaleziona, symulowanie warunków małej ilości pamięci, przez Określanie, że zwolnione bloki pamięci może pozostawać w połączonej liście stosu i sprawdzania integralności sterty, sprawdzając każdy blok pamięci na każde żądanie alokacji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtSetDbgFlag** są usuwane podczas przetwarzania wstępnego.

Poniższa tabela zawiera listę pól bitowych dla **_crtDbgFlag** oraz opis ich zachowania. Ponieważ to ustawienie powoduje bitów, zwiększona diagnostyczne dane wyjściowe i szybkości wykonywania programu mniejsze, bity te nie są ustawione (wyłączone) domyślnie. Aby uzyskać więcej informacji o tych pola bitowe, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details).

|Pole bitowe|Domyślny|Opis|
|---------------|-------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|DALEJ|WŁĄCZONY: Włącz alokacji sterty debugowania i używania identyfikatorów typ bloku pamięci, takich jak **_CLIENT_BLOCK**. WYŁĄCZONE: Dodaj nowe przydziały na połączonej liście stosu, ale ustawiony typ do bloku **_IGNORE_BLOCK**.<br /><br /> Można również łączyć z dowolnymi makra wyboru częstotliwość sterty.|
|**_CRTDBG_CHECK_ALWAYS_DF**|WYŁĄCZONE|WŁĄCZONY: Wywołaj [_CrtCheckMemory](crtcheckmemory.md) na każde żądanie alokacji i dezalokacji. OFF: **_CrtCheckMemory** musi być wywoływana jawnie.<br /><br /> Makra Sprawdzanie sterty częstotliwość przyniosło żadnego skutku, gdy ta flaga jest ustawiona.|
|**_CRTDBG_CHECK_CRT_DF**|WYŁĄCZONE|WŁĄCZONY: Obejmują **_CRT_BLOCK** typów w stanie wykrywania i pamięci przeciek różnica operacji. WYŁĄCZONE: Pamięć używana wewnętrznie przez bibliotekę uruchomieniową jest ignorowana przez te operacje.<br /><br /> Można również łączyć z dowolnymi makra wyboru częstotliwość sterty.|
|**_CRTDBG_DELAY_FREE_MEM_DF**|WYŁĄCZONE|WŁĄCZONY: Zachować zwolnione bloki pamięci w połączonej liście stosu, należy przypisać im **_FREE_BLOCK** wpisz i wypełniać je wartość bajtu 0xDD. WYŁĄCZONE: Nie przechowuj połączonej liście stosu zwolnione bloki.<br /><br /> Można również łączyć z dowolnymi makra wyboru częstotliwość sterty.|
|**_CRTDBG_LEAK_CHECK_DF**|WYŁĄCZONE|WŁĄCZONY: Wykonania przecieku automatyczne sprawdzanie przy zamykaniu programu poprzez wywołanie [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) i wygeneruj raport o błędzie, jeśli aplikacja nie może zwolnić całej pamięci przydzielonej przez jej. WYŁĄCZONE: Nie wykonuj automatycznie przeciek sprawdzanie przy zamykaniu programu.<br /><br /> Można również łączyć z dowolnymi makra wyboru częstotliwość sterty.|

**Sprawdzanie sterty częstotliwość makra**

Można określić, jak często biblioteki wykonawczej C przeprowadza weryfikację sterty debugowania (**_CrtCheckMemory**) na podstawie liczby wywołań **— funkcja malloc**, **realloc**, **bezpłatne**, i **_msize —**.

**_CrtSetDbgFlag** następnie bada górny 16 bitów *NowaFlaga* parametru wartości. Określona wartość jest liczbą **— funkcja malloc**, **realloc**, **bezpłatne**, i **_msize —** wywołań między **_CrtCheckMemory**  wywołania. W tym celu znajdują się cztery wstępnie zdefiniowane makra.

|Macro|Liczba wywołań funkcji malloc i realloc bezpłatna _msize — między wywołaniami _CrtCheckMemory|
|-----------|------------------------------------------------------------------------------------------|
|_CRTDBG_CHECK_EVERY_16_DF|16|
|_CRTDBG_CHECK_EVERY_128_DF|128|
|_CRTDBG_CHECK_EVERY_1024_DF|1024|
|_CRTDBG_CHECK_DEFAULT_DF|0 (domyślnie nie sprawdzania stosu)|

Domyślnie **_CrtCheckMemory** jest wywoływana jeden raz każdego 1024 razy wywołasz **— funkcja malloc**, **realloc**, **bezpłatne**, i **_ msize —**.

Na przykład można określić sterty Sprawdź co 16 **— funkcja malloc**, **realloc**, **bezpłatne**, i **_msize —** operacji przy użyciu następującego kodu:

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

Górny 16 bitów *NowaFlaga* parametr jest ignorowany w przypadku określenia _CRTDBG_CHECK_ALWAYS_DF. W tym przypadku **_CrtCheckMemory** jest wywoływana za każdym razem, należy wywołać **— funkcja malloc**, **realloc**, **bezpłatne**, i **_msize —**.

*NowaFlaga* jest nowy stan dotyczą **_crtDbgFlag** i jest kombinacją wartości dla każdego z pól bitowych.

### <a name="to-change-one-or-more-of-these-bit-fields-and-create-a-new-state-for-the-flag"></a>Aby zmienić co najmniej jeden z tych pól bitowych i utworzyć nowy stan flagi

1. Wywołanie **_CrtSetDbgFlag** z *NowaFlaga* równa **_CRTDBG_REPORT_FLAG** można uzyskać bieżącego **_crtDbgFlag** stanu i przechowywanie zwrócona wartość w zmiennej tymczasowej.

1. Włącz wszystkie bity przez bitowej **lub** zmiennej tymczasowej odpowiednimi maskami bitowymi (reprezentowane przez stałe manifestu w kodzie aplikacji).

1. Wyłącz usługi bits przez **i**- ing zmienną wartością bitową **nie** z odpowiednią masek bitowych.

1. Wywołaj **_CrtSetDbgFlag** z *NowaFlaga* równa wartości przechowywane w zmiennej tymczasowej, aby ustawić nowy stan dla **_crtDbgFlag**.

Poniższy kod ilustruje sposób zasymulować małej ilości pamięci warunków, przechowując uwolnione bloki pamięci połączonej liście stosu i zapobiec **_CrtCheckMemory** wywoływaniu na każde żądanie alokacji:

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

Omówienie zarządzania pamięcią i stosu debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Aby wyłączyć flagę **_CrtSetDbgFlag** funkcji, wykonaj następujące czynności **i** zmiennej za pomocą operatora testu koniunkcji **nie** z maski bitów.

Jeśli *NowaFlaga* nie jest prawidłową wartością, funkcja wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca poprzedni stan programu **_crtDbgFlag**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtSetDbgFlag**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

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
