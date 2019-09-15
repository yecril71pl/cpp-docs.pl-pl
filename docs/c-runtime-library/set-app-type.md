---
title: _set_app_type
ms.date: 11/04/2016
api_name:
- _set_app_type
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: 7e04d88d9e9981e35b7d4c80c11d27c868219f65
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957925"
---
# <a name="_set_app_type"></a>_set_app_type

Funkcja wewnętrzna używana podczas uruchamiania, aby określić, czy aplikacja jest aplikacją konsolową, czy z graficznym interfejsem użytkownika.

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
Wartość wskazująca typ aplikacji. Możliwe wartości to:

|Wartość|Opis|
|----------------|-----------------|
|_crt_unknown_app|Nieznany typ aplikacji.|
|_crt_console_app|Aplikacja konsoli (wiersza polecenia).|
|_crt_gui_app|Graficzny interfejs użytkownika (Windows).|

## <a name="remarks"></a>Uwagi

Zwykle nie trzeba wywoływać tej funkcji. Jest częścią kodu uruchomienia środowiska uruchomieniowego języka C, który `main` jest wykonywany przed wywołaniem w aplikacji.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|_set_app_type|Process. h|
