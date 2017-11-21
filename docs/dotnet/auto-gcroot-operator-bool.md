---
title: "auto_gcroot::operator — wartość logiczna | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- auto_gcroot.operator bool
- auto_gcroot::operator bool
- msclr.auto_gcroot.operator bool
- msclr::auto_gcroot::operator bool
- operator bool
dev_langs: C++
helpviewer_keywords: bool operator
ms.assetid: 87d38498-4221-4de8-8d02-c2dd2e6274ec
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 375816231f10545411cfdc359df556163c2c6039
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="autogcrootoperator-bool"></a>auto_gcroot::operator — wartość logiczna
Operator przy użyciu `auto_gcroot` w wyrażeniu warunkowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
operator bool() const;  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli obiekt opakowanych jest nieprawidłowy; `false` inaczej.  
  
## <a name="remarks"></a>Uwagi  
 Ten operator faktycznie konwertuje `_detail_class::_safe_bool` co jest bezpieczniejszy niż `bool` , ponieważ nie można przekonwertować na typ całkowity.  
  
## <a name="example"></a>Przykład  
  
```  
// msl_auto_gcroot_operator_bool.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_gcroot<String^> s;  
   if ( s ) Console::WriteLine( "s is valid" );  
   if ( !s ) Console::WriteLine( "s is invalid" );  
   s = "something";  
   if ( s ) Console::WriteLine( "now s is valid" );  
   if ( !s ) Console::WriteLine( "now s is invalid" );  
   s.reset();  
   if ( s ) Console::WriteLine( "now s is valid" );  
   if ( !s ) Console::WriteLine( "now s is invalid" );  
}  
```  
  
```Output  
s is invalid  
now s is valid  
now s is invalid  
```  
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówka** \<msclr\auto_gcroot.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Zobacz też  
 [auto_gcroot — członkowie](../dotnet/auto-gcroot-members.md)   
 [auto_gcroot::operator — wartość!](../dotnet/auto-gcroot-operator-logical-not.md)