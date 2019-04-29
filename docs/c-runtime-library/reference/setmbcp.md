---
title: _setmbcp
ms.date: 11/04/2016
apiname:
- _setmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _setmbcp
- setmbcp
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
ms.openlocfilehash: c1f4967baa5fda68a7df33bcd08935dca23fab16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356462"
---
# <a name="setmbcp"></a>_setmbcp

Ustawia nową stronę kodu wielobajtowego.

## <a name="syntax"></a>Składnia

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>Parametry

*codepage*<br/>
Nowe ustawienie strony kodowej dla procedur wielobajtowych niezależne od ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli strona kodowa jest ustawiona pomyślnie. Jeśli nie dostarczono nieprawidłowe strony kodowej dla *stronę kodową*, zwraca -1 i ustawienie strony kodowej pozostaje niezmieniony. Zestawy **errno** do **EINVAL** Jeśli wystąpi błąd alokacji pamięci.

## <a name="remarks"></a>Uwagi

**_Setmbcp** funkcja określa nową stronę kodu wielobajtowego. Domyślnie system środowiska wykonawczego automatycznie ustawia stronę kodu wielobajtowego stronę kodową ANSI systemu domyślnego. Ustawienia strony kodowe wielobajtowe ma wpływ na wszystkie procedury wielobajtowego, które nie są zależne od ustawień regionalnych. Jednak jest możliwe w celu poinstruowania **_setmbcp** do użycia na stronę kodową zdefiniowane dla bieżących ustawień regionalnych (zobacz poniższą listę stałych manifestu i skojarzone z wynikami zachowanie). Aby uzyskać listę wielobajtowych procedur, które są zależne od strony kodowej ustawień regionalnych, zamiast stronę kodu wielobajtowego, zobacz [interpretacji sekwencji znaków wielobajtowych](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

Strony kodowe wielobajtowe wpływa również na przetwarzanie znaków wielobajtowych przy użyciu następujących procedur biblioteki wykonawczej:

||||
|-|-|-|
|[Funkcje _exec](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[_spawn — funkcje](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

Ponadto wszystkie procedury biblioteki czasu wykonywania, które odbierają znaków wielobajtowych *argv* lub *envp* program argumenty jako parametry (takie jak **_exec** i **_spawn** rodzin) przetwarzać te ciągi zgodnie ze strony kodowe wielobajtowe. W związku z tym, tych procedur dotyczy to także przez wywołanie **_setmbcp** zmienia się stronę kodu wielobajtowego.

*Stronę kodową* argument może być ustawiony na jedną z następujących wartości:

- **_MB_CP_ANSI** stronę kodową ANSI użycia uzyskanych od systemu operacyjnego w momencie uruchamiania programu.

- **_MB_CP_LOCALE** Użyj bieżących ustawień regionalnych, stronę kodową uzyskany z poprzedniego wywołania [setlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** stronę kodową OEM użycia uzyskanych od systemu operacyjnego w momencie uruchamiania programu.

- **_MB_CP_SBCS** stronę kodową jednobajtowe użycia. Gdy strona kodowa jest ustawiona na **_MB_CP_SBCS**, procedur, takie jak [_ismbblead](ismbblead-ismbblead-l.md) zawsze zwraca wartość false.

- Wszystkie inne Nieprawidłowa wartość strony kodowej, niezależnie od tego, czy wartość jest ANSI, OEM lub innej strony operacyjnego systemu obsługiwane kod (z wyjątkiem UTF-7 lub UTF-8, które nie są obsługiwane).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
