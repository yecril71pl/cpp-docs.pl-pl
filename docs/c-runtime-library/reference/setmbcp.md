---
title: _setmbcp
ms.date: 11/04/2016
api_name:
- _setmbcp
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
ms.openlocfilehash: a3408f04eb60a33a84c628c989ebc9c4c4a261df
ms.sourcegitcommit: f38f770bfda1c174d2b81fabda7c893b15bd83a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77473876"
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

## <a name="return-value"></a>Wartość zwrócona

Zwraca wartość 0, jeśli strona kodowa została ustawiona pomyślnie. Jeśli podano nieprawidłową wartość strony kodowej na stronie *kodowej*, zwraca-1, a ustawienie strony kodowej jest niezmienione. Ustawia **errno** na **EINVAL** , jeśli wystąpi błąd alokacji pamięci.

## <a name="remarks"></a>Uwagi

Funkcja **_setmbcp** określa nową stronę kodową wielobajtowego. Domyślnie system czasu wykonywania automatycznie ustawia stronę kodową wielobajtową na stronę kodową ANSI systemu. Ustawienie strony kodowej wielobajtowej ma wpływ na wszystkie procedury wielobajtowe, które nie są zależne od ustawień regionalnych. Można jednak wydać **_setmbcp** , aby użyć strony kodowej zdefiniowanej dla bieżących ustawień regionalnych (zobacz poniższą listę stałych manifestu i wyniki związanych z zachowaniem). Aby uzyskać listę wielobajtowych procedur, które są zależne od strony kodowej ustawień regionalnych, a nie strony kodowej wielobajtowej, zobacz [interpretacja sekwencji znaków wielobajtowych](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

Strona kodowa wielobajtowego ma także wpływ na przetwarzanie znaków wielobajtowych przez następujące procedury biblioteki wykonawczej:

||||
|-|-|-|
|[funkcje _exec](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[funkcje _spawn](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

Ponadto wszystkie procedury biblioteki wykonawczej, które odbierają argumenty programu *argv* lub *envp* , jako parametry (takie jak rodziny **_exec** i **_spawn** ) przetwarzają te ciągi zgodnie ze stroną kodową wielobajtowego. W związku z tym te procedury są również objęte wywołaniem **_setmbcp** , które zmienia stronę kodową wielobajtowego.

Argument *CodePage* można ustawić na dowolną z następujących wartości:

- **_MB_CP_ANSI** Użyj strony kodowej ANSI uzyskanej z systemu operacyjnego podczas uruchamiania programu.

- **_MB_CP_LOCALE** Użyj strony kodowej bieżącej ustawień regionalnych uzyskanych z poprzedniego wywołania metody [setlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** Użyj strony kodowej OEM uzyskanej z systemu operacyjnego podczas uruchamiania programu.

- **_MB_CP_SBCS** Użyj jednobajtowej strony kodowej. Gdy strona kodowa jest ustawiona na **_MB_CP_SBCS**, procedura, taka jak [_ismbblead](ismbblead-ismbblead-l.md) , zawsze zwraca wartość false.

- **_MB_CP_UTF8** Użyj UTF-8.  Gdy strona kodowa jest ustawiona na **_MB_CP_UTF8**, procedura, taka jak [_ismbblead](ismbblead-ismbblead-l.md) , zawsze zwraca wartość false.

- Dowolna inna wartość strony kodowej, niezależnie od tego, czy jest to wartość ANSI, OEM czy inna strona kodowa obsługiwana przez system operacyjny (z wyjątkiem UTF-7, co nie jest obsługiwane).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_setmbcp**|\<Mbctype. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
