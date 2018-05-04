---
title: _get_purecall_handler, _set_purecall_handler — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_purecall_handler
- _set_purecall_handler_m
- _get_purecall_handler
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
- _set_purecall_handler
- _set_purecall_handler_m
- set_purecall_handler_m
- set_purecall_handler
- stdlib/_set_purecall_handler
- stdlib/_get_purecall_handler
- _get_purecall_handler
dev_langs:
- C++
helpviewer_keywords:
- _set_purecall_handler function
- set_purecall_handler function
- purecall_handler
- set_purecall_handler_m function
- _purecall_handler
- _set_purecall_handler_m function
- _get_purecall_handler function
ms.assetid: 2759b878-8afa-4129-86e7-72afc2153d9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1dca104d04546786a361c63461e502f7aa8b6127
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="getpurecallhandler-setpurecallhandler"></a>_get_purecall_handler, _set_purecall_handler —

Pobiera lub ustawia program obsługi błędów wywołanie czystej funkcji wirtualnej.

## <a name="syntax"></a>Składnia

```cpp
typedef void (__cdecl* _purecall_handler)(void);
_purecall_handler __cdecl _get_purecall_handler(void);
_purecall_handler __cdecl _set_purecall_handler(
   _purecall_handler function
);
```

### <a name="parameters"></a>Parametry

*Funkcja*<br/>
Funkcja wywoływana, gdy jest wywoływana czystej funkcji wirtualnej. A **_purecall_handler** funkcji muszą być zwrócony typ void.

## <a name="return-value"></a>Wartość zwracana

Poprzedni **_purecall_handler**. Zwraca **nullptr** Jeśli nie było żadnych poprzednią procedurę obsługi.

## <a name="remarks"></a>Uwagi

**_Get_purecall_handler** i **_set_purecall_handler —** funkcje są specyficzne dla firmy Microsoft i mają zastosowanie tylko do kod w języku C++.

Wywołanie czystej funkcji wirtualnej występuje błąd, ponieważ ma ona żadnej implementacji. Domyślnie kompilator generuje kod, aby wywołać funkcję obsługi błędu wywołanego czystej funkcji wirtualnej, która kończy program. Można zainstalować własnych funkcji obsługi błędu dla wywołań czystej funkcji wirtualnej, aby wykryć je do debugowania lub celów raportowania. Aby korzystać z własnych program obsługi błędów, tworzy funkcję, która ma **_purecall_handler** podpisu, następnie użyć **_set_purecall_handler —** dokonanie bieżący program obsługi.

Ponieważ istnieje tylko jeden **_purecall_handler** dla każdego procesu podczas wywoływania **_set_purecall_handler —** bezpośrednio wpływa wszystkie wątki. Ostatni obiekt wywołujący w którymkolwiek wątku Ustawia program obsługi.

Aby przywrócić domyślne zachowanie, należy wywołać **_set_purecall_handler —** za pomocą **nullptr** argumentu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_purecall_handler**, **_set_purecall_handler —**|\<cstdlib — > lub \<stdlib.h >|

Aby uzyskać informacje dotyczące zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```cpp
// _set_purecall_handler.cpp
// compile with: /W1
#include <tchar.h>
#include <stdio.h>
#include <stdlib.h>

class CDerived;
class CBase
{
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function(void) = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase
{
public:
   CDerived() : CBase(this) {};   // C4355
   virtual void function(void) {};
};

CBase::~CBase()
{
   m_pDerived -> function();
}

void myPurecallHandler(void)
{
   printf("In _purecall_handler.");
   exit(0);
}

int _tmain(int argc, _TCHAR* argv[])
{
   _set_purecall_handler(myPurecallHandler);
   CDerived myDerived;
}
```

```Output
In _purecall_handler.
```

## <a name="see-also"></a>Zobacz także

[Obsługa błędów](../../c-runtime-library/error-handling-crt.md)<br/>
[_purecall](purecall.md)<br/>
