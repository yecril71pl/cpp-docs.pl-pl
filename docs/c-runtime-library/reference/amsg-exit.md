---
title: _amsg_exit
ms.date: 11/04/2016
api_name:
- _amsg_exit
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _amsg_exit
helpviewer_keywords:
- _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
ms.openlocfilehash: 31979a3181dc57644f1e6877277884e55cebf733
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170942"
---
# <a name="_amsg_exit"></a>_amsg_exit

Emituje określony komunikat o błędzie środowiska uruchomieniowego, a następnie kończy działanie aplikacji z kodem błędu 255.

## <a name="syntax"></a>Składnia

```cpp
void _amsg_exit ( int rterrnum );
```

### <a name="parameters"></a>Parametry

*rterrnum*<br/>
Numer identyfikacyjny komunikatu o błędzie środowiska uruchomieniowego zdefiniowanego przez system.

## <a name="remarks"></a>Uwagi

Ta funkcja emituje komunikat o błędzie środowiska uruchomieniowego do **stderr** dla aplikacji konsolowych lub wyświetla komunikat w oknie komunikatu dla aplikacji systemu Windows. W trybie debugowania można wybrać opcję wywołania debugera przed wyjściem.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|_amsg_exit|internal.h|
