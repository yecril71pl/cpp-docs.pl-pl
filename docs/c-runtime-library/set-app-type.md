---
title: _set_app_type
ms.date: 11/04/2016
apiname:
- _set_app_type
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: f12e409355fcd10ece474103109286925b1f3a8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569822"
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

