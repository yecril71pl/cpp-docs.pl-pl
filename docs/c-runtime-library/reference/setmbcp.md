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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 61086471c6194aaa8434d291647978bf891a8aea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337602"
---
# <a name="_setmbcp"></a>_setmbcp

Ustawia nową stronę kodową wielobajtową.

## <a name="syntax"></a>Składnia

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>Parametry

*Codepage*<br/>
Nowe ustawienie strony kodowej dla procedur wielobajtowych niezależnych od ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli strona kodowa została pomyślnie ustawiona. Jeśli dla strony kodowej podano nieprawidłową wartość strony *kodowej,* zwraca wartość -1, a ustawienie strony kodowej pozostaje niezmienione. Ustawia **errno** na **EINVAL,** jeśli wystąpi błąd alokacji pamięci.

## <a name="remarks"></a>Uwagi

Funkcja **_setmbcp** określa nową stronę kodową wielobajtową. Domyślnie system czasu wykonywania automatycznie ustawia stronę kodową wielobajtową na domyślną dla systemu stronę kodową ANSI. Ustawienie strony kodowej wielobajtowej wpływa na wszystkie procedury wielobajtowe, które nie są zależne od ustawień regionalnych. Można jednak poinstruować **_setmbcp,** aby używała strony kodowej zdefiniowanej dla bieżących ustawień regionalnych (zobacz poniższą listę stałych manifestu i skojarzonych wyników zachowania). Aby uzyskać listę procedur wielobajtowych, które są zależne od strony kodowej ustawień regionalnych, a nie od strony kodowej wielobajtowej, zobacz [Interpretacja sekwencji znaków wielobajtowych](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

Strona kodowa wielobajtowa wpływa również na przetwarzanie znaków wielobajtowych przez następujące procedury biblioteki w czasie wykonywania:

||||
|-|-|-|
|[funkcje _exec](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[funkcje _spawn](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam ( tmpnam )](tempnam-wtempnam-tmpnam-wtmpnam.md)|

Ponadto wszystkie procedury biblioteki w czasie wykonywania, które otrzymują argumenty programu *argv* lub *envp* jako parametry (takie jak **_exec** i **_spawn** rodzin) przetwarzają te ciągi zgodnie ze stroną kodową wielobajtów. W związku z tym te procedury są również na nie dotyczy wywołanie **_setmbcp,** który zmienia stronę kodową wielobajtów.

Argument *strony kodowej* można ustawić na dowolną z następujących wartości:

- **_MB_CP_ANSI** Użyj strony kodowej ANSI uzyskanej z systemu operacyjnego podczas uruchamiania programu.

- **_MB_CP_LOCALE** Użyj strony kodowej bieżącej ustawień regionalnych uzyskanej z poprzedniego połączenia, aby [ustawićlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** Użyj strony kodowej OEM uzyskanej z systemu operacyjnego podczas uruchamiania programu.

- **_MB_CP_SBCS** Użyj strony kodowej jedno bajtowej. Gdy strona kodowa jest ustawiona na **_MB_CP_SBCS,** procedura, taka jak [_ismbblead](ismbblead-ismbblead-l.md) zawsze zwraca false.

- **_MB_CP_UTF8** Użyj UTF-8.  Gdy strona kodowa jest ustawiona na **_MB_CP_UTF8,** procedura, taka jak [_ismbblead](ismbblead-ismbblead-l.md) zawsze zwraca false.

- Dowolna inna prawidłowa wartość strony kodowej, niezależnie od tego, czy jest to strona kodowa ANSI, OEM, czy inna strona kodowa obsługiwana przez system operacyjny (z wyjątkiem utf-7, która nie jest obsługiwana).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
