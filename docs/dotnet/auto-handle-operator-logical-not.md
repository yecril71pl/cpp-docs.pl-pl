---
title: auto_handle::operator! | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr.auto_handle.operator!
- msclr::auto_handle::operator!
- auto_handle.operator!
- auto_handle::operator!
dev_langs: C++
helpviewer_keywords: operator!
ms.assetid: 3f6c7729-3260-4842-87f9-c491c140b299
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1f0cd9ef88895b8fa85bd89775c030aedaa5c042
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="autohandleoperator"></a>auto_handle::operator!
Operator przy użyciu `auto_handle` w wyrażeniu warunkowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
bool operator!();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli opakowana obiektu jest nieprawidłowy. `false` inaczej.  
  
## <a name="example"></a>Przykład  
  
```  
// msl_auto_handle_operator_not.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_handle<String> s1;  
   auto_handle<String> s2 = "something";  
   if ( s1) Console::WriteLine( "s1 is valid" );  
   if ( !s1 ) Console::WriteLine( "s1 is invalid" );  
   if ( s2 ) Console::WriteLine( "s2 is valid" );  
   if ( !s2 ) Console::WriteLine( "s2 is invalid" );  
   s2.reset();  
   if ( s2 ) Console::WriteLine( "s2 is now valid" );  
   if ( !s2 ) Console::WriteLine( "s2 is now invalid" );  
}  
```  
  
```Output  
s1 is invalid  
s2 is valid  
s2 is now invalid  
```  
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówka** \<msclr\auto_handle.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Zobacz też  
 [auto_handle — członkowie](../dotnet/auto-handle-members.md)   
 [auto_handle::operator — wartość logiczna](../dotnet/auto-handle-operator-bool.md)