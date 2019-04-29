---
title: _CrtSetAllocHook
ms.date: 11/04/2016
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
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
ms.openlocfilehash: cfa466ec4bce6034c15a627ccab4ee4bb0ef8f5b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347405"
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

Zwraca wartość funkcji punktu zaczepienia alokacji uprzednio zdefiniowany, lub **NULL** Jeśli *allocHook* jest **NULL**.

## <a name="remarks"></a>Uwagi

**_CrtSetAllocHook** pozwala aplikacji podłączyć własną funkcję alokacji w proces alokacji pamięci biblioteki debugowania w czasie wykonywania C. W rezultacie, każde wywołanie funkcji alokacji debugowania do przydzielania, ponownego przydzielenia lub zwolnienia bloku pamięci wyzwala wywołanie funkcji podłączania aplikacji. **_CrtSetAllocHook** dostarcza aplikacji prostą metodę do testowania, jak aplikacja obsługuje sytuacje braku pamięci, możliwość zbadania wzorców przydziału i możliwość rejestrowania informacji o alokacji później Analiza. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtSetAllocHook** są usuwane podczas przetwarzania wstępnego.

**_CrtSetAllocHook** funkcja instaluje nową funkcję alokacji zdefiniowaną przez klienta, określone w *allocHook* i zwraca wcześniej zdefiniowaną funkcję podłączania. Poniższy przykład ilustruje, jak powinny być prototypowane zdefiniowane przez klienta funkcje punktu zaczepienia alokacji:

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

**AllocType** argument określa typ operacji alokacji (**_HOOK_ALLOC**, **_HOOK_REALLOC**, i **_HOOK_FREE**), wyzwolił wywołanie funkcji podłączania alokacji. Gdy wyzwalający typ alokacji to **_HOOK_FREE**, *userData* jest wskaźnikiem na sekcję danych użytkownika bloku pamięci, która będzie zwolniona. Jednakże, gdy wyzwalający typ alokacji to **_HOOK_ALLOC** lub **_HOOK_REALLOC**, *userData* jest **NULL** ponieważ zablokować pamięci ma nie został jeszcze przydzielony.

*rozmiar* Określa rozmiar pamięci blok w bajtach, *blockType* wskazuje typ bloku pamięci *requestNumber* jest numerem porządkowym obiektu alokacji bloku pamięci i, jeśli dostępne, *filename* i **lineNumber** Określ źródła pliku nazwa i numer wiersza której zainicjowano wyzwolenie operacji alokacji.

Po zakończeniu przetwarzania funkcji podłączania, musi ona zwracać wartość logiczną, która wskazuje głównemu procesowi alokacji środowiska uruchomieniowego C sposób kontynuowania. Kiedy funkcja podłączania chce aby główny proces alokacji kontynuował tak, jeśli funkcja podłączania nigdy nie było została wywołana, to funkcja podłączania powinna zwracać **TRUE**. Powoduje to, że oryginalna operacja wyzwalania alokacji zostanie wykonana. Przy użyciu tej implementacji, funkcja podłączania może gromadzić i zapisywać informacje dotyczące alokacji do późniejszej analizy, bez zakłócania bieżącej operacji alokacji lub stanu sterty debugowania.

Kiedy funkcja podłączania chce aby główny proces alokacji kontynuował tak, jeśli wywołano wyzwalająca operacja alokacji i zakończone niepowodzeniem, a następnie funkcja podłączania powinna zwracać **FALSE**. Przy użyciu tej implementacji, funkcja podłączania można symulować cały szereg warunków pamięci i stanów sterty do testowania, jak aplikacja obsługuje każdą sytuację.

Aby wyczyścić funkcję podłączania, należy przekazać **NULL** do **_CrtSetAllocHook**.

Aby uzyskać więcej informacji o tym, jak **_CrtSetAllocHook** może być używany z innymi funkcjami zarządzania pamięcią lub pisać własne funkcje podłączania, zobacz [debugowania pisanie funkcji punktów zaczepienia](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> **_CrtSetAllocHook** nie jest obsługiwany w ramach **/CLR: pure**. **/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i usunięte w programie Visual Studio 2017.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtSetAllocHook**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Przykład sposobu użycia **_CrtSetAllocHook**, zobacz [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetAllocHook](crtgetallochook.md)<br/>
