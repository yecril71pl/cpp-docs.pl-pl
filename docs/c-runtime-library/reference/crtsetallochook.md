---
title: _Crtsetallochook — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtSetAllocHook
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
- _CrtSetAllocHook
- CrtSetAllocHook
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d86072ceb41b966adfca298152b6209450aace3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402068"
---
# <a name="crtsetallochook"></a>_CrtSetAllocHook

Instaluje funkcję alokacji zdefiniowaną przez klienta przez podłączenie jej do procesu alokacji pamięci debugowania w czasie wykonywania C (tylko wersja debug).

## <a name="syntax"></a>Składnia

```C
_CRT_ALLOC_HOOK _CrtSetAllocHook(
   _CRT_ALLOC_HOOK allocHook
);
```

### <a name="parameters"></a>Parametry

*allocHook*<br/>
Nowa funkcja alokacji zdefiniowana przez klienta do podłączenia do procesu alokacji pamięci debugowania w czasie wykonywania C.

## <a name="return-value"></a>Wartość zwracana

Zwraca funkcję punktu zaczepienia alokacji uprzednio zdefiniowany lub **NULL** Jeśli *allocHook* jest **NULL**.

## <a name="remarks"></a>Uwagi

**_Crtsetallochook —** umożliwia utworzenie punktu zaczepienia funkcji alokacji w procesie alokacji pamięci biblioteki wykonawcze debugowania C aplikacji. W rezultacie, każde wywołanie funkcji alokacji debugowania do przydzielania, ponownego przydzielenia lub zwolnienia bloku pamięci wyzwala wywołanie funkcji podłączania aplikacji. **_Crtsetallochook —** dostarcza aplikację to łatwa metoda do testowania, jak aplikacja obsługuje sytuacjach za mało pamięci, możliwość analizować wzorce alokacji i możliwość logowania później informacji o alokacji Analiza. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań **_crtsetallochook —** są usuwane podczas przetwarzania wstępnego.

**_Crtsetallochook —** funkcja instaluje funkcji alokacji zdefiniowanymi przez klienta określony w *allocHook* i zwraca funkcję wcześniej zdefiniowanego punktu zaczepienia. Poniższy przykład ilustruje, jak powinny być prototypowane zdefiniowane przez klienta funkcje punktu zaczepienia alokacji:

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

**AllocType** argument określa rodzaj operacji alokacji (**_HOOK_ALLOC**, **_HOOK_REALLOC**, i **_HOOK_FREE**) który wyzwalane wywołanie funkcji punktów zaczepienia alokacji. Jeśli wyzwalająca typ alokacji to **_HOOK_FREE**, *danych użytkownika* jest wskaźnikiem do sekcji danych użytkownika w bloku pamięci o ma zostać zwolniony. Jednakże, gdy wyzwalająca typ alokacji jest **_HOOK_ALLOC** lub **_HOOK_REALLOC**, *danych użytkownika* jest **NULL** ponieważ zablokować pamięci nie przydzielono jeszcze.

*rozmiar* Określa rozmiar pamięci bloku w bajtach *blockType* wskazuje typ bloku pamięci *requestNumber* jest numer zamówienia alokacji obiektu bloku pamięci i, jeśli dostępne, *filename* i **numer wiersza** Określ numer nazwy i wiersza pliku źródłowego której zainicjowano operację wyzwalającą alokacji.

Po zakończeniu przetwarzania funkcji podłączania, musi ona zwracać wartość logiczną, która wskazuje głównemu procesowi alokacji środowiska uruchomieniowego C sposób kontynuowania. Gdy funkcji punktów zaczepienia oczekuje, że proces alokacji głównego do kontynuowania funkcji punktów zaczepienia nigdy nie miała została wywołana, a następnie funkcji punktów zaczepienia powinien zwrócić **TRUE**. Powoduje to, że oryginalna operacja wyzwalania alokacji zostanie wykonana. Przy użyciu tej implementacji, funkcja podłączania może gromadzić i zapisywać informacje dotyczące alokacji do późniejszej analizy, bez zakłócania bieżącej operacji alokacji lub stanu sterty debugowania.

Gdy funkcji punktów zaczepienia oczekuje, że proces alokacji głównego do kontynuowania Jeśli wyzwalająca operacja alokacji została wywołana i nie powiodło się, a następnie funkcji punktów zaczepienia powinien zwrócić **FALSE**. Przy użyciu tej implementacji, funkcja podłączania można symulować cały szereg warunków pamięci i stanów sterty do testowania, jak aplikacja obsługuje każdą sytuację.

Aby wyczyścić funkcji punktów zaczepienia, należy przekazać **NULL** do **_crtsetallochook —**.

Aby uzyskać więcej informacji o tym, jak **_crtsetallochook —** może być używany z innymi funkcje zarządzania pamięcią lub zapisać funkcji zdefiniowanej przez klienta punktu zaczepienia, zobacz [debugowania pisanie funkcji punktów zaczepienia](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> **_Crtsetallochook —** nie jest obsługiwany w ramach **/CLR: pure**. **/CLR: pure** i **/CLR: Safe** — opcje kompilatora są przestarzałe w programie Visual Studio 2015 i usuwane w Visual Studio 2017 r.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtSetAllocHook**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Przykładowe zastosowania **_crtsetallochook —**, zobacz [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetAllocHook](crtgetallochook.md)<br/>
