---
title: _Crtdoforallclientobjects — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
dev_langs:
- C++
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 83c555899807c9236b803b0576bc8bf6884fd944
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

Wywołania funkcji aplikacji dla wszystkich **_client_block —** typy w stercie (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>Parametry

*pfn* wskaźnika do funkcji wywołania zwrotnego funkcji aplikacji. Pierwszy parametr do funkcji punktów danych. Drugi parametr jest wskaźnik kontekstu przekazywany do wywołania **_crtdoforallclientobjects —**.

*kontekst* wskaźnik do kontekstu dostarczone przez aplikację do przekazania do funkcji aplikacji.

## <a name="remarks"></a>Uwagi

**_Crtdoforallclientobjects —** funkcja wyszukuje połączonej listy sterty dla bloków pamięci z **_client_block —** typu i wywołań znajduje się funkcja dostarczone przez aplikację po bloku tego typu. Znaleziono bloku i *kontekstu* parametrów są przekazywane jako argumenty do funkcji aplikacji. Podczas debugowania aplikacji można śledzić określonej grupy alokacji jawnie podczas wywoływania debugowania funkcje sterty przydzielić pamięci i określając, że bloki można przypisać **_client_block —** zablokować typu. Następnie można osobno i zgłaszanych na inaczej podczas wykrywania przecieków i raportowanie stanu pamięci te bloki.

Jeśli **_crtdbg_alloc_mem_df —** pola bitowego ze [_crtdbgflag —](../../c-runtime-library/crtdbgflag.md) flaga nie jest włączona, **_crtdoforallclientobjects —** natychmiast zwraca. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań **_crtdoforallclientobjects —** są usuwane podczas przetwarzania wstępnego.

Aby uzyskać więcej informacji na temat **_client_block —** typu i może służyć za inne funkcje debugowania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Jeśli *pfn* jest **NULL**, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ustawiono **einval —** i zwraca funkcję.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>, \<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

**Biblioteki:** wersja universal C biblioteki wykonawcze tylko debugowania.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[Funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
