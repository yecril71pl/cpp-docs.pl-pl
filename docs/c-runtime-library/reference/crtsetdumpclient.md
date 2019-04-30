---
title: _CrtSetDumpClient
ms.date: 11/04/2016
apiname:
- _CrtSetDumpClient
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
- _CrtSetDumpClient
- CrtSetDumpClient
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
ms.openlocfilehash: 09f319f6298dbec6b229b2923bd86fc9b50314de
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342996"
---
# <a name="crtsetdumpclient"></a>_CrtSetDumpClient

Instaluje funkcję zdefiniowanych przez aplikację do porzucenia **_CLIENT_BLOCK** wpisz bloki pamięci (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
_CRT_DUMP_CLIENT _CrtSetDumpClient( _CRT_DUMP_CLIENT dumpClient );
```

### <a name="parameters"></a>Parametry

*dumpClient*<br/>
Nowa funkcja zrzutu pamięci zdefiniowaną przez klienta do podłączenia do procesu zrzutu pamięci debugowania w czasie wykonywania C.

## <a name="return-value"></a>Wartość zwracana

Zwraca blok klienta uprzednio zdefiniowany zrzutu funkcji.

## <a name="remarks"></a>Uwagi

**_CrtSetDumpClient** funkcja pozwala aplikacji podłączyć własną funkcję, aby zrzutu obiektów przechowywanych w **_CLIENT_BLOCK** bloki pamięci w czasie wykonywania C debugować proces zrzutu pamięci. W rezultacie, każdym razem, debugowania zrzutu funkcji takich jak [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) lub [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) zrzuty **_CLIENT_BLOCK** bloku pamięci, aplikacji Funkcja zrzutu nosi również. **_CrtSetDumpClient** dostarcza aplikacji prostą metodę do wykrywania przecieków pamięci i sprawdzania poprawności lub raportowania zawartość danych przechowywanych w **_CLIENT_BLOCK** bloków. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtSetDumpClient** są usuwane podczas przetwarzania wstępnego.

**_CrtSetDumpClient** funkcja instaluje nową funkcję zrzutu zdefiniowanych przez aplikację, określone w *dumpClient* i zwraca funkcję wcześniej zdefiniowaną zrzutu. Przykład funkcji zrzutu blok klienta jest następujący:

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

*UserPortion* argument jest wskaźnikiem do stanu sprzed część danych użytkownika bloku pamięci i *rozmiar bloku* Określa rozmiar ilość przydzielonej pamięci blokowania w bajtach. Funkcja zrzutu blok klienta musi zwracać **void**. Wskaźnik do funkcji zrzutu klienta, który jest przekazywany do **_CrtSetDumpClient** typu **_crt_dump_client —**, zgodnie z definicją w Crtdbg.h:

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

Aby uzyskać więcej informacji na temat funkcji, które działają na **_CLIENT_BLOCK** wpisz bloki pamięci, zobacz [funkcje punktu zaczepienia bloku klienta](/visualstudio/debugger/client-block-hook-functions). [_CrtReportBlockType](crtreportblocktype.md) funkcji można używać do zwracania informacji dotyczących typów bloków i podtypy.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtSetDumpClient**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtGetDumpClient](crtgetdumpclient.md)<br/>
