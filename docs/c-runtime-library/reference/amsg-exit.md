---
title: _amsg_exit
ms.date: 11/04/2016
apiname:
- _amsg_exit
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
apitype: DLLExport
f1_keywords:
- _amsg_exit
helpviewer_keywords:
- _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
ms.openlocfilehash: 87cd08a6c60a1e29b8a8e15edbfdd69d338d875d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335623"
---
# <a name="amsgexit"></a>_amsg_exit

Emituje runtime określony komunikat o błędzie, a następnie kończy działanie aplikacji z kodem błędu 255.

## <a name="syntax"></a>Składnia

```cpp
void _amsg_exit ( int rterrnum );
```

### <a name="parameters"></a>Parametry

*rterrnum*<br/>
Numer identyfikacyjny zdefiniowaną przez system runtime komunikat o błędzie.

## <a name="remarks"></a>Uwagi

Ta funkcja generuje komunikat o błędzie środowiska uruchomieniowego do **stderr** dla aplikacji konsoli lub wyświetla komunikat w komunikacie pole dla aplikacji Windows. W trybie debugowania można wywołać debugera przed zamknięciem.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|_amsg_exit|internal.h|