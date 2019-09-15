---
title: _CrtIsMemoryBlock
ms.date: 11/04/2016
api_name:
- _CrtIsMemoryBlock
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
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
ms.openlocfilehash: f29745acd06f6f5b3fa96367444e800bdc3e8e3a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938738"
---
# <a name="_crtismemoryblock"></a>_CrtIsMemoryBlock

Sprawdza, czy określony blok pamięci znajduje się w stercie lokalnym i czy ma prawidłowy identyfikator typu bloku sterty debugowania (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
int _CrtIsMemoryBlock(
   const void *userData,
   unsigned int size,
   long *requestNumber,
   char **filename,
   int *linenumber
);
```

### <a name="parameters"></a>Parametry

*userData*<br/>
Wskaźnik na początek bloku pamięci do zweryfikowania.

*zmienia*<br/>
Rozmiar określonego bloku (w bajtach).

*requestNumber*<br/>
Wskaźnik na numer alokacji bloku lub **wartość null**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał bloku lub **wartości null**.

*LineNumber*<br/>
Wskaźnik na numer wiersza w pliku źródłowym lub **wartość null**.

## <a name="return-value"></a>Wartość zwracana

**_CrtIsMemoryBlock** zwraca **wartość true** , jeśli określony blok pamięci znajduje się w stercie lokalnym i ma prawidłowy identyfikator typu bloku sterty debugowania; w przeciwnym razie funkcja zwraca **wartość false**.

## <a name="remarks"></a>Uwagi

Funkcja **_CrtIsMemoryBlock** sprawdza, czy określony blok pamięci znajduje się w stercie lokalnym aplikacji i ma prawidłowy identyfikator typu bloku. Ta funkcja może również służyć do uzyskiwania numeru zamówienia alokacji obiektów oraz nazwy pliku źródłowego/numeru wiersza, w którym pierwotnie zażądano alokacji bloku pamięci. Przekazywanie wartości innych niż**null** dla parametrów *requestNumber*, *filename*lub *LineNumber* powoduje, że **_CrtIsMemoryBlock** ustawiać te parametry do wartości w nagłówku debugowania bloku pamięci, jeśli odnajdzie blok w Sterta lokalna. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtIsMemoryBlock** są usuwane podczas przetwarzania wstępnego.

Jeśli **_CrtIsMemoryBlock** nie powiedzie się, zwraca **wartość false** , a parametry wyjściowe są inicjowane do wartości domyślnych: *requestNumber* i **LineNumber** są ustawione na 0, a *Nazwa pliku* jest ustawiona na **wartość null**.

Ponieważ ta funkcja zwraca **wartość true** lub **false**, można ją przesłać do jednego z makr [_ASSERT](assert-asserte-assert-expr-macros.md) w celu utworzenia prostego mechanizmu obsługi błędów debugowania. Poniższy przykład powoduje niepowodzenie potwierdzenia, jeśli określony adres nie znajduje się na stercie lokalnej:

```C
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,
          &filename, &linenumber ) );
```

Aby uzyskać więcej informacji o tym, jak **_CrtIsMemoryBlock** może być używany z innymi funkcjami i makrami debugowania, zobacz [MACROS for Reporting](/visualstudio/debugger/macros-for-reporting). Aby uzyskać informacje o tym, jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania sterty podstawowej, zobacz [szczegóły sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtIsMemoryBlock**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje wyłącznie [bibliotek uruchomieniowych C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Przykład

Zobacz przykład tematu [_CrtIsValidHeapPointer](crtisvalidheappointer.md) .

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
