---
title: _get_purecall_handler, _set_purecall_handler
ms.date: 11/04/2016
api_name:
- _set_purecall_handler
- _set_purecall_handler_m
- _get_purecall_handler
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
- _set_purecall_handler
- _set_purecall_handler_m
- set_purecall_handler_m
- set_purecall_handler
- stdlib/_set_purecall_handler
- stdlib/_get_purecall_handler
- _get_purecall_handler
helpviewer_keywords:
- _set_purecall_handler function
- set_purecall_handler function
- purecall_handler
- set_purecall_handler_m function
- _purecall_handler
- _set_purecall_handler_m function
- _get_purecall_handler function
ms.assetid: 2759b878-8afa-4129-86e7-72afc2153d9c
ms.openlocfilehash: 73fc2ffe5cd4ed65c8695432b53816090bbc5f8e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955676"
---
# <a name="_get_purecall_handler-_set_purecall_handler"></a>_get_purecall_handler, _set_purecall_handler

Pobiera lub ustawia procedurę obsługi błędów dla czystego wywołania funkcji wirtualnej.

## <a name="syntax"></a>Składnia

```cpp
typedef void (__cdecl* _purecall_handler)(void);
_purecall_handler __cdecl _get_purecall_handler(void);
_purecall_handler __cdecl _set_purecall_handler(
   _purecall_handler function
);
```

### <a name="parameters"></a>Parametry

*funkcyjn*<br/>
Funkcja, która ma zostać wywołana w przypadku wywołania czystej funkcji wirtualnej. Funkcja **_purecall_handler** musi mieć typ zwracany void.

## <a name="return-value"></a>Wartość zwracana

Poprzedni **_purecall_handler**. Zwraca **nullptr** , jeśli nie ma poprzedniej procedury obsługi.

## <a name="remarks"></a>Uwagi

Funkcje **_get_purecall_handler** i **_set_purecall_handler** są specyficzne dla firmy Microsoft i mają zastosowanie tylko C++ do kodu.

Wywołanie czystej funkcji wirtualnej jest błędem, ponieważ nie ma implementacji. Domyślnie kompilator generuje kod, aby wywołać funkcję programu obsługi błędów w przypadku wywołania czystej funkcji wirtualnej, która kończy program. Możesz zainstalować własną funkcję obsługi błędów dla czystych wywołań funkcji wirtualnych, aby przechwycić je do celów debugowania lub raportowania. Aby użyć własnego programu obsługi błędów, należy utworzyć funkcję, która ma sygnaturę **_purecall_handler** , a następnie użyć **_set_purecall_handler** w celu udostępnienia jej jako bieżącej procedury obsługi.

Ponieważ istnieje tylko jeden **_purecall_handler** dla każdego procesu, wywołanie **_set_purecall_handler** go natychmiast wpływa na wszystkie wątki. Ostatni obiekt wywołujący w dowolnym wątku ustawia procedurę obsługi.

Aby przywrócić zachowanie domyślne, wywołaj **_set_purecall_handler** przy użyciu argumentu **nullptr** .

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_purecall_handler**, **_set_purecall_handler**|\<cstdlib > lub \<STDLIB. h >|

Aby uzyskać informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
