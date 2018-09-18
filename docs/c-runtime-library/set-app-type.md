---
title: _set_app_type | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- _set_app_type
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
dev_langs:
- C++
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b2ad7e22bf6ba366a33dd44ce49c1a384f88b87
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041262"
---
# <a name="setapptype"></a>_set_app_type

Funkcja wewnętrznego, używany przy uruchamianiu w celu poinformowania CRT, czy aplikacja jest aplikacją konsoli lub graficznego interfejsu użytkownika aplikacji.

## <a name="syntax"></a>Składnia

```cpp
typedef enum _crt_app_type
{
    _crt_unknown_app,
    _crt_console_app,
    _crt_gui_app
} _crt_app_type;

void __cdecl _set_app_type(
    _crt_app_type appType
    );
```

## <a name="parameters"></a>Parametry

*Typ aplikacji*<br/>
Wartość, która wskazuje typ aplikacji. Możliwe wartości to:

|Wartość|Opis|
|----------------|-----------------|
|_crt_unknown_app|Nieznany typ aplikacji.|
|_crt_console_app|Aplikacja konsoli (wiersza polecenia).|
|_crt_gui_app|Aplikacja graficznego interfejsu użytkownika (Windows).|

## <a name="remarks"></a>Uwagi

Zwykle nie trzeba wywołać tę funkcję. Jest on częścią kod startowy środowiska uruchomieniowego języka C, który jest wykonywany przed `main` jest wywoływana w swojej aplikacji.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|_set_app_type|process.h|

