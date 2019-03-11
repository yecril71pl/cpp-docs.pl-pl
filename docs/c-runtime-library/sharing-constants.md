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
ms.openlocfilehash: dc27b3af0d430aedb8159b4591004f46d197ccd5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751547"
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

## <a name="see-also"></a>Zobacz także

[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
