---
title: _amsg_exit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
caps.latest.revision: 2
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e35d6f606f4862c8a326d70d2e103cb32c8cfda3
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="amsgexit"></a>_amsg_exit

Emituje komunikat o błędzie wykonawcze i kończy działanie aplikacji z kodem błędu 255.

## <a name="syntax"></a>Składnia

```cpp
void _amsg_exit ( int rterrnum );
```

### <a name="parameters"></a>Parametry

*rterrnum*<br/>
Numer identyfikacyjny runtime zdefiniowanym przez system komunikatu o błędzie.

## <a name="remarks"></a>Uwagi

Ta funkcja emituje środowiska uruchomieniowego komunikat o błędzie **stderr** dla aplikacji konsoli lub wyświetlanie pola komunikatu do wiadomości dla aplikacji systemu Windows. W trybie debugowania można wywołać debugera przed zakończeniem.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|_amsg_exit|internal.h|