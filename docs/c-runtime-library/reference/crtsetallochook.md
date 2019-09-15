---
title: _CrtSetAllocHook
ms.date: 11/04/2016
api_name:
- _CrtSetAllocHook
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
- _CrtSetAllocHook
- CrtSetAllocHook
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
ms.openlocfilehash: 303f682b54abc5e44cb7fdd4c89012dd9913288b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938483"
---
# <a name="_crtsetallochook"></a>_CrtSetAllocHook

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

Zwraca wcześniej zdefiniowaną funkcję haka alokacji lub **wartość null** , jeśli *AllocHook* ma **wartość null**.

## <a name="remarks"></a>Uwagi

**_CrtSetAllocHook** umożliwia aplikacji podłączać własną funkcję alokacji do procesu alokacji pamięci biblioteki debugowania w czasie wykonywania C. W rezultacie, każde wywołanie funkcji alokacji debugowania do przydzielania, ponownego przydzielenia lub zwolnienia bloku pamięci wyzwala wywołanie funkcji podłączania aplikacji. **_CrtSetAllocHook** zapewnia aplikacji prostą metodę testowania, w jaki sposób aplikacja obsługuje niewystarczające sytuacje w pamięci, możliwość badania wzorców alokacji oraz możliwość rejestrowania informacji o alokacji na potrzeby późniejszej analizy. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtSetAllocHook** są usuwane podczas przetwarzania wstępnego.

Funkcja **_CrtSetAllocHook** instaluje nową funkcję alokacji zdefiniowaną przez klienta określoną w *allocHook* i zwraca wcześniej zdefiniowaną funkcję haka. Poniższy przykład ilustruje, jak powinny być prototypowane zdefiniowane przez klienta funkcje punktu zaczepienia alokacji:

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

Argument **alloctype** określa typ operacji alokacji ( **_HOOK_ALLOC**, **_HOOK_REALLOC**i **_HOOK_FREE**), która wyzwoliła wywołanie funkcji Hook alokacji. Gdy wyzwalanym typem alokacji jest **_HOOK_FREE**, *UserData* jest wskaźnikiem do sekcji danych użytkownika bloku pamięci, który ma zostać zwolniony. Jednak gdy wyzwalanym typem alokacji jest **_HOOK_ALLOC** lub **_HOOK_REALLOC**, *UserData* ma **wartość null** , ponieważ blok pamięci nie został jeszcze przydzielone.

*rozmiar* określa rozmiar bloku pamięci w bajtach, *bloktype* wskazuje typ bloku pamięci, *requestNumber* jest numerem kolejności alokacji obiektów bloku pamięci i, jeśli są dostępne, *filename* i **LineNumber** Określ nazwę pliku źródłowego i numer wiersza, w którym zainicjowano operację wyzwalania alokacji.

Po zakończeniu przetwarzania funkcji podłączania, musi ona zwracać wartość logiczną, która wskazuje głównemu procesowi alokacji środowiska uruchomieniowego C sposób kontynuowania. Gdy funkcja podłączania chce, aby główny proces alokacji kontynuował działanie tak, jakby funkcja podłączania nigdy nie została wywołana, funkcja Hook powinna zwrócić **wartość true**. Powoduje to, że oryginalna operacja wyzwalania alokacji zostanie wykonana. Przy użyciu tej implementacji, funkcja podłączania może gromadzić i zapisywać informacje dotyczące alokacji do późniejszej analizy, bez zakłócania bieżącej operacji alokacji lub stanu sterty debugowania.

Gdy funkcja podłączania chce, aby główny proces alokacji kontynuował działanie tak, jakby operacja wyzwalania alokacji została wywołana i nie powiodła się, a następnie funkcja Hook powinna zwrócić **wartość false**. Przy użyciu tej implementacji, funkcja podłączania można symulować cały szereg warunków pamięci i stanów sterty do testowania, jak aplikacja obsługuje każdą sytuację.

Aby wyczyścić funkcję Hook, Przekaż **wartość null** do **_CrtSetAllocHook**.

Aby uzyskać więcej informacji o tym, jak **_CrtSetAllocHook** może być używany z innymi funkcjami zarządzania pamięcią lub jak pisać własne zdefiniowane przez klienta funkcje podłączania, zobacz [Zapisywanie funkcji punktu zaczepienia debugowania](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> **_CrtSetAllocHook** nie jest obsługiwana w przypadku opcji **/CLR: Pure**. **/CLR: Pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i usuwane w programie Visual Studio 2017.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtSetAllocHook**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje wyłącznie [bibliotek uruchomieniowych C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Przykład

Aby zapoznać się z przykładem sposobu korzystania z **_CrtSetAllocHook**, zobacz [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetAllocHook](crtgetallochook.md)<br/>
