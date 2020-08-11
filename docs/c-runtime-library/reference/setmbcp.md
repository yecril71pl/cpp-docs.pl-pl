---
title: _setmbcp
ms.date: 4/2/2020
api_name:
- _setmbcp
- _o__setmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _setmbcp
- setmbcp
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
ms.openlocfilehash: 9a981c40b9e525ba1ffc1f2198f2b6a859fd9ac7
ms.sourcegitcommit: b51703a96ee35ee2376d5f0775b70f03ccbe6d9a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/11/2020
ms.locfileid: "88086971"
---
# <a name="_setmbcp"></a>_setmbcp

Ustawia nową stronę kodową wielobajtowego.

## <a name="syntax"></a>Składnia

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>Parametry

*CodePage*<br/>
Nowe ustawienie strony kodowej dla procedur wielobajtowych niezależnych od ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli strona kodowa została ustawiona pomyślnie. Jeśli podano nieprawidłową wartość strony kodowej na stronie *kodowej*, zwraca-1, a ustawienie strony kodowej jest niezmienione. Ustawia **errno** na **EINVAL** , jeśli wystąpi błąd alokacji pamięci.

## <a name="remarks"></a>Uwagi

Funkcja **_setmbcp** określa nową stronę kodową wielobajtowego. Domyślnie system czasu wykonywania automatycznie ustawia stronę kodową wielobajtową na stronę kodową ANSI systemu. Ustawienie strony kodowej wielobajtowej ma wpływ na wszystkie procedury wielobajtowe, które nie są zależne od ustawień regionalnych. Można jednak wydać **_setmbcp** , aby użyć strony kodowej zdefiniowanej dla bieżących ustawień regionalnych (zobacz poniższą listę stałych manifestu i wyniki związanych z zachowaniem). Aby uzyskać listę wielobajtowych procedur, które są zależne od strony kodowej ustawień regionalnych, a nie strony kodowej wielobajtowej, zobacz [interpretacja sekwencji znaków wielobajtowych](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

Argument *CodePage* można ustawić na dowolną z następujących wartości:

- **_MB_CP_ANSI** Użyj strony kodowej ANSI uzyskanej z systemu operacyjnego podczas uruchamiania programu.

- **_MB_CP_LOCALE** Użyj strony kodowej bieżącej ustawień regionalnych uzyskanych z poprzedniego wywołania metody [setlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** Użyj strony kodowej OEM uzyskanej z systemu operacyjnego podczas uruchamiania programu.

- **_MB_CP_SBCS** Użyj jednobajtowej strony kodowej. Gdy strona kodowa jest ustawiona na **_MB_CP_SBCS**, procedura, taka jak [_ismbblead](ismbblead-ismbblead-l.md) , zawsze zwraca wartość false.

- **_MB_CP_UTF8** Użyj UTF-8.  Gdy strona kodowa jest ustawiona na **_MB_CP_UTF8**, procedura, taka jak [_ismbblead](ismbblead-ismbblead-l.md) , zawsze zwraca wartość false.

- Dowolna inna wartość strony kodowej, niezależnie od tego, czy jest to wartość ANSI, OEM czy inna strona kodowa obsługiwana przez system operacyjny (z wyjątkiem UTF-7, co nie jest obsługiwane).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
