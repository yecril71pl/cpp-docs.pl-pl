---
title: call_in_appdomain — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- call_in_appdomain
helpviewer_keywords:
- call_in_appdomain function
ms.assetid: 9a1a5026-b76b-4cae-a3d4-29badeb9db9c
ms.openlocfilehash: 567b6d8fe9412e58f21de9a1031ec54c4bc01cdc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230899"
---
# <a name="call_in_appdomain-function"></a>call_in_appdomain — Funkcja

Wykonuje funkcję w określonej domenie aplikacji.

## <a name="syntax"></a>Składnia

```
template <typename ArgType1, ...typename ArgTypeN>
void call_in_appdomain(
   DWORD appdomainId,
   void (*voidFunc)(ArgType1, ...ArgTypeN) [ ,
   ArgType1 arg1,
   ...
   ArgTypeN argN ]
);
template <typename RetType, typename ArgType1, ...typename ArgTypeN>
RetType call_in_appdomain(
   DWORD appdomainId,
   RetType (*nonvoidFunc)(ArgType1, ...ArgTypeN) [ ,
   ArgType1 arg1,
   ...
   ArgTypeN argN ]
);
```

#### <a name="parameters"></a>Parametry

*appdomainId*<br/>
Domena aplikacji, w której ma zostać wywołana funkcja.

*voidFunc*<br/>
Wskaźnik do **`void`** funkcji, która pobiera N parametrów (0 <= N <= 15).

*nonvoidFunc*<br/>
Wskaźnik do funkcji nie będącej **`void`** funkcją, która pobiera N parametrów (0 <= N <= 15).

*arg1... argN*<br/>
Od zera do 15 parametrów do przesłania do `voidFunc` lub `nonvoidFunc` z innej domeny aplikacji.

## <a name="return-value"></a>Wartość zwracana

Wynik wykonania `voidFunc` lub `nonvoidFunc` w określonej domenie aplikacji.

## <a name="remarks"></a>Uwagi

Argumenty funkcji przekazanej do `call_in_appdomain` nie mogą być TYPAMI CLR.

## <a name="example"></a>Przykład

```cpp
// msl_call_in_appdomain.cpp
// compile with: /clr

// Defines two functions: one takes a parameter and returns nothing,
// the other takes no parameters and returns an int.  Calls both
// functions in the default appdomain and in a newly-created
// application domain using call_in_appdomain.

#include <msclr\appdomain.h>

using namespace System;
using namespace msclr;

void PrintCurrentDomainName( char* format )
{
   String^ s = gcnew String(format);
   Console::WriteLine( s, AppDomain::CurrentDomain->FriendlyName );
}

int GetDomainId()
{
   return AppDomain::CurrentDomain->Id;
}

int main()
{
   AppDomain^ appDomain1 = AppDomain::CreateDomain( "First Domain" );

   call_in_appdomain( AppDomain::CurrentDomain->Id,
                   &PrintCurrentDomainName,
                   (char*)"default appdomain: {0}" );
   call_in_appdomain( appDomain1->Id,
                   &PrintCurrentDomainName,
                   (char*)"in appDomain1: {0}" );

   int id;
   id = call_in_appdomain( AppDomain::CurrentDomain->Id, &GetDomainId );
   Console::WriteLine( "default appdomain id = {0}", id );
   id = call_in_appdomain( appDomain1->Id, &GetDomainId );
   Console::WriteLine( "appDomain1 id = {0}", id );
}
```

## <a name="output"></a>Dane wyjściowe

```
default appdomain: msl_call_in_appdomain.exe
in appDomain1: First Domain
default appdomain id = 1
appDomain1 id = 2
```

## <a name="requirements"></a>Wymagania

**Plik nagłówka**\<msclr\appdomain.h>

Msclr **przestrzeni nazw**
