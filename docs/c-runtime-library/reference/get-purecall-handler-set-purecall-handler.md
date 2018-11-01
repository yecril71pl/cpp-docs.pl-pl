---
title: _get_purecall_handler, _set_purecall_handler —
ms.date: 11/04/2016
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
helpviewer_keywords:
- _set_purecall_handler function
- set_purecall_handler function
- purecall_handler
- set_purecall_handler_m function
- _purecall_handler
- _set_purecall_handler_m function
- _get_purecall_handler function
ms.assetid: 2759b878-8afa-4129-86e7-72afc2153d9c
ms.openlocfilehash: 0009b4bc1c7bf70bd84b9a82ecdc8643789e8164
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646368"
---
# <a name="getpurecallhandler-setpurecallhandler"></a>_get_purecall_handler, _set_purecall_handler —

Pobiera lub ustawia program obsługi błędów dla wywołania czystą funkcję wirtualną.

## <a name="syntax"></a>Składnia

```cpp
typedef void (__cdecl* _purecall_handler)(void);
_purecall_handler __cdecl _get_purecall_handler(void);
_purecall_handler __cdecl _set_purecall_handler(
   _purecall_handler function
);
```

### <a name="parameters"></a>Parametry

*— Funkcja*<br/>
Funkcja wywoływana, gdy wywoływana jest czysta funkcja wirtualna. A **_purecall_handler** funkcja musi mieć typ zwracany void.

## <a name="return-value"></a>Wartość zwracana

Poprzedni **_purecall_handler**. Zwraca **nullptr** przypadku, gdy wystąpił nie poprzedniej procedury obsługi.

## <a name="remarks"></a>Uwagi

**_Get_purecall_handler** i **_set_purecall_handler —** funkcje są specyficzne dla firmy Microsoft i mają zastosowanie tylko do kodu w języku C++.

Wywołanie czystej funkcji wirtualnej występuje błąd, ponieważ jej nie ma implementacji. Domyślnie kompilator generuje kod, aby wywołać funkcję obsługi błędów, gdy wywoływana jest czysta funkcja wirtualna, która kończy program. Można zainstalować własną funkcję obsługi błędu dla wywołań czystą funkcję wirtualną, wyłapuj je na potrzeby debugowania lub do celów raportowania. Aby użyć własnego procedurę obsługi błędów, należy utworzyć funkcję, która ma **_purecall_handler** podpisu, następnie za pomocą **_set_purecall_handler —** się bieżący program obsługi.

Ponieważ istnieje tylko jeden **_purecall_handler** dla każdego procesu, gdy wywołujesz **_set_purecall_handler —** ją od razu ma wpływ na wszystkie wątki. Ostatni obiekt wywołujący na żadnym z wątków Ustawia program obsługi.

Aby przywrócić domyślne zachowanie, należy wywołać **_set_purecall_handler —** przy użyciu **nullptr** argumentu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_purecall_handler**, **_set_purecall_handler —**|\<cstdlib — > lub \<stdlib.h >|

Aby uzyskać informacje o zgodności – zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
