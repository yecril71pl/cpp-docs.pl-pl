---
title: nieoczekiwany (CRT)
ms.date: 11/04/2016
apiname:
- unexpected
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
- unexpected
helpviewer_keywords:
- unexpected function
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
ms.openlocfilehash: 78538c0a10e183e72c742b041b297275c0859a03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155488"
---
# <a name="unexpected-crt"></a>nieoczekiwany (CRT)

Wywołania **zakończyć** lub funkcji, można określić za pomocą **set_unexpected**.

## <a name="syntax"></a>Składnia

```C
void unexpected( void );
```

## <a name="remarks"></a>Uwagi

**Nieoczekiwany** procedura nie jest używany z bieżącej implementacji programu obsługi wyjątków C++. **Nieoczekiwany** wywołania **zakończyć** domyślnie. To zachowanie domyślne można zmienić przez pisanie funkcji niestandardowych zakończenia i wywołanie **set_unexpected** o nazwie funkcji jako argumentem. **Nieoczekiwany** wywołuje funkcję ostatniego podawana jako argument do **set_unexpected**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**unexpected**|\<eh.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Zakończenie](terminate-crt.md)<br/>
