---
title: _Crtsetdumpclient — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d5fecc90b4b7259f1440a0a0d86277c769c4e16
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="crtsetdumpclient"></a>_CrtSetDumpClient

Instaluje funkcji zdefiniowanych przez aplikację do zrzutu **_client_block —** wpisz bloki pamięci (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
_CRT_DUMP_CLIENT _CrtSetDumpClient( _CRT_DUMP_CLIENT dumpClient );
```

### <a name="parameters"></a>Parametry

*dumpClient*<br/>
Nową funkcję zrzutu pamięci zdefiniowane przez klienta do przyłączanie się do procesu zrzutu pamięci środowiska wykonawczego debugowania C.

## <a name="return-value"></a>Wartość zwracana

Zwraca bloku klienta wcześniej zdefiniowanego zrzutu funkcji.

## <a name="remarks"></a>Uwagi

**_Crtsetdumpclient —** funkcja umożliwia utworzenie punktu zaczepienia ma własną funkcję zrzutu obiektów przechowywanych w aplikacji **_client_block —** bloki pamięci w czasie wykonywania C debugowania procesu zrzutu pamięci. W związku z tym, co razem, kiedy debugowania zrzutu funkcji takich jak [_crtmemdumpallobjectssince —](crtmemdumpallobjectssince.md) lub [_crtdumpmemoryleaks —](crtdumpmemoryleaks.md) zrzuty **_client_block —** blok pamięci, aplikacji Funkcja zrzutu nosi również. **_Crtsetdumpclient —** dostarcza aplikację łatwa metoda wykrywanie przecieków pamięci i sprawdzania poprawności lub reporting zawartości danych przechowywanych w **_client_block —** bloków. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań **_crtsetdumpclient —** są usuwane podczas przetwarzania wstępnego.

**_Crtsetdumpclient —** funkcja instaluje nowej funkcji zdefiniowanych przez aplikację zrzutu określone w *dumpClient* i zwraca funkcję wcześniej zdefiniowanego zrzutu. Przykładem funkcji zrzutu bloku klienta jest następujący:

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

*UserPortion* argument jest wskaźnik do początku części danych użytkownika blok pamięci i *rozmiar bloku* Określa rozmiar pamięci przydzielony blok w bajtów. Funkcja zrzutu bloku klienta musi zwracać **void**. Wskaźnik do funkcji zrzutu klienta, które są przekazywane do **_crtsetdumpclient —** jest typu **_crt_dump_client —**, zgodnie z definicją w Crtdbg.h:

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

Aby uzyskać więcej informacji na temat funkcji, które pracują na **_client_block —** wpisz bloki pamięci, zobacz [funkcji punktów zaczepienia bloku klienta](/visualstudio/debugger/client-block-hook-functions). [_Crtreportblocktype —](crtreportblocktype.md) funkcja może służyć do zwracania informacji dotyczących typów bloku i podtypów.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtSetDumpClient**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtGetDumpClient](crtgetdumpclient.md)<br/>
