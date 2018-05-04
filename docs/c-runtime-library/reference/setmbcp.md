---
title: _setmbcp — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91993171def417adfc389420d1376e5a71f8cda0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="setmbcp"></a>_setmbcp

Ustawia nowej strony kodowe wielobajtowe.

## <a name="syntax"></a>Składnia

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>Parametry

*Strona kodowa*<br/>
Nowe ustawienie strony kodowej dla procedury wielobajtowe niezależne od ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli pomyślnie ustawiono na stronę kodową. Jeśli podano nieprawidłowy strony kodowej dla *codepage*, zwraca -1 i ustawienie strony kodowej jest bez zmian. Ustawia **errno** do **einval —** Jeśli wystąpi błąd alokacji pamięci.

## <a name="remarks"></a>Uwagi

**_Setmbcp —** funkcja określa nowej strony kodowe wielobajtowe. Domyślnie system środowiska wykonawczego automatycznie ustawia strony kodowe wielobajtowe systemu domyślną stronę kodową ANSI. Ustawienia strony kodowe wielobajtowe ma wpływ na wszystkie wielobajtowe procedury, które nie są zależne ustawień regionalnych. Jednak użytkownik może nakazać programowi **_setmbcp —** do użycia na stronę kodową zdefiniowane dla bieżącego ustawienia regionalne (zobacz poniższą listę stałych manifestu i skojarzone zachowanie wyników). Lista wielobajtowe procedur, które są zależne od strona kodowa ustawień lokalnych, a nie strony kodowe wielobajtowe, zobacz [interpretacji znaków wielobajtowych sekwencji](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

Strony kodowe wielobajtowe dotyczy również przetwarzanie znaków wielobajtowych przy użyciu poniższych procedur biblioteki wykonawczej:

||||
|-|-|-|
|[_exec — funkcje](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[_spawn — funkcje](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

Ponadto wszystkie procedury biblioteki wykonawczej otrzymujących znaków wielobajtowych *ARGV —* lub *envp —* program argumenty jako parametry (takie jak **_exec —** i **_spawn** rodzin) przetworzyć te ciągi zgodnie ze strony kodowe wielobajtowe. W związku z tym te procedury dotyczy także przez wywołanie do **_setmbcp —** zmienia się strony kodowe wielobajtowe.

*Codepage* argument może być ustawiony na jedną z następujących wartości:

- **_MB_CP_ANSI** stronę kodową ANSI użycia uzyskanych z systemu operacyjnego podczas uruchamiania programu.

- **_MB_CP_LOCALE** Użyj bieżących ustawień regionalnych strona kodowa uzyskane z poprzedniego wywołania [setlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** strona kodowa OEM Użyj uzyskane z systemu operacyjnego podczas uruchamiania programu.

- **_MB_CP_SBCS** strona kodowa jednobajtowe użycia. Jeśli strona kodowa jest równa **_MB_CP_SBCS**, procedur, takich jak [_ismbblead —](ismbblead-ismbblead-l.md) zawsze zwraca wartość false.

- Wszelkie inne prawidłowy kod strony wartości, niezależnie od tego, czy wartość jest ANSI, OEM lub inne strony kodu działania systemu — obsługiwane (z wyjątkiem UTF-7 i UTF-8, które nie są obsługiwane).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
