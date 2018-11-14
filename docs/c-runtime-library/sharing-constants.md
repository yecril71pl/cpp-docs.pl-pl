---
title: Udostępnianie stałych
ms.date: 11/04/2016
f1_keywords:
- _SH_DENYNO
- _SH_DENYRD
- _SH_DENYRW
- _SH_DENYWR
- _SH_COMPAT
helpviewer_keywords:
- _SH_DENYRW constant
- SH_DENYRD constant
- _SH_COMPAT constant
- _SH_DENYRD constant
- SH_DENYRW constant
- sharing constants
- SH_DENYNO constant
- _SH_DENYWR constant
- SH_DENYWR constant
- _SH_DENYNO constant
- SH_COMPAT constant
ms.assetid: 95fadc3a-55dc-473d-98b5-e8211900465d
ms.openlocfilehash: ecc7e5fc5afaf1d6d97f3ab46be3b1ed3001d8e5
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519545"
---
# <a name="sharing-constants"></a>Udostępnianie stałych

Stałe do udostępniania plików tryby.

## <a name="syntax"></a>Składnia

```

#include <share.h>
```

## <a name="remarks"></a>Uwagi

*Shflag* argument określa tryb współdzielenia, która składa się z jednego lub więcej stałych manifestu. Może być łączone z *oflag* argumentów (patrz [plik — stałe](../c-runtime-library/file-constants.md)).

W poniższej tabeli wymieniono stałe i ich znaczenie:

|Stała|Znaczenie|
|--------------|-------------|
|`_SH_DENYRW`|Nie zezwala na odczyt i zapis do pliku|
|`_SH_DENYWR`|Nie zezwala na dostęp do zapisu do pliku|
|`_SH_DENYRD`|Nie zezwala na dostęp do odczytu do pliku|
|`_SH_DENYNO`|Zezwala uprawnienia odczytu i zapisu|
|`_SH_SECURE`|Ustawia tryb bezpieczny (odczytu udostępnionego, wyłączny dostęp do zapisu).|

## <a name="see-also"></a>Zobacz też

[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)