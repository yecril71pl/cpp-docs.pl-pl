---
title: _CrtSetDbgFlag | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e6524d8c562d8be6ac7a4a1471fa09d65322ff47
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="crtsetdbgflag"></a>_CrtSetDbgFlag

Pobiera lub modyfikuje stan **_crtdbgflag —** flagę w celu kontrolowania zachowania alokacji sterty debugowania Menedżera (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
int _CrtSetDbgFlag(
   int newFlag
);
```

### <a name="parameters"></a>Parametry

*NowaFlaga*<br/>
Nowy stan dla **_crtdbgflag —**.

## <a name="return-value"></a>Wartość zwracana

Zwraca poprzedni stan **_crtdbgflag —**.

## <a name="remarks"></a>Uwagi

**_Crtsetdbgflag —** dzięki funkcji aplikacji kontrolować sposób menedżera sterty debugowania śledzi przydziału pamięci, modyfikując pola bitowego **_crtdbgflag —** flagi. Ustawienie usługi bits (włączenie), aplikacja może nakazać menedżera sterty debugowania do wykonania specjalnych operacji debugowania, w tym sprawdzania wyciek pamięci, gdy aplikacja jest kończona i raportowania, jeśli znajdzie, symulując warunki ilości pamięci przez określenie, że bloki pamięci zwolnionych może pozostawać w stercie połączonej listy i sprawdzania integralności sterty sprawdzając każdy blok pamięci na każde żądanie alokacji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań **_crtsetdbgflag —** są usuwane podczas przetwarzania wstępnego.

W poniższej tabeli wymieniono pola bitowe dla **_crtdbgflag —** oraz opis ich zachowanie. Ponieważ to ustawienie powoduje bitów zwiększona dane wyjściowe diagnostyki i szybkość wykonywania zmniejszenie program, te usługi bits nie są ustawione (wyłączone) domyślnie. Aby uzyskać więcej informacji o tych pól bitowych, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details).

|Pole bitowe|Domyślny|Opis|
|---------------|-------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|ON|Włączony: Włącz Alokacje sterty debugowania i Użyj identyfikatorów typu bloku pamięci, takich jak **_client_block —**. OFF: Dodaj nowe przydziały do stosu w połączonej listy, ale ustawiony typ, aby zablokować **_ignore_block —**.<br /><br /> Mogą być również połączone ze wszystkimi częstotliwości stercie makra wyboru.|
|**_CRTDBG_CHECK_ALWAYS_DF**|WYŁĄCZANIE|Włączony: Wywołanie [_crtcheckmemory —](crtcheckmemory.md) na każde żądanie alokacji i cofania alokacji. OFF: **_crtcheckmemory —** musi być jawnie wywołana.<br /><br /> Makra wyboru częstotliwości stercie nie obowiązują, gdy ta flaga jest ustawiona.|
|**_CRTDBG_CHECK_CRT_DF —**|WYŁĄCZANIE|Włączony: Obejmują **_crt_block —** typów w stanie wykrywania i pamięci przeciek różnica operacji. WYŁĄCZONE: Pamięć używana wewnętrznie przez biblioteki wykonawczej jest ignorowana przez te operacje.<br /><br /> Mogą być również połączone ze wszystkimi częstotliwości stercie makra wyboru.|
|**_CRTDBG_DELAY_FREE_MEM_DF**|WYŁĄCZANIE|Włączony: Zachowaj zwolnienie pamięci bloków w stercie na połączone listy, przypisz im **_free_block —** wpisz i wypełnienie bajt 0xDD. WYŁĄCZONE: Nie przechowuj zwolnionych bloków w stercie listy połączonej.<br /><br /> Mogą być również połączone ze wszystkimi częstotliwości stercie makra wyboru.|
|**_CRTDBG_LEAK_CHECK_DF —**|WYŁĄCZANIE|Włączony: Wykonaj przeciek automatyczne sprawdzanie przy zamykaniu program poprzez wywołanie [_crtdumpmemoryleaks —](crtdumpmemoryleaks.md) i generowanie raportów o błędach w przypadku aplikacji nie można zwolnić wszystkie pamięć ona przydzielone. OFF: Nie należy automatycznie wykonywać przeciek sprawdzanie przy zamykaniu program.<br /><br /> Mogą być również połączone ze wszystkimi częstotliwości stercie makra wyboru.|

**Sprawdzanie sterty częstotliwość makra**

Można określić, jak często biblioteki wykonawczej języka C sprawdza poprawność sterty debugowania (**_crtcheckmemory —**) na podstawie liczby wywołań **— funkcja malloc**, **realloc**, **wolnego**, i **_msize —**.

**_Crtsetdbgflag —** następnie bada górny 16 bitów *NowaFlaga* parametru wartości. Określona wartość jest liczbą **— funkcja malloc**, **realloc**, **wolnego**, i **_msize —** wywołuje między **_crtcheckmemory —**  wywołania. Cztery wstępnie zdefiniowane makra znajdują się w tym celu.

|Macro|Liczba wywołań — funkcja malloc, realloc wolny i _msize — między wywołań _crtcheckmemory —|
|-----------|------------------------------------------------------------------------------------------|
|_CRTDBG_CHECK_EVERY_16_DF|16|
|_CRTDBG_CHECK_EVERY_128_DF|128|
|_CRTDBG_CHECK_EVERY_1024_DF|1024|
|_CRTDBG_CHECK_DEFAULT_DF|0 (domyślnie nie są sprawdzane stosu)|

Domyślnie **_crtcheckmemory —** jest wywoływana po każdym 1024 razy wywołać **— funkcja malloc**, **realloc**, **wolnego**, i **_ msize —**.

Na przykład można określić sterty Sprawdź co 16 **— funkcja malloc**, **realloc**, **wolnego**, i **_msize —** operacje z następującym kodem:

```C
#include <crtdbg.h>
int main( )
{
    int tmp;

    // Get the current bits
    tmp = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);

    // Clear the upper 16 bits and OR in the desired freqency
    tmp = (tmp & 0x0000FFFF) | _CRTDBG_CHECK_EVERY_16_DF;

    // Set the new bits
    _CrtSetDbgFlag(tmp);
}
```

Górny 16 bitów *NowaFlaga* parametru są ignorowane, jeśli określono _crtdbg_check_always_df —. W takim przypadku **_crtcheckmemory —** jest wywoływana za każdym razem, należy wywołać **— funkcja malloc**, **realloc**, **wolnego**, i **_msize —**.

*NowaFlaga* jest nowy stan do zastosowania do **_crtdbgflag —** i jest kombinacją wartości dla poszczególnych pól bitowych.

### <a name="to-change-one-or-more-of-these-bit-fields-and-create-a-new-state-for-the-flag"></a>Aby zmienić co najmniej jeden z tych pól bitowych i utworzyć nowy stan flagi

1. Wywołanie **_crtsetdbgflag —** z *NowaFlaga* równa **_crtdbg_report_flag —** uzyskać bieżące **_crtdbgflag —** stanu i magazynu zwrócona wartość w zmiennej tymczasowej.

1. Włącz wszystkie bity przez bitowej **lub** zmiennej tymczasowej z odpowiedniego masek bitowych (reprezentowane przez stałe manifestu w kodzie aplikacji).

1. Wyłącz usługi bits przez **i**- ne zmiennej z bitowego **nie** z odpowiednią masek bitowych.

1. Wywołanie **_crtsetdbgflag —** z *NowaFlaga* wartość przechowywana w zmiennej tymczasowej, aby ustawić nowy stan dla **_crtdbgflag —**.

Poniższy kod ilustruje sposób symulować ilości pamięci warunki, przechowując zwolniony bloki pamięci sterty połączonej listy i zapobiec **_crtcheckmemory —** z na każde żądanie alokacji:

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

Omówienie zarządzania pamięcią i sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Aby wyłączyć flagę **_crtsetdbgflag —** funkcji, należy **i** zmiennej z bitowego **nie** z maski bitów.

Jeśli *NowaFlaga* nie jest prawidłową wartością tej funkcji wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia **errno** do **einval —** i zwraca poprzedni stan **_crtdbgflag —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtSetDbgFlag**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

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
