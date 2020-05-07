---
title: _set_app_type
ms.date: 4/2/2020
api_name:
- _set_app_type
- _o__set_app_type
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: 2b78b7205b1e5dda7ac7062747c6dd1065ed1c94
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919915"
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
Wartość wskazująca typ aplikacji. Możliwe wartości są następujące:

|Wartość|Opis|
|----------------|-----------------|
|_crt_unknown_app|Nieznany typ aplikacji.|
|_crt_console_app|Aplikacja konsoli (wiersza polecenia).|
|_crt_gui_app|Graficzny interfejs użytkownika (Windows).|

## <a name="remarks"></a>Uwagi

Zwykle nie trzeba wywoływać tej funkcji. Jest częścią kodu uruchomienia środowiska uruchomieniowego języka C, który `main` jest wykonywany przed wywołaniem w aplikacji.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|_set_app_type|Process. h|
